> **PROPRIETARY — ALL RIGHTS RESERVED.** © 2026 Mohamed Fathi Alrahman. Not open source. Not MIT. The engines are private. Viewing is not a license.
>
> Press & trade: [PRESS.md](./PRESS.md)

# FathiMind

**Human-centric cognitive engineering operating system.**

This repository is the headquarters. It is not a list of other people's articles. It is the operating handbook for a system that already runs.

```
INPUT (host telemetry)
        │
        ▼
   HelixMind        measure  →  health score, events, insights
        │
        ▼
   MFR-Cognition    verify   →  evidence, confidence, decision object
        │
        ▼
   AetherMind       reason   →  hypotheses, recommendation
        │
        ▼
   SovereignEvolution evolve →  scored next target, permanent memory
```

---

## Table of contents

- [What this is](#what-this-is)
- [The rank above a reading list](#the-rank-above-a-reading-list)
- [Architecture](#architecture)
- [Systems](#systems)
- [Decisions](#decisions)
- [Quality](#quality)
- [Planning and OKRs](#planning-and-okrs)
- [Prioritization](#prioritization)
- [Delivery](#delivery)
- [RFCs](#rfcs)
- [Security](#security)
- [Incidents](#incidents)
- [Strategy](#strategy)
- [Roadmap](#roadmap)
- [How to run](#how-to-run)
- [Docs](#docs)

---

## What this is

FathiMind is the public spine of four repositories owned by [mfathialrahman-crypto](https://github.com/mfathialrahman-crypto):

| Repository | Layer | Version | Cadence |
| --- | --- | --- | --- |
| [HelixMind](https://github.com/mfathialrahman-crypto/HelixMind) | Telemetry and anomaly intelligence | v1.2 | every 2 hours |
| [MFR-Cognition](https://github.com/mfathialrahman-crypto/MFR-Cognition) | Cognitive core | v4.2.219 | every 2 hours |
| [AetherMind](https://github.com/mfathialrahman-crypto/AetherMind) | Intelligence / reasoning | v1.3 | every 2 hours |
| [SovereignEvolution](https://github.com/mfathialrahman-crypto/SovereignEvolution) | Permanent evolution engine | v1.44 | daily 03:00 UTC |

Current engine heads (2026-10-13): HelixMind v1.2 with long-window baseline penalties; MFR-Cognition v4.2.219 with hardened path/secret redaction and decision traces; AetherMind v1.3 with optional sibling envelope ingest (Helix insights/envelope + redacted MFR cognition envelope); SovereignEvolution v1.44 with completed targets including shared-contracts, baseline-learning, cross-project-flow, live-envelope-ingest, project-factory, and outbound envelopes. Shared schemas (RFC-0001) live under `schemas/`.

---

## The rank above a reading list

[charlax/engineering-management](https://github.com/charlax/engineering-management) is a high-quality curated index (books, essays, talks) about engineering leadership. It has earned attention because the topic is large and the table of contents is complete.

It does not:

- produce a decision
- attach evidence or confidence
- measure a running system
- choose the next unit of work with a scored function
- write an audit trail

FathiMind does. That is a higher category, not a louder README.

Stars measure how many people bookmarked a topic. Traces measure whether a system worked this morning.

---

## Architecture

Layers are separated on purpose.

1. **Measure** — HelixMind collects CPU, memory, disk, load, processes, network, uptime. Three detection layers: absolute, statistical, short predictive. Correlated multi-signal events. Explainable health score. Long-window baseline is descriptive and applies capped penalties inside healthy absolute bands.
2. **Verify** — MFR-Cognition turns a metrics snapshot into a decision object: input, evidence, anomalies, confidence, status. Hardened redaction, atomic writes, lock, and size guards.
3. **Reason** — AetherMind forms hypotheses and emits a recommendation only as strong as the confidence. Optionally consumes local Helix and redacted MFR envelopes (stale/invalid ignored).
4. **Evolve** — SovereignEvolution scans the ecosystem, records gaps, and selects the next development target. It does not invent fake diffs. Ships local inbox/outbox, factory board, and envelope validation.

Shared rule: **no tight coupling**. Cross-layer flow is a contract, not a merge.

Full diagram: [docs/architecture.md](docs/architecture.md)

Schemas live in [`schemas/`](./schemas/).

---

## Systems

### HelixMind — measure

Health components: CPU 25 · Memory 25 · Disk 20 · Load 15 · Stability 15.

Outputs: `helix_state.json`, `helix_insights.json`, `helix_events.json`, `helix_report.txt`, `helix_envelope.json`.

### MFR-Cognition — verify

Decision pipeline: input → evidence → reasoning (thresholds + statistical) → confidence → structured output.

Outputs: `state.json`, `decisions.json`, `report.txt`, `cognition_envelope.json` (redacted).

### AetherMind — reason

Pipeline: evidence → hypotheses → confidence → recommendation.

Rule: **no strong recommendation when confidence is low.**

Outputs: `aether_state.json`, `aether_recommendations.json`, `aether_report.txt`.

### SovereignEvolution — evolve

Loops: daily (incremental), weekly (architectural), monthly (strategic).

Priority score = impact × feasibility × strategic × reusability.

Outputs: `evolution_memory.json`, `evolution_status.json`, `daily_report.md`, local outbox envelopes.

---

## Decisions

A decision that cannot be replayed is an opinion.

Minimum fields:

- timestamp (UTC)
- input snapshot
- evidence list
- anomalies
- confidence in `[0.3, 0.98]`
- status: `stable` | `warning` | `critical`
- signature (truncated SHA-256)

Owner: MFR-Cognition. Consumers: AetherMind (local envelope), humans, this handbook.

---

## Quality

Quality is not a slogan. It is HelixMind's health model plus the evolution rule:

> Only real, high-value, safe changes are executed. Artificial changes are forbidden.

Shipped:

- Unit tests on HelixMind, MFR-Cognition, and AetherMind. A red suite blocks the 2-hour cycle.
- Shared JSON schemas (RFC-0001 accepted 2026-09-26). Runtime validation is present in SovereignEvolution and optional elsewhere.
- Cross-project flow via local sibling envelopes (AetherMind discovers Helix and redacted MFR; SovereignEvolution inbox/outbox).
- Long-term baseline learning in HelixMind (capped departure penalties) and SovereignEvolution drift alerts.
- Project Factory operationalization as record-only local board in SovereignEvolution.

Still open / maintenance:

- Further runtime schema validation hardening across all writers (non-blocking where present).
- Continuous security hardening (path/secret redaction, atomicity, locks) — actively maintained.
- Scalability of history retention and observation windows.

Those remaining items are tracked in engine changelogs and the evolution memory, not hidden.

---

## Planning and OKRs

### O1 — Make the ecosystem verifiable

- KR: pytest on the three critical pipelines — **done 2026-09-23**
- KR: one JSON contract for events and decisions — **schemas created 2026-09-26; validation in evolution**
- KR: zero decisions without an evidence trace — in production for MFR

### O2 — Connect layers without merging repositories

- KR: AetherMind optionally reads Helix insights/envelope and redacted MFR cognition envelope — **shipped**
- KR: SovereignEvolution measures execution, not only discovery — **inbox/outbox and completed targets**

### O3 — Keep GitHub at operating-system grade

- KR: profile README + this HQ + architecture / OKR / RFC docs
- KR: public issues for scored targets — core targets completed; handbook updated

Detail: [docs/okrs.md](docs/okrs.md)

---

## Prioritization

SovereignEvolution scores candidates. Core targets from the 2026-09 board are now completed in the engines (see COMPLETED_TARGET_IDS in evolution_engine.py):

| ID | Title | Score | State |
| --- | --- | --- | --- |
| `test-foundation` | Real unit tests across Helix, MFR, Aether | 6480 | **done** |
| `shared-contracts` | Shared event and decision schemas | 5040 | **done** (schemas + evolution validation) |
| `cross-project-flow` | Helix → MFR → Aether | 3888 | **done** (local envelope discovery) |
| `baseline-learning` | Long-term baseline in HelixMind | 2744 | **done** (capped penalties + drift alerts) |

Next work is selected by SovereignEvolution from remaining opportunities or the local factory board. Maintenance scans are preferred when no high-value safe target remains.

---

## Delivery

| Loop | When | What it writes |
| --- | --- | --- |
| Runtime | every 2 hours | state, reports, signatures, envelopes |
| Evolution | daily 03:00 UTC | memory, status, daily report, outbox |
| Handbook | on intent | this repository |

Delivery is a commit of traces, not a slide.

---

## RFCs

Any change that:

- introduces a shared schema
- lets one repo consume another repo's output
- changes the health or confidence model

starts as an RFC in [docs/rfcs.md](docs/rfcs.md). Code follows the RFC, not the other way around.

---

## Security

- No secrets in repositories. Platform credentials stay on the platform.
- Outputs are host metrics and decision traces, not personal data.
- Signatures are integrity hashes of public snapshots, not authentication.
- Path and secret redaction is fail-closed on operator surfaces.
- Report vulnerabilities privately; see [SECURITY.md](SECURITY.md).

---

## Incidents

| Signal | Warning | Critical |
| --- | --- | --- |
| CPU | > 70% | > 85% |
| Memory | > 80% | > 90% |
| Disk | — | > 92% |

AetherMind maps state to `observe` · `monitor_closely` · `investigate_immediately` · `continue_normal_operations`.

HelixMind additionally flags correlated multi-signal pressure and baseline departures.

---

## Strategy

FathiMind is a **human-centric neural extension**, not a chatbot wrapper and not a bookmark wiki.

Direction:

- Keep the four layers distinct
- Make them interoperate through contracts and local envelopes
- Prefer evidence over rhetoric
- Let evolution pick the next honest gap
- Refuse ornamental commits

---

## Roadmap

Core 2026-09 targets are shipped. Ongoing: security/reliability hardening, observation window scaling, and any new scored targets from SovereignEvolution. See engine CHANGELOG.md files and evolution memory for the live board.

## Serve gate

Private skill [`auto-serve`](https://github.com/mfathialrahman-crypto/auto-serve). A result is served only when evidence is present, fresh, and confidence clears the floor AetherMind already enforces (0.45). A calm serve needs 0.70. The skill never mutates an engine and never writes a schema. Helix health is not a confidence.

---

## How to run

Each runtime repository:

```bash
pip install -r requirements.txt
python <entry>.py
```

| Repo | Entry |
| --- | --- |
| HelixMind | `helix_core.py` |
| MFR-Cognition | `brain.py` |
| AetherMind | `core.py` |
| SovereignEvolution | `evolution_engine.py` |

Automation is GitHub Actions on each repository.

---

## Docs

- [Architecture](docs/architecture.md)
- [OKRs](docs/okrs.md)
- [RFCs](docs/rfcs.md)
- [Schemas](./schemas/)
- [Contributing](CONTRIBUTING.md)
- [Security](SECURITY.md)
- [AGENTS.md](AGENTS.md) — Project Engineering Constitution

---

**Owner:** Mohamed Fathi Alrahman · [profile](https://github.com/mfathialrahman-crypto)
