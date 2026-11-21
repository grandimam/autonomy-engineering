# Reconstruction proposal

**Status: design only.** This is an original proposal for a small teaching system. It is not OpenAI source code or a verified reproduction of its internals. The [published evidence](source/README.md) motivates the case study; the mechanisms below are choices for a possible local implementation.

## Start with a deterministic simulation

Use a single process, a SQLite database, a command-line interface, and a fake worker that returns predetermined results. This makes failure behavior inspectable before adding model calls, a queue, or external integrations. Do not create real pull requests or perform deployments in the first example.

Build around a small set of durable records:

| Record | Suggested fields | Invariant |
| --- | --- | --- |
| Task | ID, workflow version, state, revision, ready time | Each accepted update advances the revision. |
| Attempt | ID, task ID, ownership token, expiry, result | Only the current owner may commit a result. |
| Event | Source, external ID, resource key, occurrence time, receipt time | The source and external ID form a unique pair. |
| Wait | Task ID, event filter, starting cursor, status | A recorded matching event can satisfy the wait. |
| Effect | Task ID, logical action ID, status, external reference | Retries reuse the same logical action identity. |

## Proposed execution protocol

1. Ingest a simulated input into the event table. Enforce uniqueness before scheduling work.
2. Claim one eligible task in a short transaction. Record its attempt and ownership token, then release the database transaction before doing work.
3. Give the fake worker a snapshot containing the task revision and permitted outputs. Treat its response as a proposal to the coordinator.
4. Validate the proposed transition against the pinned workflow definition. Commit only if the task revision and ownership token still match.
5. Register a wait and its event cursor in the same transaction as the task update. Check already-recorded events before sleeping, so an early event remains discoverable.
6. When an event satisfies a wait, consume the wait and make the task eligible atomically. Repeated deliveries must not create additional attempts for the same transition.
7. If an attempt expires, allow a replacement attempt with a new token. Reject any later result submitted under the old token.

These rules protect database state. They do not make an external API call transactional. A later integration would need an outbox, a stable idempotency key where supported, and reconciliation when a remote result is uncertain.

## Failure scenarios to demonstrate

| Scenario | Expected result |
| --- | --- |
| The same input arrives twice | One logical event and one intended scheduling effect. |
| The process stops after claiming work | The task can become eligible again after expiry. |
| An expired worker returns after its replacement | The stale result is rejected. |
| A matching event arrives just before wait registration | The stored event satisfies the new wait. |
| A worker proposes an invalid transition | The task remains unchanged and the attempt records the rejection. |
| A task repeatedly fails | A finite retry budget leads to an explicit stopped state. |

Use an injected clock for expiry checks and an explicit fault-injection point around each commit. The purpose of these checks is to demonstrate durable coordination under failure, not merely confirm that the successful path works.

## Completion criteria for a future implementation

A reader should be able to create a task, inspect its history, interrupt execution, restart it, and observe a correct terminal outcome using only local fixtures. Include setup instructions and the failure demonstrations above before calling it a runnable implementation. Track that work under [implementations](../../implementations/README.md).
