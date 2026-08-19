<!-- markdownlint-disable -->

# Hardening Report: gvasilei--AutoReviewer/0.5

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **gvasilei--AutoReviewer/0.5** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in workflow files use mutable tag refs instead of pinned 40-character commit SHA digests, making the workflows vulnerable to supply-chain attacks if the referenced action tags are moved or compromised.

Failing references in build.yml:
- `actions/checkout@v4`
- `actions/setup-node@v4`

Failing references in check-dist.yml:
- `actions/checkout@v4`
- `actions/setup-node@v4`
- `actions/upload-artifact@v4`

Failing references in code-review.yml:
- `actions/checkout@v4`

Failing references in codeql-analysis.yml:
- `actions/checkout@v4`
- `github/codeql-action/init@v3`
- `github/codeql-action/autobuild@v3`
- `github/codeql-action/analyze@v3`

Failing references in linter.yml:
- `actions/checkout@v4`
- `actions/setup-node@v4`
- `super-linter/super-linter/slim@v5`

Locations:

- `.github/workflows/build.yml:19`
- `.github/workflows/build.yml:25`
- `.github/workflows/check-dist.yml:25`
- `.github/workflows/check-dist.yml:31`
- `.github/workflows/check-dist.yml:52`
- `.github/workflows/code-review.yml:13`
- `.github/workflows/codeql-analysis.yml:35`
- `.github/workflows/codeql-analysis.yml:41`
- `.github/workflows/codeql-analysis.yml:49`
- `.github/workflows/codeql-analysis.yml:60`
- `.github/workflows/linter.yml:19`
- `.github/workflows/linter.yml:25`
- `.github/workflows/linter.yml:35`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 13 unpinned `uses:` references across 5 workflow files to full 40-character commit SHAs:
- actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262 (used in build.yml, check-dist.yml, code-review.yml, codeql-analysis.yml, linter.yml)
- actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020 (used in build.yml, check-dist.yml, linter.yml)
- actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02 (used in check-dist.yml)
- github/codeql-action/init@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26 (used in codeql-analysis.yml)
- github/codeql-action/autobuild@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26 (used in codeql-analysis.yml)
- github/codeql-action/analyze@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26 (used in codeql-analysis.yml)
- super-linter/super-linter/slim@v5 → @a8150b40c89574adb5f68bf9502b890a236a06b3 (used in linter.yml)
All original tag names preserved as inline comments (e.g., # v4) for readability. Two files (check-dist.yml and codeql-analysis.yml) were rewritten entirely due to corruption from partial edits.

