<!-- markdownlint-disable -->

# Hardening Report: ahmadnassri--action-commit-lint/v2.1.13

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **ahmadnassri--action-commit-lint/v2.1.13** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image referenced by a mutable tag (`docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.13`) instead of an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the action reference. It should be pinned to a specific SHA digest, e.g. `docker://ghcr.io/ahmadnassri/action-commit-lint@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:20`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `ghcr.io/ahmadnassri/action-commit-lint:2.1.13` with its immutable SHA digest `ghcr.io/ahmadnassri/action-commit-lint@sha256:b97d068a02ebe06b93a7e143c9f42037829a26042ab485b4dfcc0ece6ed00c10` in action.yml line 20. The original tag is preserved as a comment for readability.

