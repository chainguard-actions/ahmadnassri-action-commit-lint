<!-- markdownlint-disable -->

# Hardening Report: ahmadnassri--action-commit-lint/v2.1.16

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ahmadnassri--action-commit-lint/v2.1.16** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. `image: docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.16` uses the tag `2.1.16`, which can be overwritten at any time. This exposes the action to supply-chain attacks where a malicious image is pushed under the same tag. It should be pinned to a SHA digest, e.g. `image: ghcr.io/ahmadnassri/action-commit-lint@sha256:<64-hex-char-digest> # 2.1.16`.

Locations:

- `action.yml:20`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag reference `docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.16` with the immutable SHA digest `docker://ghcr.io/ahmadnassri/action-commit-lint@sha256:c7e02e5c730dc5b3a1ee5f2a8ed07ffc0abdc83d019679b28747e725977e9b00 # 2.1.16` in action.yml line 20. This pins the Docker image to an immutable digest, preventing supply-chain attacks where a malicious image could be pushed under the same tag.

