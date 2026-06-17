<!-- markdownlint-disable -->

# Hardening Report: ahmadnassri--action-commit-lint/v2.1.14

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ahmadnassri--action-commit-lint/v2.1.14** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image referenced by a mutable tag rather than an immutable SHA digest. `image: docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.14` uses the tag `2.1.14`, which can be silently overwritten to point to a different (potentially malicious) image. It should be pinned to a specific SHA digest, e.g. `image: ghcr.io/ahmadnassri/action-commit-lint@sha256:<64-hex-char-digest> # 2.1.14`.

Locations:

- `action.yml:21`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag reference `docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.14` with the immutable SHA digest `docker://ghcr.io/ahmadnassri/action-commit-lint@sha256:6969c51a08779c0092dae632bfb9e36f3401dd7df4fca2c6d8bba03dbee127ed # 2.1.14` in action.yml line 21. The original tag is preserved as a comment for readability.

