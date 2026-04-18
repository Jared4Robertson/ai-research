# Program.md Pattern

**Summary**: A living instruction file the human edits to steer an autonomous coding agent — shifting the researcher's role from hand-editing code to evolving high-level strategy.

**Sources**: raw/karpathy-autoresearch-notes.md

**Last updated**: 2026-04-18

---

In [[autoresearch]], `program.md` is the file the human maintains while the agent maintains `train.py`. Rather than hand-tuning code to run experiments, the researcher writes and refines natural language instructions that shape the agent's behavior and research direction over time. The README describes it as a "super lightweight skill."

## The inversion

This flips the traditional research workflow:

| Traditional | Autoresearch |
|---|---|
| Researcher hand-edits training code | Researcher edits `program.md` |
| Runs experiments manually | Agent edits `train.py` and runs experiments |
| Interprets results, edits again | Agent keeps improvements, discards regressions |

The agent's search space is bounded by a single diff surface (`train.py`). The human's leverage point moves up the stack to intent and strategy.

## Broader applicability

`program.md` is essentially a "research org in a file" — a living document that accumulates the researcher's priors, constraints, and direction over time. The pattern is analogous to a CLAUDE.md or agent system prompt, but purpose-built for iterative scientific experimentation. The key property: it's human-editable at a higher level of abstraction than the thing being automated.

## Related pages

- [[autoresearch]]
- [[repository-as-context]]
- [[agent-harness]]
