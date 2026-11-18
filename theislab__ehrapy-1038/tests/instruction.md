# Issue

**Title:** NCP without tensorly dependency

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [x] This comment contains a description of changes (with reason)
- [x] Referenced issue is linked 
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Documentation in `docs` is updated

**Description of changes**
 .

<!-- Please state what you've changed and how it might affect the user. -->

**Technical details**

Removes `tensorly` dependency, and replace with a custom implemention in numpy.

**In a nutshell**

- Custom implementation takes longer until converged, but equal reconstruction quality
- Custom implementation on par with speed as tensorly
- Custom implementation can recover signal as tensorly can for synthetic data


## Compare ehrapy vs tensorly on synthetic data

### Compare convergence
```py
import numpy as np
import pandas as pd
import time
import matplotlib.pyplot as plt

rng = np.random.default_rng(42)

n_obs, n_vars, n_time = 50, 10, 20
true_rank = 3

A_true = np.abs(rng.standard_normal((n_obs, true_rank)))
B_true = np.abs(rng.standard_normal((n_vars, true_rank)))
C_true = np.abs(rng.standard_normal((n_time, true_rank)))

tensor = np.einsum('ir,jr,kr->ijk', A_true, B_true, C_true)
tensor += 0.1 * np.abs(rng.standard_normal(tensor.shape))
```

```py
import ehrdata as ed
import ehrapy as ep

edata = ed.EHRData(
    shape=(n_obs, n_vars),
    layers={"data": tensor.copy()},
    var=pd.DataFrame(index=[f"var_{i}" for i in range(n_vars)]),
)

rank = true_rank

t0 = time.perf_counter()
ep.tl.ncp(edata, layer="data", rank=rank, n_iter_max=300, random_state=0)
time_ep = time.perf_counter() - t0

A_ep = edata.obsm["X_ncp"]
B_ep = edata.varm["ncp_loadings"]
C_ep = edata.uns["ncp"]["temporal_factors"]

recon_ep = np.zeros_like(tensor)
for r in range(rank):
    recon_ep += np.einsum('i,j,k', A_ep[:, r], B_ep[:, r], C_ep[:, r])
error_ep = np.linalg.norm(tensor - recon_ep) / np.linalg.norm(tensor)

print(f"ehrapy (numpy):  error={error_ep:.6f}  time={time_ep:.3f}s")
```

```py
import tensorly
from tensorly.decomposition import non_negative_parafac

t0 = time.perf_counter()
weights_tl, factors_tl = non_negative_parafac(
    tensor, rank=rank, init="random", n_iter_max=300, random_state=0
)
time_tl = time.perf_counter() - t0

recon_tl = tensorly.cp_to_tensor((weights_tl, factors_tl))
error_tl = np.linalg.norm(tensor - recon_tl) / np.linalg.norm(tensor)

print(f"tensorly:        error={error_tl:.6f}  time={time_tl:.3f}s")
print(f"ehrapy (numpy):  error={error_ep:.6f}  time={time_ep:.3f}s")
```

**Convergence and reconstruction**
```py
# Run ehrapy's internal function to get per-iteration errors
from ehrapy.tools._ncp import _nonneg_cp

# We can track convergence by running _nonneg_cp with small n_iter_max repeatedly
errors_ep = []
for n in range(1, 301):
    w, fs = _nonneg_cp(tensor, rank=rank, n_iter_max=n, random_state=0)
    recon = np.zeros_like(tensor)
    for r in range(rank):
        component = w[r] * np.einsum('i,j,k', fs[0][:, r], fs[1][:, r], fs[2][:, r])
        recon += component
    errors_ep.append(np.linalg.norm(tensor - recon) / np.linalg.norm(tensor))
    if n > 1 and abs(errors_ep[-2] - errors_ep[-1]) < 1e-8:
        break

fig, axes = plt.subplots(1, 2, figsize=(12, 4))

axes[0].plot(errors_ep, label="ehrapy (numpy MU)")
axes[0].axhline(error_tl, color="red", ls="--", label=f"tensorly final ({error_tl:.5f})")
axes[0].set_xlabel("Iteration")
axes[0].set_ylabel("Relative reconstruction error")
axes[0].set_title("Convergence")
axes[0].legend()

flat_orig = tensor.ravel()
axes[1].scatter(flat_orig, recon_tl.ravel(), s=2, alpha=0.3, label="tensorly")
axes[1].scatter(flat_orig, recon_ep.ravel(), s=2, alpha=0.3, label="ehrapy")
lims = [0, flat_orig.max()]
axes[1].plot(lims, lims, 'k--', lw=0.5)
axes[1].set_xlabel("Original")
axes[1].set_ylabel("Reconstructed")
axes[1].set_title("Reconstruction quality")
axes[1].legend()

plt.tight_layout()
plt.show()
```

<img width="1189" height="390" alt="image" src="https://github.com/user-attachments/assets/736e19e4-44c6-4fd0-9b37-d9843d44b167" />

Comment: tensorly converged in less iterations.

### Compare runtime

```py
from ehrapy.tools._ncp import _nonneg_cp

sizes = [(20, 5, 10), (50, 10, 20), (100, 100, 40), (2000, 300, 60)]
results = []

for shape in sizes:
    t = np.abs(rng.standard_normal(shape)) + 0.01
    label = "×".join(str(s) for s in shape)

    t0 = time.perf_counter()
    non_negative_parafac(t, rank=3, init="random", n_iter_max=100, random_state=0)
    dt_tl = time.perf_counter() - t0

    t0 = time.perf_counter()
    _nonneg_cp(t, rank=3, n_iter_max=100, random_state=0)
    dt_ep = time.perf_counter() - t0

    results.append((label, dt_tl, dt_ep))
    print(f"{label:>15s}  tensorly={dt_tl:.3f}s  ehrapy={dt_ep:.3f}s  ratio={dt_ep/dt_tl:.1f}x")
```

