# Contributing

Build this repository around systems with inspectable evidence. One well-supported case study is more useful than many empty directories.

## Case studies

Use `case-studies/<system-name>/` and include:

| File | What belongs here |
| --- | --- |
| `README.md` | Scope, status, and a reading path |
| `architecture.md` | Source-backed views and unresolved technical questions |
| `reconstruction.md` | An explicitly proposed design, with assumptions |
| `tradeoffs.md` | Analysis of choices and their consequences |
| `references.md` | Primary references and links to local evidence |
| `source/` | Metadata, a concise summary, and asset provenance |
| `diagrams/` | Attributed source visuals and clearly labeled original diagrams |

Distinguish facts stated by a source, inferences supported by evidence, and implementation choices made for an example. Do not turn a proposed mechanism into a claim about the source system.

## Source capture

Record the canonical URL, publisher, authors, publication date, capture date, acquisition method, and limitations. Give every saved visual a source URL, local path, media type, and SHA-256 digest in a manifest.

Use meaningful filenames and file extensions that match the actual media type. Keep original figures separate from browser screenshots and redraws. For dynamic content, identify whether an artifact preserves the animation or only one frame.

Link to full articles unless there is a basis for including their text. Attribute third-party material and document its rights separately from the repository license. Do not store authentication data, browser profiles, or unrelated page assets.

## Concepts, patterns, and code

Create concept and pattern pages as their explanations become useful across studies. A pattern should state the problem, assumptions, mechanism, failure cases, and evidence for using it.

An implementation should have reproducible setup instructions, a runnable example, and checks for meaningful failure modes. Label simulations and fake agents clearly. Do not create a package manifest that implies an implementation exists before it does.

Before submitting, check local links, inspect diagrams, verify manifest digests, and run the checks relevant to any changed code.
