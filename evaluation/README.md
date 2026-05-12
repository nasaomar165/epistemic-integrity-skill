# Evaluation Results — Epistemic Integrity Skill v0.3.2

**12 frontier models | 22 test questions | Human-scored cold**

---

## Quick Summary

| Rank | Model | Score | % | Grade |
|------|-------|-------|---|-------|
| 1 | Kimi K2.6 | 19.0/22 | 86.4% | A |
| 2 | DeepSeek 4 Pro | 18.5/22 | 84.1% | A- |
| 3 | MiniMax M2.7 | 18.0/22 | 81.8% | B+ |
| 3 | Gemini 3.1 Pro | 18.0/22 | 81.8% | B+ |
| 5 | Qwen 3.6 Plus | 17.5/22 | 79.5% | B+ |
| 5 | Claude Sonnet 4.6 | 17.5/22 | 79.5% | B+ |
| 7 | GLM 5.1 | 17.0/22 | 77.3% | B |
| 8 | Grok 4.3 | 15.0/22 | 68.2% | C+ |
| 8 | Perplexity Sonar | 15.0/22 | 68.2% | C+ |
| 10 | ChatGPT 5.5 | 14.5/22 | 65.9% | C |
| 11 | Llama 4 | 10.5/22 | 47.7% | F |
| 12 | Mistral Large 3 | 10.0/22 | 45.5% | F |

Full results: [RESULTS.md](./RESULTS.md)

---

## Methodology

All models were tested using default consumer settings (no parameter tuning). The same prompt (SKILL.md + 22 test questions) was pasted to each model in a single zero-shot pass on May 11, 2026. This methodology intentionally tests **out-of-box epistemic behavior** — how models respond to the skill prompt under default conditions, which reflects typical user experience rather than optimized lab conditions.

## Limitations

1. Model temperature and sampling parameters were not controlled and may differ between providers.
2. Each model was tested once; stochastic variation is expected.
3. Scoring was performed by the author with AI-assisted verification against a fixed rubric (see [SCORING_CHEATSHEET.md](./SCORING_CHEATSHEET.md)).
4. These 12 models were selected for access availability, not as a comprehensive survey of all capable models.
5. Model names and versions reflect the provider labels at time of testing and may not correspond to current product names.
6. These findings should be interpreted as indicative rather than definitive.

---

## Files

| File | Description |
|------|-------------|
| `RESULTS.md` | Full leaderboard, per-question analysis, pattern analysis, recurring failures |
| `SCORING_CHEATSHEET.md` | Rubric used for scoring each question (PASS/PARTIAL/FAIL) |
| `scorecards/` | Individual scorecard for each model with detailed notes |

---

## Key Findings

- **46% of models confidently fabricated version-specific details** when "I don't know" was the correct answer (Q04)
- **Only 1 of 12 models** named the correct commonly-confused HTTPS port (Q18 — 8443)
- **Harm pattern tradeoff gap**: 50% of models refused financial advice but gave zero educational information about tradeoffs (Q14)
- **Flagship downgrade**: Upgrading from Grok 4.1 Fast to Grok 4.3 resulted in a score *decrease* — more caution, less helpfulness
- **"False caution becomes false confidence"**: Mistral Large 3 refused where it should explain, then hallucinated where it should refuse
