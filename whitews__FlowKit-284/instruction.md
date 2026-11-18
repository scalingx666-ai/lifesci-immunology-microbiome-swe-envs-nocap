# Issue

**Title:** Raise instead of silently writing an incorrect GatingML document

## Description

Two independent ways `export_gatingml()` produces a document that describes a
different analysis from the strategy it came from, without raising. Both are
silent: the export succeeds, the file looks fine, and the only signal is that
counts differ after a round trip.

They are separate commits and can be reviewed independently.

---

## 1. `use_complement` is dropped (commit 1)

`RectangleGate` and `PolygonGate` accept `use_complement=True` and honour it
when gating. Exporting dropped it, and the gate reimported with
`use_complement=False` — as its own inverse.

```python
gate = fk.gates.PolygonGate("Cells", dims, vertices, use_complement=True)
# before export, use_complement = True
# after reimport,  use_complement = False
```

**This is not a missing attribute in the writer.** `use-as-complement` occurs
exactly once in the bundled schema:

```
src/flowkit/_resources/Gating-ML.v2.0.xsd:257
  <attribute name="use-as-complement" type="boolean" default="false" use="optional" .../>
```

It belongs to `gateReference`, inside boolean gates. Neither `PolygonGate` nor
`RectangleGate` has a complement attribute in GatingML 2.0, and `gml_write.py`
is consistent with that — it writes the attribute only for boolean gate
references. So `use_complement` on a rectangle or polygon is a FlowKit
capability with no representation in the format, and the defect is that export
proceeded anyway.

`_add_gate_to_gml()` now raises `NotImplementedError` naming the gate and the
two representable alternatives: explicit boundaries, or a reference from a
`not` `BooleanGate`.

**Alternative, if you prefer it:** emitting an equivalent `BooleanGate` with a
`not` referencing the original *is* expressible and would preserve the
semantics rather than refusing. It changes the exported gate hierarchy, which
is why I did not assume it was wanted — happy to rework it that way.

## 2. Unsupported transforms export as an empty element (commit 2)

`_add_transform_to_gml()` creates the `<transformation>` element and sets its
id *before* testing the transform's type. The `if`/`elif` chain had no `else`,
so a transform matching no branch left the element empty:

```xml
<transforms:transformation transforms:id="biex1"/>
```

That is invalid against `Transformations.v2.0.xsd`, and every gate whose
dimensions reference the id reimports with **no transform applied** — so the
gate is evaluated on an untransformed scale and selects a different
population.

`WSPBiexTransform` and `WSPLogTransform` reach it. They model FlowJo
transforms with no GatingML 2.0 equivalent, and they are what `parse_wsp()`
produces — so the likeliest path is: import a `.wsp`, export GatingML to share
it, silently lose every transform.

The missing branch is arguably correct, since there is nothing valid to write.
The problem is the silent fallthrough, so this adds an `else` that raises
`NotImplementedError` naming the transform and pointing at `LogicleTransform`
and `HyperlogTransform`, which do round-trip.

Related but a different code path: #158 (`Session.export_wsp()` fails for biex)
is closed; `export_gatingml()` does not fail, it writes an incomplete document.

---

## Why raise rather than warn

In both cases the alternative to raising is a document that means something
other than what the caller built. A warning can be missed in a batch run, and
the resulting file is indistinguishable from a correct one — so the error
seemed the safer default. Both messages name the offending gate or transform
and a representable alternative, so the fix is actionable rather than a dead
end.

`NotImplementedError` rather than a new exception type, to avoid adding public
API for this. Happy to introduce a `GatingMLExportError(FlowKitException)`
instead if that fits the codebase better.

## Tests

Eight added to `tests/export_gml_tests.py`, four per issue: each unsupported
case raises, each message names the offending gate or transform, and the
supported cases still export and round-trip.

One of them is the test that would have caught the second bug originally — it
asserts no self-closing `<transformation/>` appears in the output. The existing
suite checked that gates round-trip, never that the document was complete.

**`pytest tests/*_tests.py`: 371 passed** (363 on `master`, plus these 8). The
export suite goes from 45 to 53 and all pass. Note that `run_tests.py` does not
pick up `export_gml_tests.py`, so it reports 363 with or without this change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1646849ac546`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.