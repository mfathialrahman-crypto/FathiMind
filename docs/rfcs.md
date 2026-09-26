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

- **Status:** implemented (2026-09-26)
- **Depends:** RFC-0001 (accepted)
- **Layer:** aether
- **Summary:** AetherMind may load `helix_insights.json` and `decisions.json` when present, and treat them as evidence instead of only live `psutil` samples.
- **Motivation:** AetherMind previously re-collected host metrics. It did not consume the other layers.
- **Proposal:** Implemented in AetherMind:
  - Env `HELIX_INSIGHTS_PATH` and `MFR_DECISIONS_PATH`.
  - Missing / unreadable files → live-psutil behaviour unchanged.
  - Evidence older than two runtime cycles (4 hours) is rejected.
  - Independent agreement raises confidence. It does not change the action.
  - Disagreement is a hypothesis (`possible host mismatch`), not an escalation.
  - GitHub Actions optionally fetches sibling traces. Private repos need `FATHIMIND_INGEST_TOKEN`.
- **Risks:** Stale files; Actions `GITHUB_TOKEN` cannot read sibling private repos without a PAT.
- **Rollback:** Unset the env vars. `reason()` is unchanged.

## Open

Further RFCs require baseline-learning and Project Factory.
