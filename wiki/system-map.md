# System Map

**Summary**: The fourth artifact in the [[question-chain]], covering Q9–Q10: what is inside vs. outside the system, and how internal pieces relate to each other.

**Sources**: raw/question-chain-v2.md

**Last updated**: 2026-04-18

---

**Owner:** EM with Senior Engineers

## Q9: What is inside this system and what is outside?

Define the system boundary:
- What does this product own vs. get from other systems?
- Where are the integration points — what data comes in, what goes out, and to/from where?
- What is explicitly *not* part of this system, even if related?

Naming what's out-of-scope is as important as naming what's in scope.

Answer format: a list of what's in, what's out, and where the edges are.

## Q10: How do the pieces inside this system relate to each other?

- What are the major modules or services inside the product?
- Which module owns which capabilities from Q7 ([[capabilities-and-rules]])?
- How do they communicate — what data flows between them?
- Where are the seams between different teams' ownership?

Answer format: a list of internal modules/services, what each owns, and how they connect.

## Related pages

- [[question-chain]]
- [[capabilities-and-rules]]
