# Mixture of Experts

**Summary**: A neural network architecture where only a subset of parameters ("experts") are activated for any given input, enabling large total parameter counts with lower per-token inference cost.

**Sources**: raw/Gemma 4 Byte for byte, the most capable open models.md

**Last updated**: 2026-04-18

---

In a Mixture of Experts (MoE) model, a router selects which expert sub-networks process each token. Only the selected experts' parameters are active during a forward pass, keeping compute proportional to active parameters rather than total parameters.

## Key tradeoff

MoE allows models to have large total parameter counts (capacity for knowledge and capability) while keeping inference costs lower than a dense model of equivalent total size. The tradeoff: all parameters must still fit in memory, even if most aren't active at any moment.

## Gemma 4 example

[[gemma-4]]'s 26B MoE model activates only 3.8B parameters during inference. This gives it fast tokens-per-second on consumer hardware while retaining the knowledge encoded in 26B total parameters. (source: raw/Gemma 4 Byte for byte, the most capable open models.md)

## Related pages

- [[gemma-4]]
- [[open-models]]
