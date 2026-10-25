> **PROPRIETARY — ALL RIGHTS RESERVED.** © 2026 Mohamed Fathi Alrahman. Not open source. Not MIT. The engines are private. Viewing is not a license.
>
> Press & trade: [PRESS.md](./PRESS.md)

# FathiMind

**Human-centric cognitive engineering operating system.**

[![Status](https://img.shields.io/badge/Ecosystem-Live-brightgreen)](https://github.com/mfathialrahman-crypto)
[![Public Core](https://img.shields.io/badge/Public%20Core-MIT%20v2.1.30--pro-orange)](https://github.com/mfathialrahman-crypto/MFR-Adaptive-Intelligence-Core-Pro)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)

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

## Live Ecosystem (2026-10-25)

| Repository | Layer | Version | Cadence |
| --- | --- | --- | --- |
| [HelixMind](https://github.com/mfathialrahman-crypto/HelixMind) | Telemetry and anomaly intelligence | v1.2 | every 2 hours |
| [MFR-Cognition](https://github.com/mfathialrahman-crypto/MFR-Cognition) | Cognitive core | v4.2.254 | every 2 hours |
| [AetherMind](https://github.com/mfathialrahman-crypto/AetherMind) | Intelligence / reasoning | v1.3 | every 2 hours |
| [SovereignEvolution](https://github.com/mfathialrahman-crypto/SovereignEvolution) | Permanent evolution engine | v1.44 | daily 03:00 UTC |
| [MFR Adaptive Intelligence Core Pro](https://github.com/mfathialrahman-crypto/MFR-Adaptive-Intelligence-Core-Pro) | **Public** transparent analysis | v2.1.30-pro | continuous |

Current heads: HelixMind v1.2 with long-window baseline; MFR-Cognition v4.2.254 with expanded host metrics (uptime, battery, CPU freq, temperatures, I/O), hardened redaction and decision traces; AetherMind v1.3 with optional sibling envelope ingest; SovereignEvolution v1.44 with completed targets. Shared schemas (RFC-0001) under `schemas/`. Public Core Pro at v2.1.30-pro (expanded unit tests for decision contract mapping covering insufficient/conflicting/low-confidence paths; CLI --version and --validate flags; pure-Python validate_report() contract checker; all analysis outputs satisfy analysis.schema.json; insufficient-evidence reports include fingerprint and question; public docs aligned to version.py SSOT).

---

## The rank above a reading list

[charlax/engineering-management](https://github.com/charlax/engineering-management) is a high-quality curated index. It does not produce a decision, attach evidence or confidence, measure a running system, or write an audit trail.

**FathiMind does.** That is a higher category.

Stars measure how many people bookmarked a topic.  
**Traces measure whether a system worked this morning.**

---

## Architecture

Layers are separated on purpose.

1. **Measure** — HelixMind collects CPU, memory, disk, load, processes. Three detection layers. Explainable health score. Long-window baseline with capped penalties.
2. **Verify** — MFR-Cognition turns metrics into a decision object: input, evidence, anomalies, confidence, status. Hardened redaction, atomic writes, locks.
3. **Reason** — AetherMind forms hypotheses and emits a recommendation **only as strong as the confidence**. Optionally consumes local Helix and redacted MFR envelopes.
4. **Evolve** — SovereignEvolution scans the ecosystem, records gaps, and selects the next development target. It does not invent fake diffs.

Shared rule: **no tight coupling**. Cross-layer flow is a contract.

Full diagram: [docs/architecture.md](docs/architecture.md)  
Schemas: [`schemas/`](./schemas/).

---

## Doctrine

1. No strong recommendation at low confidence.
2. No fake changes.
3. Every decision is a trace.
4. Layers stay separate.
5. Public transparency where it strengthens trust; private engines where it protects the system.
6. Continuous daily evolution.

---

## Quality

Quality is HelixMind's health model plus the evolution rule:

> Only real, high-value, safe changes are executed. Artificial changes are forbidden.

Shipped:
- Unit tests on HelixMind, MFR-Cognition, and AetherMind. Red suite blocks the 2-hour cycle.
- Shared JSON schemas (RFC-0001).
- Cross-project flow via local sibling envelopes.
- Long-term baseline learning.
- Project Factory as record-only local board.

---

## Public Surface

The only fully open component is **[MFR Adaptive Intelligence Core Pro](https://github.com/mfathialrahman-crypto/MFR-Adaptive-Intelligence-Core-Pro)** (MIT).  
Everything else remains proprietary to protect the living system.

---

## Serve Gate

Private skill `auto-serve`. A result is served only when evidence is present, fresh, and confidence clears the floor (0.45). A calm serve needs 0.70. The skill never mutates an engine.

---

## How to run (private engines)

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
- [Changelog](CHANGELOG.md)
- [Contributing](CONTRIBUTING.md)
- [Security](SECURITY.md)
- [AGENTS.md](AGENTS.md) — Project Engineering Constitution

---

**Owner:** Mohamed Fathi Alrahman · [profile](https://github.com/mfathialrahman-crypto)
