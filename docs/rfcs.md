# RFCs

Request for comments. Write here before changing a contract or a cross-repo flow.

## Template

```
RFC: <number> — <title>
Status: draft | accepted | implemented | rejected
Layer: helix | mfr | aether | sovereign | contract
Summary:
Motivation:
Proposal:
Risks:
Rollback:
```

## RFC-0001 — Shared event and decision schemas

- **Status:** draft
- **Layer:** contract
- **Summary:** Freeze Event, Decision, Recommendation, Target objects (see architecture.md) as versioned JSON schemas.
- **Motivation:** SovereignEvolution lists `shared-contracts` at score 5040. Without schemas, cross-project flow will couple implementations.
- **Proposal:** `schemas/event.schema.json`, `decision.schema.json`, `recommendation.schema.json`, `target.schema.json` in this repository. Runtimes validate on write.
- **Risks:** Existing JSON fields vary slightly (signature length, extra keys). Schema must allow additive fields.
- **Rollback:** Keep writing current JSON; validation optional behind a flag.

## RFC-0002 — Helix → MFR → Aether data flow

- **Status:** draft
- **Depends:** RFC-0001
- **Layer:** aether
- **Summary:** AetherMind may load `helix_insights.json` and `decisions.json` when present, and treat them as evidence instead of only live `psutil` samples.
- **Motivation:** AetherMind currently re-collects host metrics. It does not yet consume the other layers.
- **Proposal:** Optional paths via env. Missing files → current behaviour. Confidence increases when independent layers agree.
- **Risks:** Stale files. Reject evidence older than two runtime cycles.
- **Rollback:** Ignore optional paths.

## Open

Further RFCs require `test-foundation` and `baseline-learning` once RFC-0001 is accepted.
