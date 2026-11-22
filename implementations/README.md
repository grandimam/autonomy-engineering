# Implementations

Implementations make the handbook executable: small programs that expose one mechanism clearly and test how it behaves under failure.

**Current status:** No runnable implementation has been published yet.

## First milestone: minimal autonomous coordinator

Build on the [Performance Factory reconstruction proposal](../case-studies/openai-performance-factory/reconstruction.md), starting with a single process, SQLite, deterministic workers, and an injected clock. Do not require an LLM, external queue, or cloud account to understand the initial example.

Planned stages:

1. **Event ingestion:** Deduplicate events and create intended work once.
2. **Workflow transitions:** Persist task state and reject invalid changes.
3. **Durable dispatch:** Claim tasks with leases and fencing tokens.
4. **Agent boundary:** Accept worker proposals only after coordinator validation.
5. **Evaluation and feedback:** Record outcomes and create justified follow-up work.
6. **End-to-end test:** Restart the process mid-flight and demonstrate recovery.

## Definition of done

An implementation must have a runnable README, pinned or declared dependencies, executable code, automated checks, and repeatable failure demonstrations. Show duplicate delivery, worker crashes, stale results, invalid transitions, and retry exhaustion where applicable. Distinguish simulated behavior from real integrations and document known limitations.

The first proposed directory is `minimal-factory/`; it should be added only when real code exists.

The longer-term application is a [mission](../missions/README.md), not a claim that the toy coordinator is production-ready.
