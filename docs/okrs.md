# OKRs — operating quarter

Cycle source: SovereignEvolution. Status as of 2026-10-13.

## O1 — Make the ecosystem verifiable

| KR | Measure | Status |
| --- | --- | --- |
| Unit tests on Helix, MFR, Aether core pipelines | pytest present and green in CI | **done** |
| One JSON contract for events and decisions | schema files in this repo (`schemas/`) | **done** (RFC-0001) |
| Zero untraced decisions | every decision entry has evidence + confidence | in production for MFR |

## O2 — Connect layers without merging repositories

| KR | Measure | Status |
| --- | --- | --- |
| AetherMind optionally reads Helix + MFR outputs | documented flag / sibling envelope ingest, no crash if files absent | **done** (RFC-0002) |
| Evolution measures execution | engine records gaps and selects next target from real state | **done** (completed targets include baseline-learning, cross-project-flow, live-envelope-ingest, project-factory) |

## O3 — GitHub at operating-system grade

| KR | Measure | Status |
| --- | --- | --- |
| Profile README | `mfathialrahman-crypto/mfathialrahman-crypto` | done |
| HQ handbook | this repository | done |
| Public issues for four targets | issues in FathiMind | done |

## Guardrail

OKRs do not authorize fake velocity. If a KR cannot be evidenced, it stays red.
