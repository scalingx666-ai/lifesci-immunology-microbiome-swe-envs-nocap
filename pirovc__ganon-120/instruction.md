# Issue

**Title:** Feature/remove use of high resolution clock

## Description

# The what and why

The `std::chrono::high_resolution_clock` is currently the base ticking clock for `StopClock`. The thing is... `high_resolution_clock` is really just an alias. Its usage should be actually **avoided and the real clock should be revealed and explicitly set**. Here is a full explanation from [cppreference](https://en.cppreference.com/w/cpp/chrono/high_resolution_clock):

> The high_resolution_clock is not implemented consistently across different standard library implementations, and its use should be avoided. It is often just an alias for std::chrono::steady_clock or std::chrono::system_clock, but which one it is depends on the library or configuration. When it is a system_clock, it is not monotonic (e.g., the time can go backwards). For example, for gcc's libstdc++ it is system_clock, for MSVC it is steady_clock, and for clang's libc++ it depends on configuration.

That means that, so far, `ganon` was using a `std::chrono::system_clock` under the hood. One can easily check that the `operator<<` definition on `StopClock` was actually already calling the `system_clock`:

```
const auto time = std::chrono::system_clock::to_time_t( timepoint );
stream << std::put_time( std::localtime( &time ), "%c" );
```

Also, once again from [cppreference](https://en.cppreference.com/w/cpp/chrono/system_clock):

> It is the only C++ clock that has the ability to map its time points to C-style time.

That's the reason why we could "print" the result from the clock...

With all that said, this PR brings actually **no functional change**. It only exposes the real clock we were using.

# Und dann, was ist los?

Now that we know we are using the `system_clock`, the question is should we be really using it? In general, there seems to be a consent on the fact that using a monotonic clock to measure intervals is a better option. Here are a few words again from [cppreference](https://en.cppreference.com/w/cpp/chrono/steady_clock):

> Class std::chrono::steady_clock represents a monotonic clock. The time points of this clock cannot decrease as physical time moves forward and the time between ticks of this clock is constant. This clock is not related to wall clock time (for example, it can be time since last reboot), and is most suitable for measuring intervals.

I don't have the answer to this... maybe we should research a bit more? Once again, the main goal here was to remove the cloak from `std::chrono::high_resolution_clock` and reveal the clock actually being used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `260dea8af0af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.