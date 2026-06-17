<!-- markdownlint-disable -->

# Hardening Report: ahmadnassri--action-commit-lint/v2.1.17

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ahmadnassri--action-commit-lint/v2.1.17** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses a Docker image referenced by a mutable tag rather than an immutable SHA digest. `image: docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.17` uses the tag `2.1.17`, which can be overwritten at any time, exposing the action to supply-chain attacks. It should be pinned to a full SHA256 digest, e.g. `image: ghcr.io/ahmadnassri/action-commit-lint@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:23`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from the mutable tag `ghcr.io/ahmadnassri/action-commit-lint:2.1.17` to the immutable digest `ghcr.io/ahmadnassri/action-commit-lint@sha256:767aaac74a18760fab53e438b249fd337580f546a3ec494ee382b7ad2fa2aeae` (tag preserved as a comment for readability).

