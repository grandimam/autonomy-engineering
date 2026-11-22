# Patterns

A pattern captures a reusable engineering solution independent of a specific agent framework.

Each pattern should document its problem, prerequisites, mechanism, invariants, tradeoffs, failure modes, and a worked example with tests. Link to the concept it supports, the implementation that demonstrates it, and missions that use it.

## Candidate patterns

| Pattern | Problem addressed |
| --- | --- |
| Event-to-task conversion | Turn signals into deduplicated durable work |
| Workflow state machines | Enforce valid, inspectable task transitions |
| Lease-based dispatch and fencing | Recover abandoned work and reject stale workers |
| Resumable execution | Continue after interruptions without losing progress |
| Idempotent external effects | Avoid duplicate consequential actions on retry |
| Evaluation gates | Require evidence before accepting an outcome |
| Event subscriptions | Resume waiting work without missing early events |
| Feedback-driven scheduling | Convert observations into new work |
| Human approval gates | Bound authority and preserve accountability |

**Status:** These are candidates, not finished pattern guides and not claims about any particular published system. The [Performance Factory reconstruction](../case-studies/openai-performance-factory/reconstruction.md) provides an initial design for testing several of them.