```
       20×5×10  tensorly=0.017s  ehrapy=0.018s  ratio=1.0x
       50×10×20  tensorly=0.019s  ehrapy=0.066s  ratio=3.4x
     100×100×40  tensorly=0.097s  ehrapy=0.052s  ratio=0.5x
    1000×200×60  tensorly=3.974s  ehrapy=2.456s  ratio=0.6x
   20000×300×60  tensorly=196.115s  ehrapy=206.691s  ratio=1.1x
```

Comment: tensorly is matched in speed in order of magnitude

### Compare ability to recover known signal

```py
import ehrdata as ed
import ehrapy as ep

rng = np.random.default_rng(0)

n_patients, n_vars, n_time = 45, 3, 12
rank = 3
grp_size = n_patients // rank  # 15 patients per group

# -- Patient factors: three distinct groups --
A = np.zeros((n_patients, rank))
for r in range(rank):
    lo, hi = r * grp_size, (r + 1) * grp_size
    A[lo:hi, r] = rng.uniform(0.8, 1.2, size=grp_size)
    for other in range(rank):
        if other != r:
            A[lo:hi, other] = rng.uniform(0.0, 0.10, size=grp_size)

# -- Variable factors: each variable dominated by one component --
B = np.array([
    [1.0,  0.05, 0.05],   # heart_rate      → component 1
    [0.05, 1.0,  0.05],   # blood_pressure  → component 2
    [0.05, 0.05, 1.0 ],   # inflammation    → component 3
])

# -- Time factors: three distinct temporal signatures --
t = np.linspace(0, 1, n_time)
C = np.column_stack([
    1 - np.exp(-3 * t),                         # component 1: saturating rise
    np.exp(-2 * t),                              # component 2: exponential decay
    np.exp(-0.5 * ((t - 0.5) / 0.15) ** 2),     # component 3: Gaussian peak at midpoint
])

# Build tensor and add small noise
tensor_ex = np.einsum("ir,jr,kr->ijk", A, B, C)
tensor_ex += 0.02 * rng.uniform(size=tensor_ex.shape)

var_names = ["heart_rate", "blood_pressure", "inflammation"]
obs = pd.DataFrame(
    {"group": ["A"] * grp_size + ["B"] * grp_size + ["C"] * grp_size},
    index=[f"patient_{i}" for i in range(n_patients)],
)
edata_ex = ed.EHRData(
    shape=(n_patients, n_vars),
    layers={"data": tensor_ex},
    obs=obs,
    var=pd.DataFrame(index=var_names),
)

ep.tl.ncp(edata_ex, layer="data", rank=rank, n_iter_max=500, random_state=0)

print("Shapes:")
print(f"  obsm  X_ncp:            {edata_ex.obsm['X_ncp'].shape}")
print(f"  varm  ncp_loadings:     {edata_ex.varm['ncp_loadings'].shape}")
print(f"  uns   temporal_factors: {edata_ex.uns['ncp']['temporal_factors'].shape}")
```

```py
import tensorly
from tensorly.decomposition import non_negative_parafac

weights_tl, factors_tl = non_negative_parafac(
    tensor_ex, rank=rank, init="random", n_iter_max=500, random_state=0
)

edata_ex_tl = ed.EHRData(
    shape=(n_patients, n_vars),
    layers={"data": tensor_ex},
    obs=obs.copy(),
    var=pd.DataFrame(index=var_names),
)

A_tl, B_tl, C_tl = factors_tl
norms = np.maximum(np.linalg.norm(A_tl, axis=0), 1e-12)
edata_ex_tl.obsm["X_ncp"] = A_tl / norms[np.newaxis, :]
norms_b = np.maximum(np.linalg.norm(B_tl, axis=0), 1e-12)
edata_ex_tl.varm["ncp_loadings"] = B_tl / norms_b[np.newaxis, :]
norms_c = np.maximum(np.linalg.norm(C_tl, axis=0), 1e-12)
edata_ex_tl.uns["ncp"] = {"temporal_factors": C_tl / norms_c[np.newaxis, :]}

print("tensorly shapes:")
print(f"  obsm  X_ncp:            {edata_ex_tl.obsm['X_ncp'].shape}")
print(f"  varm  ncp_loadings:     {edata_ex_tl.varm['ncp_loadings'].shape}")
print(f"  uns   temporal_factors: {edata_ex_tl.uns['ncp']['temporal_factors'].shape}")
```

**ehrapy implementation recovered factors**
```py
print("— ehrapy (NumPy MU) —")
ep.pl.ncp(edata_ex, n_top=3)
```

<img width="793" height="493" alt="image" src="https://github.com/user-attachments/assets/5453698b-35b3-441e-8ead-ee23258cda64" />

**tensorly implementation recovered factors**
```py
print("\n— tensorly (HALS) —")
ep.pl.ncp(edata_ex_tl, n_top=3)
```
<img width="771" height="513" alt="image" src="https://github.com/user-attachments/assets/390dafbf-7064-4f38-9477-190458fa9039" />


Comment: both tensorly and ehrapy recover known longitudinal structure.
<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. here. -->

**Additional context**

<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee138c3cc53e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.