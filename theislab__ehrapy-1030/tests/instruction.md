# Issue

**Title:** Non-negative CP decomposition of 3D data

## Description

## Description of changes

Adds three new functions for **Non-negative CP (PARAFAC) tensor factorisation** of 3-D `EHRData` objects (observations × variables × time), together with two matching plot functions.

### New functions

| Function | Location | Description |
|---|---|---|
| `ep.tl.ncp` | `ehrapy/tools/_ncp.py` | Decomposes a 3-D layer into `rank` non-negative triplets (patient / variable / time factors). Uses `tensorly` when installed; falls back to a built-in numpy ALS implementation. Results stored in `.obsm`, `.varm`, `.uns`. |
| `ep.pl.ncp` | `ehrapy/plot/_ncp.py` | Three-panel-per-component layout: temporal profile · top-loaded variables · sample-loading histogram. |
| `ep.pl.ncp_cluster_trajectories` | `ehrapy/plot/_ncp.py` | Per-cluster mean risk trajectories for the variables most characteristic of each cluster's dominant NCP component. |

### Dependencies

`tensorly`

### Examples

```py
import numpy as np, pandas as pd
import ehrdata as ed, ehrapy as ep
np.random.seed(0)
tensor = np.abs(np.random.randn(30, 8, 12))  # patients × vars × time
edata = ed.EHRData(
     shape=(30, 8),
     layers={"data": tensor},
     var=pd.DataFrame(index=[f"var_{i}" for i in range(8)]),
)
ep.tl.ncp(edata, layer="data", rank=3)
edata.obsm["X_ncp"].shape        # (30, 3)  – sample factors
edata.varm["ncp_loadings"].shape  # (8, 3)   – variable factors
edata.uns["ncp"]["temporal_factors"].shape  # (12, 3) – time factors
```

```py
import numpy as np, pandas as pd
import ehrdata as ed, ehrapy as ep

np.random.seed(0)
tensor = np.abs(np.random.randn(30, 8, 12))
edata = ed.EHRData(
    shape=(30, 8),
    layers={"data": tensor},
    var=pd.DataFrame(index=[f"var_{i}" for i in range(8)]),
)
ep.tl.ncp(edata, layer="data", rank=3)

ep.pl.ncp(edata, n_top=5)
```
<img width="851" height="766" alt="ncp" src="https://github.com/user-attachments/assets/b5777355-3f7c-4f77-b55d-8380d877a38b" />

```py
import numpy as np, pandas as pd
import ehrdata as ed, ehrapy as ep

np.random.seed(0)
tensor = np.abs(np.random.randn(30, 8, 12))
obs = pd.DataFrame(
    {"group": ["A"] * 15 + ["B"] * 15},
    index=[str(i) for i in range(30)],
)
edata = ed.EHRData(
    shape=(30, 8),
    layers={"data": tensor},
    obs=obs,
    var=pd.DataFrame(index=[f"var_{i}" for i in range(8)]),
)
ep.tl.ncp(edata, layer="data", rank=3)
ep.pl.ncp_cluster_trajectories(edata, layer="data", cluster_key="group")
```
<img width="644" height="246" alt="ncp_cluster_trajectories" src="https://github.com/user-attachments/assets/aef1acdd-5129-42e1-a2b6-aa84953b8dbb" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a4ad385bcef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.