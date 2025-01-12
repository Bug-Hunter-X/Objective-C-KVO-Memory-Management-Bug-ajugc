# Objective-C KVO Memory Management Bug

This repository demonstrates a common yet subtle bug in Objective-C related to Key-Value Observing (KVO) and memory management.  Failure to remove KVO observers before the observed object is deallocated can result in crashes or unpredictable behavior.

The `bug.m` file contains code that exhibits this issue.  The `bugSolution.m` file shows the corrected code with proper observer removal.

## Reproducing the Bug

1. Clone this repository.
2. Compile and run `bug.m`. You should observe a crash or unexpected behavior.
3. Examine `bugSolution.m` to see the corrected implementation.

## Understanding the Problem

When an object is deallocated, its associated KVO observers must be explicitly removed using `removeObserver:forKeyPath:`. Failing to do so can lead to the observer attempting to access memory that has already been freed.  This typically manifests as a crash, but can also lead to more insidious and difficult-to-debug problems.