# Autoresearch

**Summary**: Karpathy's minimal autonomous overnight research loop — a coding agent edits a single training file, runs fixed-budget GPU experiments, and keeps changes that improve a validation metric.

**Sources**: raw/karpathy-autoresearch-notes.md

**Last updated**: 2026-04-18

---

`autoresearch` is a public repo by Andrej Karpathy ([github.com/karpathy/autoresearch](https://github.com/karpathy/autoresearch), March 2026). It pairs a simplified single-GPU LLM training codebase (derived from nanochat) with an agentic research loop.

## Core idea

A coding agent (Claude, Codex, etc.) is given access to the repo. It edits `train.py`, runs short training experiments, and keeps changes that improve `val_bpb` (validation bits per byte — lower is better, vocab-independent so architectural changes stay comparable). The human's lever is not hand-editing Python but evolving [[program-md-pattern|program.md]].

## The three files that matter

| File | Role |
|---|---|
| `prepare.py` | Fixed: data download, BPE tokenizer, dataloader/eval utilities. Agent does not modify. |
| `train.py` | Full GPT, optimizer (Muon + AdamW), training loop, hyperparameters, architecture. **Agent edits this.** |
| `program.md` | Baseline instructions for the agent. **Human edits this.** See [[program-md-pattern]]. |

## Experiment protocol

- **Fixed wall-clock budget:** each run is 5 minutes (excluding startup/compilation)
- **Throughput:** ~12 experiments/hour, ~100 overnight
- **Metric:** `val_bpb` — validation bits per byte, lower is better
- **Why fixed time:** experiments stay comparable on the same machine; the system tends toward what's best for your platform in that budget window
- **Tradeoff:** numbers are not directly comparable across different hardware setups

## Hardware and stack

- Designed for a single NVIDIA GPU (tested on H100)
- Python 3.10+, uv, PyTorch — no distributed training, no heavy config framework
- Community forks exist for macOS/MLX, Windows RTX, AMD, and weaker GPUs

## Smaller compute guidance

For laptops or weaker GPUs: use lower-entropy data (e.g. TinyStories), reduce `vocab_size`, lower `MAX_SEQ_LEN`, adjust `DEVICE_BATCH_SIZE`, reduce `EVAL_TOKENS`, lower `DEPTH`, simplify `WINDOW_PATTERN`, shrink `TOTAL_BATCH_SIZE` (source: raw/karpathy-autoresearch-notes.md).

## Philosophy

- Research as steering agents + `program.md`, not hand-tuning training code
- Scope control: one file for the agent to change → reviewable diffs and bounded search space
- Deliberately tiny codebase so humans and agents can hold the whole thing in context

## License

MIT

## Related pages

- [[program-md-pattern]]
- [[repository-as-context]]
- [[agent-harness]]
- [[open-models]]
