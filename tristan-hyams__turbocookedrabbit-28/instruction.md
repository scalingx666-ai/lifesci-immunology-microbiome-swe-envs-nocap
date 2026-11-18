# Issue

**Title:** Acquire lock before fetch Started, to prevent data-race

## Description

Hi, now i am working on library which are rely on this. I want to close all my library channels only after consumer really stop consuming loop. For example:
```go
err := consuming.consumer.StopConsuming(immediately, flushMessages)
if err != nil {
	return errors.WithMessage(err, "stop consumer")
}

// NOTE: do not close output channel while underlying consumer really stops
for consuming.consumer.Started() {
	time.Sleep(10 * time.Millisecond)
}

close(consuming.outputChan)
```

And now, when i run tests, i've got a data-race, because i want to read variable Started, and at the same time this variable changed by consumer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57af75f9f9cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.