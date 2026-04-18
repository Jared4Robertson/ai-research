# Question Chain

**Summary**: A 10-question sequence that walks a product team from initial idea to well-defined epics, stories, and tasks across four structured artifacts.

**Sources**: raw/question-chain-v2.md

**Last updated**: 2026-04-18

---

The Question Chain is a lightweight product definition methodology. Each question has a clear expected answer format, and each answer feeds the next. The goal is alignment before work begins — catching disagreements at the question level rather than the sprint level.

## The four artifacts

| Artifact | Questions | Owner |
|---|---|---|
| [[product-brief]] | Q1–Q3 | PM-A with Product Director |
| [[user-journeys]] | Q4–Q6 | PM-B with EM |
| [[capabilities-and-rules]] | Q7–Q8 | PM-B + EM + PM-A |
| [[system-map]] | Q9–Q10 | EM with Senior Engineers |

## Design principles

- **One-sentence test (Q1):** If different people give different answers to "what are we building and why?", that's a red flag before a line of code is written.
- **Traceability:** Every capability (Q7) must trace back to a step in a user journey (Q6). If it doesn't, question whether it's needed.
- **Business rules vs. software rules (Q8):** A business rule is still true even if everything is done on paper. This keeps BR-## entries stable across implementation changes.
- **Boundary-first thinking (Q9):** What's explicitly *not* part of the system is as important as what is.

## Related pages

- [[product-brief]]
- [[user-journeys]]
- [[capabilities-and-rules]]
- [[system-map]]
