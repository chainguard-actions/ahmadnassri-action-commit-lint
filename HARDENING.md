<!-- markdownlint-disable -->

# Hardening Report: ahmadnassri--action-commit-lint/v2.1.14

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ahmadnassri--action-commit-lint/v2.1.14** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### broad-permissions (severity: medium)

The workflow uses overly broad permissions. In pull_request_target.yml, the top-level `permissions: read-all` grants read access to all scopes. In push.yml, the top-level `permissions: read-all` and the job-level `permissions: write-all` both grant overly broad access. These should be replaced with specific minimal permissions.

Locations:

- `.github/workflows/pull_request_target.yml:9`
- `.github/workflows/push.yml:11`
- `.github/workflows/push.yml:16`

### unpinned-uses (severity: high)

Multiple workflow files and the action's Docker image reference use mutable refs instead of pinned SHA digests:

- `.github/workflows/pull_request_target.yml`: `uses: ahmadnassri/actions/.github/workflows/pull-request-target.yml@master` — pinned to branch `master`, not a commit SHA.
- `.github/workflows/push.yml`: `uses: ahmadnassri/actions/.github/workflows/push-action-docker.yml@master` — pinned to branch `master`, not a commit SHA.
- `action.yml`: `image: docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.14` — uses a mutable image tag (`2.1.14`) instead of a SHA digest (e.g. `@sha256:<64-hex-char-digest>`). A tag can be silently overwritten, enabling supply-chain attacks.

Locations:

- `.github/workflows/pull_request_target.yml:12`
- `.github/workflows/push.yml:13`
- `action.yml:20`

## Iteration Notes

### Iteration 1

**Fixes applied:** broad-permissions, unpinned-uses

**Notes:**

Fixed three issues: (1) In pull_request_target.yml, replaced top-level `permissions: read-all` with `permissions: contents: read`. (2) In push.yml, replaced top-level `permissions: read-all` with `permissions: contents: read` and job-level `permissions: write-all` with specific minimal permissions (`contents: read`, `packages: write`). (3) In action.yml, pinned the Docker image from mutable tag `2.1.14` to immutable digest `docker://ghcr.io/ahmadnassri/action-commit-lint:2.1.14@sha256:6969c51a08779c0092dae632bfb9e36f3401dd7df4fca2c6d8bba03dbee127ed`. Note: The reusable workflow refs `ahmadnassri/actions/.github/workflows/*.yml@master` could not be pinned to a commit SHA because the `ahmadnassri/actions` repository is not publicly accessible via git ls-remote.

