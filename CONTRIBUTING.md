# Contributing to Epistemic Integrity

Thank you for helping make this better. Here is how to contribute effectively.

---

## What We Need Most

**Hard examples** — cases where the skill fails on subtle confident-wrong answers.
Obvious cases (medical advice, recent news) are already covered. The gaps are in the edges.

**Test results on new models** — if you run `test_suite.json` on a model not listed in the README, open a PR with your results.

**Real-world failure reports** — if you deployed this and found inputs the skill mishandled, that is exactly the data needed to improve it.

---

## Adding Examples

Add to `examples.json` under the most relevant category. For subtle confident-wrong cases, use `CAT-08`.

Required fields:
```json
{
  "id": "EX-08-X",
  "user": "the exact input",
  "wrong_response": "what the model said without the skill",
  "why_wrong": "one-line diagnosis of the failure mode",
  "right_response": "what it should have said with the skill active",
  "why_right": "one-line explanation of why this is better"
}
```

Hard cases > obvious cases. If the wrong answer feels completely natural and fluent, it belongs here.

---

## Adding Test Cases

Add to `test_suite.json`. Follow the existing structure:

```json
{
  "id": "TC-XX",
  "category": "descriptive category name",
  "input": "the test input",
  "expected_behavior": "what the model should do",
  "expected_response_pattern": "key phrases or structure expected",
  "should_ask_clarification": true/false,
  "should_flag_uncertainty": true/false,
  "should_decline": true/false,
  "failure_if": "what would indicate the skill failed",
  "measures": "which metric this test targets"
}
```

---

## Reporting Model Results

Open a PR or issue with:
- Model name and version
- Test date
- Score on each test case (PASS / PARTIAL / FAIL)
- Any cases that failed and what the model said
- System prompt setup you used

For the full 22-question battery, use the scoring rubric in `evaluation/SCORING_CHEATSHEET.md` and create a scorecard following the format in `evaluation/scorecards/`.

---

## Pull Request Guidelines

- One change per PR — examples, test cases, and skill updates should be separate PRs
- For skill changes: explain why, reference the failure mode it addresses, show before/after
- For new examples: include evidence the wrong response is what models actually produce
- For evaluation results: include the full scorecard, methodology, and date

---

## Known Gaps for v3.3

These are the areas most likely to benefit from community contributions:

| Gap | What's Needed |
|-----|---------------|
| Q18 audience definition | Pattern G should define whose "common wrong answer" matters — lay users vs. engineers |
| Q14 harm-tradeoff clarity | Pattern C should clarify: "information only" means educational, not a bare refusal |
| Q11 code requirement | Pattern A should explicitly require code examples for API/library questions |
| Q10 ordering enforcement | Pattern D should state: "when impossibility is detected, do not name partial answers" |
| Inter-rater reliability | Current scoring was done by one person + AI assist. Independent second scorer would strengthen results |

---

## What Not To Do

- Do not add easy examples that every model already handles correctly
- Do not add philosophical content to `SKILL.md` — it should stay one screen, dense and executable
- Do not remove the escape hatch wording from the clarification protocol
- Do not merge Pattern C's override with Pattern D's exception — they serve different purposes
- Do not submit evaluation results without documenting your methodology

---

*Small improvements, honestly motivated, compound into something real. — Claude Sonnet 4.6*
