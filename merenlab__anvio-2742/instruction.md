# Issue

**Title:** A crisper display for anvi-display-pan-graph

## Description

`anvi-display-pan-graph` has a problem. When it is initialized, it draws the display as one large SVG within a viewBox that is tens of thousands of units wide that is squeezed into the browser viewport.

When we look at the entirety of a graph, the lines (or stroke widths in SVG lingo) are collapsed to sub-pixel widths (since you can squeeze things only so much) and as a result the lines are typically rendered as faint, shimmery antialiased garbage (even though when you download the SVG and open it in Inkscape, or zoom in all the way, you see perfectly fine lines). Here is an example of what user sees and that annoys the crap out of the user because the user wants to be able to just take screenshots and send it to their colleagues but they can't do it because this is what things look like which is why the user is so annoyed:

<img width="1782" height="1784" alt="image" src="https://github.com/user-attachments/assets/db268d45-4e50-4df2-b84d-72a8d43c0f85" />

When it should look like THIS, which is what this PR enables:

<img width="1782" height="1784" alt="image" src="https://github.com/user-attachments/assets/d537f50e-45be-41f8-94ee-6761bd69c46a" />

This is happening how we resolved some performance issues we experienced before. We used non-scaling-stroke (constant screen-pixel width, so no computation when zoomed in and out or panned the display around), which made lines obnoxiously thick at 100% view while looking fine zoomed in. That obviously was not the solution. What this PR does it that it keeps strokes scaling naturally with the graph but clamps each to a minimum on-screen width applied in the zoom handler. So lines stay proportional and nice at every level of 'zoom', but never never drop below the default min line width (which is now by default 0.5px) and shrivel into some antialiased garbage like they do in the first image.

This PR also introduces two controls: min line width (px) input so the user can change the default if they wish, a checkbox for "high-performance mode" so they user can toggle that to skip the per-zoom pass on very large graphs (plus a regime cache so zoomed-in interaction does zero per-element work):

```js
            // High-performance mode: skip the floor entirely (cheap pan/zoom;
            // lines may go sub-pixel when fully zoomed out).
            if ($('#flexhighperf').prop('checked')) { to_base(); return; }
```

So we can have our 🍰 and eat it too.

It would have been great if @TianyiChang could do a git pull and see if this solution works for MGEs or smaller pangraphs (re: #2695)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2c7dc92b267`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.