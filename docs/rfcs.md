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

- **Status:** implemented (schemas created 2026-09-26)
- **Layer:** contract
- **Summary:** Freeze Event, Decision, Recommendation, Target objects as versioned JSON schemas.
- **Motivation:** SovereignEvolution listed `shared-contracts` at high score. Without schemas, cross-project flow couples implementations.
- **Proposal:** Implemented. Files live in this repository:
  - `schemas/event.schema.json`
  - `schemas/decision.schema.json`
  - `schemas/recommendation.schema.json`
  - `schemas/target.schema.json`
- **Next step:** Runtimes continue optional validation on write. Validation remains non-blocking.
- **Risks:** Existing JSON fields vary slightly. Schemas allow additive fields (`additionalProperties: true`).
- **Rollback:** Keep writing current JSON; validation stays optional.

## RFC-0002 — Helix → MFR → Aether data flow

- **Status:** implemented
- **Depends:** RFC-0001
- **Layer:** aether
- **Summary:** AetherMind may load sibling envelopes (`helix_insights.json` / related) when present and treat them as evidence.
- **Motivation:** AetherMind should consume verified outputs from other layers instead of only re-collecting host metrics.
- **Proposal:** Optional sibling envelope ingest. Missing files → current behaviour. Confidence increases when independent layers agree.
- **Risks:** Stale files. Reject evidence older than two runtime cycles.
- **Rollback:** Ignore optional paths.

## Completed targets (SovereignEvolution)

shared-contracts, baseline-learning, cross-project-flow, live-envelope-ingest, project-factory.

Further RFCs require a new scored target from the evolution engine.
