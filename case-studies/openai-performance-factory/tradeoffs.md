# Reconstruction tradeoffs

This analysis applies to the [proposed local implementation](reconstruction.md). It does not assert which technologies or protocols OpenAI uses.

| Choice | Benefit | Cost or failure risk | How to assess it |
| --- | --- | --- | --- |
| One database for tasks and events | Scheduling decisions can share a transaction. | Write contention can limit concurrency. | Measure claim latency as competing workers increase. |
| Expiring ownership | Abandoned work becomes recoverable. | A slow worker can overlap with its replacement. | Delay one worker past expiry and reject its stale result. |
| Short database transactions | Workers do not hold locks while executing. | Completion requires conflict detection. | Race two updates against the same revision. |
| Recorded events with cursors | Early events can be reconsidered when a wait is created. | Retention and cursor semantics become part of correctness. | Replay events around the wait-registration boundary. |
| Workflow version pinning | Existing tasks keep stable rules. | Old definitions need retention or explicit migration. | Resume an old task after installing a new definition. |
| Finite retry budgets | Failures cannot retry indefinitely. | Some transient failures need manual resumption. | Verify the stopped state preserves enough evidence to continue. |

## Keep scheduling and side effects separate

The difficult boundary in this proposal is a remote action whose result is unknown after a process failure. For example, a request might succeed remotely just before the local process stops recording its response. Repeating the request blindly is unsafe for correctness, even if local task updates are perfectly serialized.

Give each logical action a durable identifier before attempting it. Prefer a remote API that accepts that identifier, or reconcile the remote resource before retrying. If neither is possible, expose the uncertain outcome instead of claiming exactly-once execution.

## Add complexity in response to evidence

Start with the single-database simulation. Add a dedicated queue when measured scheduling load warrants it, and then test the new dual-write boundary. Add a real model only after the coordinator can reject invalid outputs and enforce budgets. This progression makes each new failure mode visible and keeps the example small enough to understand.
