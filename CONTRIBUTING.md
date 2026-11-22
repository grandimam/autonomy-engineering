# Contributing

This is an implementation-oriented field guide, **not** an awesome list. Contributions should help readers understand, build, test, or apply an autonomous-system mechanism.

## Editorial standard

A substantive engineering topic should answer:

1. What is the mechanism?
2. Why is it needed, and under what assumptions?
3. How can someone implement the smallest useful version?
4. What invariants and failure experiments establish correctness?
5. Where can the mechanism be applied in an end-to-end mission?

Prefer one well-supported, tested explanation over many empty headings or tool links.

## Case studies

Use `case-studies/<system-name>/` with a scoped README, source-backed architecture notes, reconstruction assumptions, tradeoffs, references, and attributed diagrams when appropriate. Separate **published facts**, **supported inference**, and **our proposed implementation**. Never imply access to private internals.

## Source capture

Record the canonical URL, publisher, author, publication and capture dates, acquisition method, and limitations. Attribute preserved visuals, record their provenance and hashes, and distinguish original figures from screenshots or redraws. Link to full articles unless inclusion is permitted. Do not include secrets, authentication data, or unrelated assets.

## Concepts and patterns

Concepts explain foundational ideas independently of vendors. Patterns document a recurring problem, prerequisites, mechanics, invariants, failure cases, tradeoffs, and worked examples. Cross-link related concepts, case studies, implementations, and missions.

## Implementations

Include reproducible setup instructions, executable source, meaningful tests, and deliberate failure experiments. Label deterministic simulations, mocks, and real integrations. Do not publish an empty package or claim that design-only work is runnable.

## Missions

A mission must state its objective, trigger, durable workflow, execution permissions, evaluation criteria, feedback mechanism, recovery policy, and human approval points. Distinguish proposed, simulated, locally working, and deployed behavior. Report outcomes with evidence rather than assuming that generated software is useful.

## Review checklist

- Sources and claims are correctly attributed.
- Local links work; diagrams and manifests are verified.
- Proposed designs are not represented as facts about third-party systems.
- Code runs as documented and failure tests are reproducible.
- External actions are bounded and appropriate approvals are explicit.
- Status labels reflect what actually exists.
