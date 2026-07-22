# Milestones

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ../ENGINEERING_CONSTITUTION.md, ../ROADMAP.md
Related Documents: ../MASTER_PRD.md, ../FEATURE_MATRIX.md, ../ARCHITECTURE.md
Next Expansion: Flesh out milestones M04-M50 with full task breakdowns as each phase begins.
Last Updated: 2026-07-23
```

This directory holds the milestone specifications for Dhee_AI. Milestones are dependency-ordered
units of delivery derived from [`../ROADMAP.md`](../ROADMAP.md). Each milestone is only complete
when it satisfies the Definition of Done in
[`../ENGINEERING_CONSTITUTION.md`](../ENGINEERING_CONSTITUTION.md).

`MILESTONE_01`-`MILESTONE_03` are fleshed out as worked examples; `MILESTONE_04`-`MILESTONE_50`
are scaffolded and expanded per the Execution Policy (their `Status` is `Draft`).

## Index
See [`../ROADMAP.md`](../ROADMAP.md) for the phase-to-milestone map and full titles. Files:
`MILESTONE_01.md` through `MILESTONE_50.md`.

## Milestone template

```md
# MILESTONE_NN: Title

​```
Status: Draft | In Review | Stable
Priority: High | Medium | Low
Owner: Repository Maintainer
Depends On: MILESTONE_(NN-1)
Related Documents:
Next Expansion:
Last Updated: YYYY-MM-DD
​```

## Phase
Which roadmap phase this milestone belongs to.

## Goal
One or two sentences describing the outcome.

## Scope
What is included in this milestone.

## Deliverables
- Concrete artifacts (packages, endpoints, UI, docs, tests).

## Acceptance criteria
- Verifiable conditions, aligned with the Definition of Done.

## Dependencies
- Preceding milestones and specifications required.

## Risks & mitigations
- Known risks and how they are addressed.
```

## Rules
- Milestones must reference the specifications they implement; they never introduce behavior not
  present in the specification (Living Specification Rule).
- Update [`../ROADMAP.md`](../ROADMAP.md) and [`../FEATURE_MATRIX.md`](../FEATURE_MATRIX.md) when
  milestone scope or sequencing changes.
