# Review Severity

## Purpose

This document defines the severity labels for reviewing plans and repo-grounded spec amendments.

## Severity Levels

Every review comment should be classified as one of:

- `Blocking`: must be addressed before continuing the current slice.
- `Non-blocking`: should be addressed soon, but does not invalidate the current slice.
- `Optional`: safe to ignore.

`Nitpick` may be used as a synonym for `Optional`, but `Optional` is the preferred label in committed repo docs.

## Blocking Rule

A review comment is usually blocking only when it changes one of these:

- the first safe slice,
- the active stage boundary,
- the v0 scope,
- the core architecture seams,
- what is truly required to begin implementation safely.

If a review does not change one of those, it is usually not blocking.

## Review Posture

Review should be diff-oriented.
Do not reopen the whole plan unless a locked decision was actually disturbed.

The point of severity labels is to keep review useful without turning every pass into a full redesign.
