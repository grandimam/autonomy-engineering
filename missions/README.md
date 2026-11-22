# Missions

Missions demonstrate how independently understood autonomy mechanisms combine to pursue a real objective over time.

A mission is **not** a single prompt, a one-shot agent demo, or merely a workflow diagram. It has a defined objective, inputs or triggers, durable work, bounded execution, evaluation, feedback, and explicit human authority.

## Mission catalog

| Mission | Objective | Status |
| --- | --- | --- |
| [Discover and build](discover-and-build/README.md) | Discover software opportunities, build original alternatives, and evaluate outcomes | Proposed; not implemented |

## What each mission must document

- **Objective and scope:** What outcome is sought, and what is explicitly out of scope?
- **Trigger and inputs:** What starts or resumes the mission, and where does evidence come from?
- **Workflow and state:** What durable records and transitions coordinate work?
- **Execution and authority:** What can agents do independently, and what requires approval?
- **Evaluation:** What observable evidence indicates success or failure?
- **Feedback:** How do observations generate the next task or change priorities?
- **Reliability:** How are retries, duplicates, outages, and uncertain external effects handled?
- **Results:** Which parts are simulated, implemented, deployed, or empirically validated?

Keep substantial product implementations in their own repositories. Link back to the reusable concepts, patterns, and experiments that explain how the mission works. Never label a proposed mission as operational.
