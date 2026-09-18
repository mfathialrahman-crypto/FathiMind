> **PROPRIETARY — ALL RIGHTS RESERVED.** © 2026 Mohamed Fathi Alrahman. Not open source. Not MIT. The engines are private. Viewing is not a license.

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
| [HelixMind](https://github.com/mfathialrahman-crypto/HelixMind) | Telemetry and anomaly intelligence | v1.1 | every 2 hours |
| [MFR-Cognition](https://github.com/mfathialrahman-crypto/MFR-Cognition) | Cognitive core | v4.1 | every 2 hours |
| [AetherMind](https://github.com/mfathialrahman-crypto/AetherMind) | Intelligence / reasoning | v1.1 | every 2 hours |
| [SovereignEvolution](https://github.com/mfathialrahman-crypto/SovereignEvolution) | Permanent evolution engine | v1.1 | daily 03:00 UTC |

Last recorded cycle (2026-09-18): Helix health **100**, MFR **STABLE / 0.85**, Aether `continue_normal_operations / 0.80`, cognition generation **238**.

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

1. **Measure** — HelixMind collects CPU, memory, disk, load, processes, network, uptime. Three detection layers: absolute, statistical, short predictive. Correlated multi-signal events. Explainable health score.
2. **Verify** — MFR-Cognition turns a metrics snapshot into a decision object: input, evidence, anomalies, confidence, status.
3. **Reason** — AetherMind forms hypotheses and emits a recommendation only as strong as the confidence.
4. **Evolve** — SovereignEvolution scans the ecosystem, records gaps, and selects the next development target. It does not invent fake diffs.

Shared rule: **no tight coupling**. Cross-layer flow is a contract, not a merge.

Full diagram: [docs/architecture.md](docs/architecture.md)

---

## Systems

### HelixMind — measure

Health components: CPU 25 · Memory 25 · Disk 20 · Load 15 · Stability 15.

Outputs: `helix_state.json`, `helix_insights.json`, `helix_events.json`, `helix_report.txt`.

### MFR-Cognition — verify

Decision pipeline: input → evidence → reasoning (thresholds + statistical) → confidence → structured output.

Outputs: `state.json`, `decisions.json`, `report.txt`.

### AetherMind — reason

Pipeline: evidence → hypotheses → confidence → recommendation.

Rule: **no strong recommendation when confidence is low.**

Outputs: `aether_state.json`, `aether_recommendations.json`, `aether_report.txt`.

### SovereignEvolution — evolve

Loops: daily (incremental), weekly (architectural), monthly (strategic).

Priority score = impact × feasibility × strategic × reusability.

Outputs: `evolution_memory.json`, `evolution_status.json`, `daily_report.md`.

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

Owner: MFR-Cognition. Consumers: AetherMind (planned), humans, this handbook.

---

## Quality

Quality is not a slogan. It is HelixMind's health model plus the evolution rule:

> Only real, high-value, safe changes are executed. Artificial changes are forbidden.

Current honest gaps (from SovereignEvolution memory):

- No unit tests in any runtime repository
- No shared event/schema contracts
- No cross-project data flow yet
- No long-term baseline learning
- Project Factory discovered, not operational

Those gaps are the roadmap. They are not hidden.

---

## Planning and OKRs

### O1 — Make the ecosystem verifiable

- KR: pytest on the three critical pipelines
- KR: one JSON contract for events and decisions
- KR: zero decisions without an evidence trace

### O2 — Connect layers without merging repositories

- KR: AetherMind optionally reads `helix_insights.json` and `decisions.json`
- KR: SovereignEvolution measures execution, not only discovery

### O3 — Keep GitHub at operating-system grade

- KR: profile README + this HQ + architecture / OKR / RFC docs
- KR: public issues for the four scored targets

Detail: [docs/okrs.md](docs/okrs.md)

---

## Prioritization

SovereignEvolution scores candidates. The current board:

| ID | Title | Score | State |
| --- | --- | --- | --- |
| `test-foundation` | Real unit tests across Helix, MFR, Aether | 6480 | queued |
| `shared-contracts` | Shared event and decision schemas | 5040 | queued |
| `cross-project-flow` | Helix → MFR → Aether | 3888 | queued |
| `baseline-learning` | Long-term baseline in HelixMind | 2744 | **next** |

The engine rotated the "next" pointer across these four. None have been executed as code yet. That is recorded here without theatre.

---

## Delivery

| Loop | When | What it writes |
| --- | --- | --- |
| Runtime | every 2 hours | state, reports, signatures |
| Evolution | daily 03:00 UTC | memory, status, daily report |
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
- Report vulnerabilities privately; see [SECURITY.md](SECURITY.md).

---

## Incidents

| Signal | Warning | Critical |
| --- | --- | --- |
| CPU | > 70% | > 85% |
| Memory | > 80% | > 90% |
| Disk | — | > 92% |

AetherMind maps state to `observe` · `monitor_closely` · `investigate_immediately` · `continue_normal_operations`.

HelixMind additionally flags correlated multi-signal pressure.

---

## Strategy

FathiMind is a **human-centric neural extension**, not a chatbot wrapper and not a bookmark wiki.

Direction:

- Keep the four layers distinct
- Make them interoperate through contracts
- Prefer evidence over rhetoric
- Let evolution pick the next honest gap
- Refuse ornamental commits

---

## Roadmap

See [Prioritization](#prioritization). Issues will track the four targets in this repository.

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
- [Contributing](CONTRIBUTING.md)
- [Security](SECURITY.md)

---

**Owner:** Mohamed Fathi Alrahman · [profile](https://github.com/mfathialrahman-crypto)
