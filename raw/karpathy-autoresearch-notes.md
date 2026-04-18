# Notes: Karpathy’s **autoresearch**

**Repo:** [github.com/karpathy/autoresearch](https://github.com/karpathy/autoresearch)  
**Context:** [tweet 1](https://x.com/karpathy/status/2029701092347630069), [tweet 2](https://x.com/karpathy/status/2031135152349524125) — Karpathy, March 2026.

## What it is

A **minimal autonomous “overnight research” loop** for a **real single-GPU LLM training** codebase (a simplified single-GPU take on [nanochat](https://github.com/karpathy/nanochat)). You point a coding agent (Claude, Codex, etc.) at the repo; the agent **edits training code**, runs short experiments, **keeps changes that improve a validation metric** and discards or iterates otherwise. The human’s main lever is not hand-editing Python like a traditional researcher, but evolving **`program.md`** — instructions that steer the agent (described in the README as a “super lightweight skill”).

## The three files that matter

| File             | Role                                                                                                                                    |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **`prepare.py`** | Fixed: constants, one-time data download, BPE tokenizer training, dataloader/eval utilities. **Agent does not modify.**                 |
| **`train.py`**   | Full GPT, optimizer (Muon + AdamW), training loop, hyperparameters, batching, architecture. **Agent edits this** — single diff surface. |
| **`program.md`** | Baseline instructions for the agent. **Human edits this** to shape behavior and “research org” over time.                               |

Also: `pyproject.toml` for dependencies. README emphasizes keeping the repo **small and self-contained**.

## Experiment protocol (design)

- **Fixed wall-clock budget:** each training run is **5 minutes** (excluding startup/compilation), regardless of what the agent changes. Rough mental math in README: ~**12 experiments/hour**, ~**100 overnight**.
- **Metric:** **`val_bpb`** (validation **bits per byte**) — **lower is better**; **vocab-independent** so architecture/tokenizer changes stay comparable.
- **Why fixed time:** (1) experiments are comparable on _your_ machine for that budget; (2) the system tends toward what’s **best for your platform** in that window. **Tradeoff:** numbers are **not directly comparable** across different hardware setups.

## Requirements & quick start (from README)

- **Hardware:** single **NVIDIA GPU** (README: tested on **H100**). CPU/MPS/other platforms intentionally not in-tree; see **notable forks** in the repo README (macOS, MLX, Windows RTX, AMD, etc.).
- **Stack:** Python **3.10+**, **[uv](https://docs.astral.sh/uv/)**, PyTorch + small deps — no distributed training, no heavy config framework.

Typical flow: `uv sync` → `uv run prepare.py` (data + tokenizer, ~2 min one-time) → `uv run train.py` (sanity ~5 min) → then run an agent with repo access and a prompt like “read `program.md` and kick off a new experiment.”

## Philosophy (condensed)

- **Research as steering agents + `program.md`**, not only as hand-tuning `train.py`.
- **Scope control:** one file for the agent to change → reviewable diffs and bounded search space.
- **Deliberately tiny codebase** so humans and agents can hold the whole thing in context.

## Smaller compute (README guidance)

For laptops / weaker GPUs, README suggests forks and tuning ideas: lower-entropy data (e.g. **TinyStories**), reduce **`vocab_size`**, lower **`MAX_SEQ_LEN`** in `prepare.py`, adjust **`DEVICE_BATCH_SIZE`**, reduce **`EVAL_TOKENS`**, lower **`DEPTH`** in `train.py`, simplify **`WINDOW_PATTERN`**, shrink **`TOTAL_BATCH_SIZE`** (powers of two), etc.

## License

**MIT** (per upstream README).

---

_These notes summarize the public README as of access date; verify details and numbers on the live repo if you’re reproducing experiments._
