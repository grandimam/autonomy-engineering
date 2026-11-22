# Mission 001 — Discover and build

**Status: proposed.** This is an illustrative end-to-end mission, not a deployed autonomous product factory.

## Objective

Continuously discover promising software problems, research existing products, propose an original alternative, build a bounded implementation, and evaluate whether it provides value.

This mission is one possible bridge from autonomy engineering to the wider Grandimam ambition of independently building alternatives to venture-backed software. It is **not** an instruction to reproduce proprietary code, copy protected assets, or misrepresent affiliation.

## Proposed loop

1. **Observe:** Periodically ingest public product launches, Hacker News discussions, and other permitted sources.
2. **Discover:** Extract recurring problems, user needs, and possible product opportunities, retaining source evidence.
3. **Decide:** Rank opportunities against explicit criteria. Request human approval before committing to a product direction.
4. **Build:** Create a scoped specification, implementation tasks, tests, and a deployable original prototype.
5. **Evaluate:** Test functional quality and gather actual user or market feedback when available.
6. **Learn:** Persist outcomes and generate follow-up tasks or new investigations.

## Engineering capabilities required

| Capability | Responsibility |
| --- | --- |
| Triggers | Schedule discovery and react to new evidence |
| Task workflows | Persist research, approval, implementation, and evaluation work |
| Execution | Run bounded research and engineering tasks |
| State and memory | Retain sources, decisions, artifacts, and results |
| Evaluation | Distinguish working code from useful outcomes |
| Feedback | Convert findings into explicit next actions |
| Reliability | Resume after failures without duplicating consequential effects |
| Oversight | Require approval for scope, spending, publication, and deployment |

## Proposed first vertical slice

Start small: poll a permitted public feed, deduplicate new items, create research tasks, generate evidence-backed opportunity briefs, and present them for human review. Do **not** begin with autonomous production deployment or purchases.

### Acceptance criteria for the first slice

- Replaying the same item does not create duplicate research tasks.
- A restart preserves pending work and source references.
- Every opportunity brief links to its supporting evidence.
- Failed work can be retried within a bounded policy.
- No product build or external publication occurs without the configured approval.

## What success means

The system must produce decisions and artifacts that can be independently inspected. A generated repository is not proof of product value. Track implementation quality, operating cost, research accuracy, deployment status, and evidence of actual user usefulness separately.

Future reports should distinguish proposed behavior, local simulation, working integration, and observed production results.
