# Issue

**Title:** reduce memory footprint and increase speed when creating FCS files

## Description

I noticed a significant increase of memory usage with `create_fcs` when writing concatenated data from a large (> 30 GiB) dataset: The memory footprint shot up to 150-200% of the maximum footprint during concatenation - while creating the final file. The concatenated events were already stored in the correct object type and datatype, so I started investigating...

This pull request addresses the issue by avoiding the conversion of the `event_data` (Python iterator type) to an `array.array('f', event_data)` when both object type and datatype already match with the required types - the data is then just passed as a reference, instead of creating a copy of the data before writing. For all those datasets this will increase performance when writing. For large datasets this will additionally reduce the risk of out-of-memory errors as well.


Details about the root cause:

The call to `array.array('f', event_data)` produces a deep copy of the input data, even if `event_data` is already an array with elements of the desired datatype. Here's the [`arraymodule.c`](https://github.com/python/cpython/blob/3.12/Modules/arraymodule.c) and the [relevant line](https://github.com/python/cpython/blob/580d7810946ba13f07847c0deab89c0edfe01cb7/Modules/arraymodule.c#L2721) in the CPtyon repo:
```Python
else if (initial != NULL && array_Check(initial, state) && len > 0) {
    arrayobject *self = (arrayobject *)a;
    arrayobject *other = (arrayobject *)initial;
    memcpy(self->ob_item, other->ob_item, len * other->ob_descr->itemsize);
}
```
I'm sure there's good reasons to pass a copy to the users (avoid side effects probably), but that comes with a performance and memory penalty.

Demonstration of the increase in memory usage (+75%):

```Python
import os
import psutil
from array import array

def print_memory_usage(label: str) -> None:
    process = psutil.Process(os.getpid())
    memory_mb = process.memory_info().rss / (1024 ** 2)
    print(f"{label}:\n{memory_mb:.2f} MB", end='\n\n', flush=True)

def main():
    # Create a large array of floats, approx. 100 MiB
    my_events = array('f', [float(i) for i in range(20_000_000)])
    print_memory_usage("Memory usage with `my_events`")
   
    # Assign event data to new variable - passing a reference
    float_array = my_events
    print(f"`float_array` is a reference to `my_events`: {float_array is my_events}")
    print_memory_usage("Memory usage with `float_array` pointing to `my_events`")

    # Assign casted event data to new variable - passing a copy
    float_array = array('f', my_events)
    print(f"`float_array` is a reference to `my_events`: {float_array is my_events}")
    print_memory_usage("Memory usage with `my_events` copied to `float_array`")

if __name__ == "__main__":
    main()
```
```Terminal
Memory usage with `my_events`:
99.59 MB

`float_array` is a reference to `my_events`: True
Memory usage with `float_array` pointing to `my_events`:
99.61 MB

`float_array` is a reference to `my_events`: False
Memory usage with `my_events` copied to `float_array`:
175.91 MB

```

The suggested code change is straightforward - and avoids both the performance penalty and the increase in memory usage when `event_data` is already an `array.array()` with the correct datatype.


Testing of the changed code:
```terminal
(flowio) christianrickert@MBP FlowIO % pip install . && python run_tests.py
Processing ./FlowIO
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Building wheels for collected packages: FlowIO
  Building wheel for FlowIO (pyproject.toml) ... done
  Created wheel for FlowIO: filename=FlowIO-1.3.0-py3-none-any.whl size=18810 sha256=1d7e4ade7abc4e570d24cad0260e064824b346e380e1a9f42e8ed6e4326ef899
  Stored in directory: /private/var/folders/69/_bcjpnpx5xs5xwtnxydjdsd00000gn/T/pip-ephem-wheel-cache-52jgfqyn/wheels/a5/12/b4/ef0e59b15408ccfe63acd58ef10f4e10fe58a9750a13b803e1
Successfully built FlowIO
Installing collected packages: FlowIO
  Attempting uninstall: FlowIO
    Found existing installation: FlowIO 1.3.0
    Uninstalling FlowIO-1.3.0:
      Successfully uninstalled FlowIO-1.3.0
Successfully installed FlowIO-1.3.0
...............................
----------------------------------------------------------------------
Ran 31 tests in 1.704s

OK
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `285fa578699a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.