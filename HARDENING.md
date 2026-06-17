<!-- markdownlint-disable -->

# Hardening Report: ahmadnassri--action-commit-lint/v2.1.15

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ahmadnassri--action-commit-lint/v2.1.15** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses a Docker image referenced by a mutable version tag rather than an immutable SHA digest. `image: docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.15` should be replaced with a SHA-pinned reference such as `image: docker://ghcr.io/ahmadnassri/action-commit-lint@sha256:<64-hex-char-digest>`. A mutable tag can be silently overwritten, enabling a supply-chain attack.

Locations:

- `action.yml:22`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag reference `docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.15` with the immutable SHA256 digest `docker://ghcr.io/ahmadnassri/action-commit-lint@sha256:e8745addfb180f32cd7a8eeb54c642d563cb6d6f42d4b7231ceb84625477212f # 2.1.15` in action.yml line 22. The original tag is preserved as a comment for readability.

