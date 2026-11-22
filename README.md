<p align="center"><sub>AN OPEN FIELD GUIDE TO BUILDING AUTONOMOUS SYSTEMS</sub></p>

<h1 align="center">Autonomy Engineering</h1>

<p align="center"><strong>Understand the mechanism. Build it yourself. Break it deliberately. Prove it recovers.</strong><br/>Engineering explanations, real-world architecture studies, runnable experiments, and end-to-end missions.</p>

<p align="center"><a href="#start-here">Start here</a> · <a href="#the-learning-path">Learning path</a> · <a href="#missions">Missions</a> · <a href="CONTRIBUTING.md">Contribute</a></p>

---

## Beyond the agent loop

A successful agent demo is not the same as an autonomous system. Systems that pursue objectives over time must decide what work matters, persist progress, coordinate execution, evaluate outcomes, recover from failure, and know when a human must intervene.

**Autonomy engineering** is the engineering discipline of building systems that can pursue objectives over time, make decisions, execute actions, evaluate outcomes, and recover from failures with bounded human intervention.

This is **not an awesome list** or a directory of agent frameworks. It is an open, implementation-oriented field guide. We study mechanisms independently of products and vendors, reconstruct them in small programs, test their failure modes, and combine them into useful autonomous operations.

> The standard: don't just explain how an autonomous system works. Build the smallest version that proves the mechanism, break it deliberately, and demonstrate how it recovers.

## Start here

### 01 / OpenAI Performance Factory

Our first [case study](case-studies/openai-performance-factory/README.md) investigates the [published Performance Factory architecture](https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/): event-driven work, configurable workflows, persistent tasks, dispatch, and verification.

[Read the case study](case-studies/openai-performance-factory/README.md) · [Architecture questions](case-studies/openai-performance-factory/architecture.md) · [Reconstruction proposal](case-studies/openai-performance-factory/reconstruction.md) · [Tradeoffs](case-studies/openai-performance-factory/tradeoffs.md)

![OpenAI's published Performance Factory architecture](case-studies/openai-performance-factory/diagrams/orchestrator-architecture.webp)

<sub>Original figure: OpenAI. [Source and attribution](case-studies/openai-performance-factory/source/README.md).</sub>

**Current status:** one evidence-backed case study and a design proposal. No runnable reconstruction has been published yet. Proposed mechanisms are teaching designs, not claims about OpenAI's private implementation.

## The learning path

Each area asks four questions: **What is it? Why does it exist? How can I build it? How do I prove it works?**

| Capability | What you learn to engineer |
| --- | --- |
| 01. Objectives & planning | Translate desired outcomes into actionable work |
| 02. Events & triggers | Decide when work starts, resumes, or repeats |
| 03. Tasks & workflows | Persist work and enforce valid transitions |
| 04. Execution & runtimes | Execute agents and tools with bounded authority |
| 05. State & memory | Preserve execution history and relevant context |
| 06. Verification & evaluation | Establish whether the intended outcome was achieved |
| 07. Feedback & adaptation | Turn observed results into subsequent work |
| 08. Reliability & recovery | Survive crashes, retries, duplicates, and partial failures |
| 09. Human oversight | Escalate uncertainty and require approvals when necessary |
| 10. Autonomous operations | Assemble the capabilities into ongoing systems |

This is a [curriculum outline](concepts/README.md), **not** a claim that all chapters are complete. We publish substantive explanations and working examples incrementally.

## How a topic becomes an engineering capability

**Concept → Pattern → Implementation → Experiment → Application**

For example, *durable task dispatch*:

1. **Concept:** Why must work survive independently of the agent processing it?
2. **Pattern:** State machines, task claims, leases, fencing tokens, and idempotency.
3. **Implementation:** A small persistent dispatcher built with Python and SQLite.
4. **Experiment:** Kill the worker, replay an event, expire a lease, and reject a stale result.
5. **Application:** Use the dispatcher in a recurring autonomous mission.

Examples should remain understandable without adopting a particular agent framework. Code must distinguish deterministic simulations from live integrations.

## Explore the repository

| Section | Purpose | Current state |
| --- | --- | --- |
| [Concepts](concepts/README.md) | Understand foundational ideas | Curriculum outlined |
| [Patterns](patterns/README.md) | Reuse mechanisms across systems | Candidates outlined |
| [Case studies](case-studies/README.md) | Investigate real systems and their evidence | First study published |
| [Implementations](implementations/README.md) | Run and test the mechanisms | First implementation planned |
| [Missions](missions/README.md) | Combine capabilities to pursue real objectives | First mission proposed |
| [Resources](resources/README.md) | Inspect primary sources and provenance | First source indexed |

## Missions

A **mission** is an end-to-end autonomous operation that combines triggers, decisions, execution, evaluation, feedback, and human oversight around an objective.

Our [first proposed mission](missions/discover-and-build/README.md) is to monitor software discovery sources, identify interesting opportunities, investigate products, build original alternatives, and evaluate whether they provide value. This is a proposed design, **not** an operating autonomous product factory.

Missions are where the handbook's mechanisms become practical. Full products belong in their own repositories; this repository documents the reusable autonomy mechanisms and evidence from their use.

## First implementation milestone

The first vertical slice will extend the Performance Factory reconstruction:

1. Ingest an event without creating duplicate logical work.
2. Create a durable task using a versioned workflow definition.
3. Claim and dispatch the task; recover after a process crash.
4. Validate proposed state transitions and reject stale workers.
5. Evaluate an outcome and generate follow-up work when appropriate.
6. Run the full loop locally with reproducible fault-injection tests.

[Read the implementation plan](implementations/README.md). Until code and tests are published, this is a roadmap rather than a completed capability.

## How this relates to Grandimam and Jove

**Autonomy Engineering is the knowledge layer:** a tool-agnostic field guide to understanding and building reliable autonomous systems.

**Jove is a potential implementation layer:** an autonomous execution system that can apply these ideas. The handbook should remain useful without Jove.

**Grandimam is the application and public content layer:** experiments, original products, and documented attempts to independently build alternatives to venture-backed software. The aim is to demonstrate outcomes, not merely generate code.

An investigation can become a written explanation, a runnable experiment, a technical video, and ultimately a component in a real product. Technical claims should remain evidence-based, and business outcomes should be measured rather than assumed.

## How we study systems

1. **Observe:** Start with primary sources and record provenance.
2. **Explain:** Separate published facts, supported inferences, and open questions.
3. **Reconstruct:** Implement the smallest mechanism that exposes the important decisions.
4. **Challenge:** Test duplicates, crashes, stale results, partial failures, and invalid transitions.
5. **Apply:** Integrate proven capabilities into an end-to-end mission.
6. **Evaluate:** Report what worked, what failed, and what remains uncertain.

## Contributing

We value primary-source investigations, precise explanations, minimal working implementations, fault-injection tests, and reproducible mission reports. A well-supported mechanism is worth more than a long list of links.

See [CONTRIBUTING.md](CONTRIBUTING.md) for evidence standards and contribution requirements.

---

<p align="center"><strong>Read deeply. Build carefully. Make the mechanisms visible.</strong><br/><sub>Original contributions: <a href="LICENSE">MIT</a></sub></p>
