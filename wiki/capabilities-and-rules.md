# Capabilities and Rules

**Summary**: The third artifact in the [[question-chain]], covering Q7–Q8: what the product must be able to do and the non-negotiable business rules it must follow.

**Sources**: raw/question-chain-v2.md

**Last updated**: 2026-04-18

---

**Owner:** PM-B + EM + PM-A

## Q7: What must this product be able to do?

Each capability is a thing the product does, stated without specifying how — e.g. "calculate settlement amounts," "notify users when reconciliation fails," "generate audit reports."

**Traceability rule:** Every capability must trace back to a step in a user journey from Q6 ([[user-journeys]]). If a capability doesn't trace back, question whether it's needed.

Answer format: a list of capabilities.

## Q8: What are the business rules this product must follow?

These are rules of the business, not rules of the software. The test: would this rule still be true if everything were done on paper and spreadsheets? If yes, it belongs here.

Rules are numbered (BR-01, BR-02, etc.) so they can be referenced in stories and technical decisions later.

Answer format: a numbered list of non-negotiable rules.

## Related pages

- [[question-chain]]
- [[user-journeys]]
- [[system-map]]
