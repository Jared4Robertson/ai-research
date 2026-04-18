# Open Models

**Summary**: Publicly released model weights that can be downloaded, run locally, and fine-tuned — contrasted with proprietary API-only models.

**Sources**: raw/Gemma 4 Byte for byte, the most capable open models.md

**Last updated**: 2026-04-18

---

Open models give developers control over data, infrastructure, and model behavior — deployable on-premises, offline, or in any cloud environment.

Key properties vs. proprietary models:
- **Data sovereignty:** inputs never leave your environment
- **Customizability:** full weight access enables fine-tuning on domain-specific data
- **Offline capability:** no API dependency; works without network access
- **Cost structure:** upfront compute cost rather than per-token API pricing

## Licensing matters

Not all "open" models carry the same permissions:
- **Apache 2.0** (e.g. [[gemma-4]]): commercially permissive, minimal restrictions
- **Meta's LLaMA license**: open weights with usage restrictions
- **Research-only licenses**: prohibit commercial use

## State of open models (April 2026)

[[gemma-4]]'s 31B Dense model ranks #3 on the Arena AI open model leaderboard, competing with and beating models up to 20x its size. This represents a significant narrowing of the gap between open and proprietary frontier models.

The Gemmaverse (100,000+ Gemma variants) illustrates how community fine-tuning multiplies the value of open base models. Notable examples: BgGPT (Bulgarian-first language model by INSAIT) and Cell2Sentence-Scale (cancer therapy pathway discovery with Yale University). (source: raw/Gemma 4 Byte for byte, the most capable open models.md)

## Related pages

- [[gemma-4]]
- [[mixture-of-experts]]
