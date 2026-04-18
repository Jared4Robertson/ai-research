# Gemma 4

**Summary**: Google's most capable open model family as of April 2026, released under Apache 2.0 with four sizes targeting edge, desktop, and server hardware.

**Sources**: raw/Gemma 4 Byte for byte, the most capable open models.md

**Last updated**: 2026-04-18

---

Announced April 2, 2026 by Google DeepMind. Built from the same research and technology as Gemini 3. Over 400 million Gemma downloads across all generations; 100,000+ community variants (the "Gemmaverse").

## Model sizes

| Model | Active parameters | Target hardware |
|---|---|---|
| E2B | Effective 2B | Mobile, IoT, Android |
| E4B | Effective 4B | Mobile, IoT, Android |
| 26B MoE | 3.8B active (26B total) | Consumer GPU, laptop |
| 31B Dense | 31B | Single 80GB H100 (unquantized), consumer GPU (quantized) |

The 26B uses [[mixture-of-experts]] — activating only 3.8B parameters during inference for fast tokens-per-second. The 31B Dense maximizes raw quality and is the preferred base for fine-tuning.

## Performance

- 31B Dense: ranked #3 open model on Arena AI text leaderboard (as of April 1, 2026)
- 26B MoE: ranked #6 open model
- Both outperform models up to 20x their size by parameter count (source: raw/Gemma 4 Byte for byte, the most capable open models.md)

## Key capabilities

- **Advanced reasoning:** multi-step planning, math, instruction-following
- **Agentic workflows:** native function calling, structured JSON output, system instructions
- **Multimodal:** all models process video and images natively; E2B and E4B add native audio input
- **Context window:** 128K (edge models), 256K (larger models)
- **Languages:** natively trained on 140+ languages
- **Code generation:** high-quality offline code generation

## License

Apache 2.0 — commercially permissive, complete developer flexibility and digital sovereignty.

## Ecosystem

Available via: Google AI Studio, Hugging Face, Kaggle, Ollama, NVIDIA NIM, LM Studio, vLLM, llama.cpp, MLX, Unsloth, SGLang, and more. Deployable on Vertex AI, Cloud Run, GKE, and TPUs.

## Related pages

- [[mixture-of-experts]]
- [[open-models]]
