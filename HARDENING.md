<!-- markdownlint-disable -->

# Hardening Report: gvasilei--AutoReviewer/0.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **gvasilei--AutoReviewer/0.4** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across the workflow files use mutable tags instead of pinned 40-character SHA digests, making the workflows vulnerable to supply-chain attacks if the referenced action tags are moved or compromised.

Failing references:
- `.github/workflows/build.yml`: `actions/checkout@v3`
- `.github/workflows/check-dist.yml`: `actions/checkout@v3`, `actions/setup-node@v3.6.0`, `actions/upload-artifact@v3`
- `.github/workflows/code-review.yml`: `actions/checkout@v3`
- `.github/workflows/codeql-analysis.yml`: `actions/checkout@v3`, `github/codeql-action/init@v2`, `github/codeql-action/autobuild@v2`, `github/codeql-action/analyze@v2`

Locations:

- `.github/workflows/build.yml:11`
- `.github/workflows/check-dist.yml:21`
- `.github/workflows/check-dist.yml:24`
- `.github/workflows/check-dist.yml:44`
- `.github/workflows/code-review.yml:14`
- `.github/workflows/codeql-analysis.yml:34`
- `.github/workflows/codeql-analysis.yml:39`
- `.github/workflows/codeql-analysis.yml:47`
- `.github/workflows/codeql-analysis.yml:53`

### missing-permissions (severity: medium)

`build.yml` and `check-dist.yml` have no top-level `permissions:` key and no job-level `permissions:` key on any of their jobs. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/build.yml:1`
- `.github/workflows/check-dist.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 4 workflow files:

1. **build.yml**: Pinned `actions/checkout@v3` → `@a37ce9120846195fa4ece8f58b268e6043cb2f26 # v3`; added top-level `permissions: contents: read`.

2. **check-dist.yml**: Pinned `actions/checkout@v3` → `@a37ce9120846195fa4ece8f58b268e6043cb2f26 # v3`, `actions/setup-node@v3.6.0` → `@64ed1c7eab4cce3362f8c340dee64e5eaeef8f7c # v3.6.0`, `actions/upload-artifact@v3` → `@ff15f0306b3f739f7b6fd43fb5d26cd321bd4de5 # v3`; added top-level `permissions: contents: read`.

3. **code-review.yml**: Pinned `actions/checkout@v3` → `@a37ce9120846195fa4ece8f58b268e6043cb2f26 # v3`; permissions block already existed (`contents: read`, `pull-requests: write`).

4. **codeql-analysis.yml**: Pinned `actions/checkout@v3` → `@a37ce9120846195fa4ece8f58b268e6043cb2f26 # v3`, `github/codeql-action/init@v2`, `autobuild@v2`, and `analyze@v2` all → `@b8d3b6e8af63cde30bdc382c0bc28114f4346c88 # v2`; job-level permissions block already existed.

