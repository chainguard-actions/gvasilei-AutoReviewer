<!-- markdownlint-disable -->

# Hardening Report: gvasilei--AutoReviewer/v0.6.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **gvasilei--AutoReviewer/v0.6.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across the workflow files use mutable version tags instead of full 40-character SHA commit pins, making the workflows vulnerable to supply-chain attacks if the referenced action tags are moved or compromised. Failing references:
- build.yml: `actions/checkout@v6`, `actions/setup-node@v6`
- check-dist.yml: `actions/checkout@v6`, `actions/setup-node@v6`, `actions/upload-artifact@v7`
- code-review.yml: `actions/checkout@v6`
- codeql-analysis.yml: `actions/checkout@v6`, `github/codeql-action/init@v4`, `github/codeql-action/autobuild@v4`, `github/codeql-action/analyze@v4`
- linter.yml: `actions/checkout@v6`, `actions/setup-node@v6`, `super-linter/super-linter/slim@v8`

Each should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/build.yml:18`
- `.github/workflows/build.yml:24`
- `.github/workflows/check-dist.yml:27`
- `.github/workflows/check-dist.yml:33`
- `.github/workflows/check-dist.yml:57`
- `.github/workflows/code-review.yml:14`
- `.github/workflows/codeql-analysis.yml:37`
- `.github/workflows/codeql-analysis.yml:43`
- `.github/workflows/codeql-analysis.yml:55`
- `.github/workflows/codeql-analysis.yml:64`
- `.github/workflows/linter.yml:22`
- `.github/workflows/linter.yml:28`
- `.github/workflows/linter.yml:37`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 13 unpinned `uses:` references across 5 workflow files to full SHA commits:
- build.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803, actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38
- check-dist.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803, actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38, actions/upload-artifact@v7 → @043fb46d1a93c77aae656e7c1c64a875d1fc6a0a
- code-review.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803
- codeql-analysis.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803, github/codeql-action/init@v4 → @ff2f1c621b7f889edc0d3c761ac2e6a3f8cdb0dd, github/codeql-action/autobuild@v4 → @ff2f1c621b7f889edc0d3c761ac2e6a3f8cdb0dd, github/codeql-action/analyze@v4 → @ff2f1c621b7f889edc0d3c761ac2e6a3f8cdb0dd
- linter.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803, actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38, super-linter/super-linter/slim@v8 → @4ce20838b8ab83717e78138c5b3a1407148e0918
All original tags preserved as inline comments.

