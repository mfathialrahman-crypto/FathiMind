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

- **Status:** accepted (schemas created 2026-09-26)
- **Layer:** contract
- **Summary:** Freeze Event, Decision, Recommendation, Target objects as versioned JSON schemas.
- **Motivation:** SovereignEvolution listed `shared-contracts` at score 5040. Without schemas, cross-project flow couples implementations.
- **Proposal:** Implemented. Files now live in this repository:
  - `schemas/event.schema.json`
  - `schemas/decision.schema.json`
  - `schemas/recommendation.schema.json`
  - `schemas/target.schema.json`
- **Next step:** Runtimes (Helix, MFR, Aether, Sovereign) should begin optional validation on write. Validation remains non-blocking until confidence is high.
- **Risks:** Existing JSON fields vary slightly. Schemas allow additive fields (`additionalProperties: true`).
- **Rollback:** Keep writing current JSON; validation stays optional behind a flag.

## RFC-0002 — Helix → MFR → Aether data flow

- **Status:** draft
- **Depends:** RFC-0001 (now accepted)
- **Layer:** aether
- **Summary:** AetherMind may load `helix_insights.json` and `decisions.json` when present, and treat them as evidence instead of only live `psutil` samples.
- **Motivation:** AetherMind currently re-collects host metrics. It does not yet consume the other layers.
- **Proposal:** Optional paths via env. Missing files → current behaviour. Confidence increases when independent layers agree.
- **Risks:** Stale files. Reject evidence older than two runtime cycles.
- **Rollback:** Ignore optional paths.

## Open

Further RFCs require baseline-learning and Project Factory once RFC-0002 is accepted.
