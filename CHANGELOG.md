# Changelog

All notable changes to the FathiMind handbook and shared contracts are documented here.

The format is based on Keep a Changelog, and this project adheres to semantic versioning where applicable for the handbook.

## [Unreleased]

### Changed
- Public Core Pro references in README (badge, ecosystem table, status paragraph) aligned to verified v2.1.41-pro (SSOT version.py). Reflects CLI regression fix (full parser and demo() restored after accidental removal during magic-number extraction in v2.1.40-pro), retained named constants (CONFLICT_SECOND_THRESHOLD, STABLE_CONFIDENCE_THRESHOLD, FALLBACK_VARIANCE, VARIANCE_FLOOR, CI_Z_SCORE, PRIOR_STRENGTH, OPPOSITION_FACTOR), 38/38 unit tests, mypy --strict clean, and version-consistency CI green. No numerical behavior change.

### Documented
- Independent full ecosystem inspection cycle (2026-10-27): Core Pro re-verified at v2.1.41-pro with CI success, 38/38 tests, and restored CLI. AGENTS.md constitution review notes already current. No critical issues.

## [2026-10-26]

### Changed
- Public Core Pro version in README badge, ecosystem table, and status paragraph synchronized to v2.1.38-pro.
- AGENTS.md footer updated to record the latest inspection and alignment cycle results.

## [2026-10-25]

### Changed
- Public Core Pro version in README badge, ecosystem table, and status paragraph synchronized to v2.1.34-pro.
- AGENTS.md footer updated to record inspection cycle results.

## [2026-10-24]

### Changed
- Public Core Pro version in README badge, ecosystem table, and status paragraph synchronized to v2.1.28-pro.
- Previous unreleased notes updated for accuracy.

## [2026-10-23]

### Changed
- Public Core Pro version in README badge, ecosystem table, and status paragraph synchronized to v2.1.22-pro.
- Confirmed AGENTS.md constitution present and reviewed across the ecosystem.

## [2026-10-22]

### Changed
- Confirmed AGENTS.md constitution present and reviewed across the ecosystem.
- Synchronized Public Core Pro status to v2.1.17-pro (historical).

## [2026-10-21]

### Added
- Long-horizon section in AGENTS.md matching the continuous development cycle doctrine.
- Current ecosystem status table and heads in README.

### Changed
- Documentation synchronized with implemented RFCs and OKRs.

## [2026-09-26]

### Added
- Versioned JSON schemas under `schemas/` for Event, Decision, Recommendation, Target (RFC-0001 implemented).
- RFC-0002 optional sibling envelope ingest documented.

### Changed
- Architecture diagram and layer contracts updated.

## [2026-09-18]

### Added
- Initial FathiMind HQ handbook, OKRs, RFCs template, and public issues for evolution targets.

## [2026-10-21] continued

### Changed
- Closed completed evolution target issues #2 (shared-contracts), #3 (cross-project-flow), #4 (baseline-learning) after verification against implemented schemas, RFC docs, and private engine status.
