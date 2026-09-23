# OKRs — operating quarter

Cycle source: SovereignEvolution v1.1. test-foundation shipped 2026-09-23.

## O1 — Make the ecosystem verifiable

| KR | Measure | Status |
| --- | --- | --- |
| Unit tests on Helix, MFR, Aether core pipelines | pytest present and green in CI | **done 2026-09-23** |
| One JSON contract for events and decisions | schema files in this repo, consumed by runtimes | not started |
| Zero untraced decisions | every `decisions.json` entry has evidence + confidence | in production for MFR |

## O2 — Connect layers without merging repositories

| KR | Measure | Status |
| --- | --- | --- |
| AetherMind optionally reads Helix + MFR outputs | documented flag, no crash if files absent | not started |
| Evolution measures execution | report gap list edited by hand; the engine does not clone the other repos | corrected — not an automatic scanner |

## O3 — GitHub at operating-system grade

| KR | Measure | Status |
| --- | --- | --- |
| Profile README | `mfathialrahman-crypto/mfathialrahman-crypto` | done |
| HQ handbook | this repository | done |
| Public issues for four targets | issues in FathiMind | done |

## Guardrail

OKRs do not authorize fake velocity. If a KR cannot be evidenced, it stays red.
