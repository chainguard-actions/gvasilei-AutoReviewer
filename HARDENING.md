<!-- markdownlint-disable -->

# Hardening Report: gvasilei--AutoReviewer/0.5.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **gvasilei--AutoReviewer/0.5.1** was hardened automatically. 5 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in build.yml use mutable version tags instead of full 40-character SHA commit digests, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved. Failing references: `actions/checkout@v4`, `actions/setup-node@v4`.

Locations:

- `.github/workflows/build.yml:19`
- `.github/workflows/build.yml:25`

### unpinned-uses (severity: high)

All `uses:` references in check-dist.yml use mutable version tags instead of full 40-character SHA commit digests. Failing references: `actions/checkout@v4`, `actions/setup-node@v4`, `actions/upload-artifact@v4`.

Locations:

- `.github/workflows/check-dist.yml:26`
- `.github/workflows/check-dist.yml:32`
- `.github/workflows/check-dist.yml:56`

### unpinned-uses (severity: high)

All `uses:` references in code-review.yml use mutable version tags instead of full 40-character SHA commit digests. Failing references: `actions/checkout@v4`.

Locations:

- `.github/workflows/code-review.yml:13`

### unpinned-uses (severity: high)

All `uses:` references in codeql-analysis.yml use mutable version tags instead of full 40-character SHA commit digests. Failing references: `actions/checkout@v4`, `github/codeql-action/init@v3`, `github/codeql-action/autobuild@v3`, `github/codeql-action/analyze@v3`.

Locations:

- `.github/workflows/codeql-analysis.yml:36`
- `.github/workflows/codeql-analysis.yml:42`
- `.github/workflows/codeql-analysis.yml:50`
- `.github/workflows/codeql-analysis.yml:60`

### unpinned-uses (severity: high)

All `uses:` references in linter.yml use mutable version tags instead of full 40-character SHA commit digests. Failing references: `actions/checkout@v4`, `actions/setup-node@v4`, `super-linter/super-linter/slim@v5`.

Locations:

- `.github/workflows/linter.yml:19`
- `.github/workflows/linter.yml:25`
- `.github/workflows/linter.yml:33`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable action tag references to full SHA digests across 5 workflow files:
- build.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020
- check-dist.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02
- code-review.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5
- codeql-analysis.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, github/codeql-action/init@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26, github/codeql-action/autobuild@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26, github/codeql-action/analyze@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26
- linter.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, super-linter/super-linter/slim@v5 → @a8150b40c89574adb5f68bf9502b890a236a06b3
All original tags preserved as inline comments.

### Iteration 2

**Fixes applied:** unpinned-uses

**Notes:**

Fixed two unpinned `uses:` references in `.github/workflows/codeql-analysis.yml`:
1. Line 53: Pinned `github/codeql-action/autobuild@v3` → `github/codeql-action/autobuild@b7351df727350dca84cb9d725d57dcf5bc82ba26 # v3`
2. Line 63: Replaced a malformed step (whose `name:` field was corrupted with an embedded `uses:` reference containing `@v3`) with a proper `Analyze` step using `github/codeql-action/analyze@b7351df727350dca84cb9d725d57dcf5bc82ba26 # v3`. The SHA `b7351df727350dca84cb9d725d57dcf5bc82ba26` was verified via lookup_action_sha and matches the SHA already used for the `init` step in the same workflow.

