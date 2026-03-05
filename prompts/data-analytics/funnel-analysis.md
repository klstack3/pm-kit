# Funnel Analysis Interpreter

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have funnel data (conversion rates between steps) and need help interpreting where to focus. This prompt turns raw numbers into prioritized insights and next steps.

---

## The Prompt

```
You are a product analyst specializing in conversion optimization. You think in terms of leverage — where the biggest opportunity is relative to the effort required.

Here is our funnel data:

{{paste_your_funnel_data — can be a table, list of step-to-step conversion rates, or raw numbers}}

**Context:**
- **Product:** {{product}}
- **Funnel Type:** {{e.g., "signup to activation", "free to paid", "landing page to purchase"}}
- **Time Period:** {{when_this_data_is_from}}
- **Known Context:** {{anything_relevant — e.g., "we launched a new landing page last month", "pricing changed in March"}}

Analyze the funnel:

1. **Step-by-Step Diagnosis:** For each step transition, assess:
   - Is this conversion rate good, average, or concerning compared to typical benchmarks for this type of funnel?
   - What are the 2-3 most likely reasons for drop-off at this step?
   - What data would you want to see to confirm each hypothesis?

2. **Biggest Lever:** Which single step improvement would have the largest impact on end-to-end conversion? Show the math — if we improved this step by X%, what happens to overall throughput?

3. **Quick Wins vs. Deep Investigations:**
   - Quick wins: Changes that are low-effort and likely to improve conversion (e.g., copy changes, removing a step)
   - Deep investigations: Problems that need more data or research before you can act (e.g., "we need session recordings of step 3 drop-offs")

4. **Segmentation Hypotheses:** Suggest 3 ways to segment this funnel that might reveal hidden patterns (e.g., "mobile vs. desktop at step 2 might show very different behavior").

5. **What This Funnel Doesn't Tell Us:** What important questions can't be answered by this data alone?
```

---

## Variables

- `{{paste_your_funnel_data}}` — Your funnel data in any format
- `{{product}}` — Your product
- `{{e.g., "signup to activation"}}` — The funnel type
- `{{when_this_data_is_from}}` — Time period
- `{{anything_relevant}}` — Contextual information

---

## Example

**Input:**
- Landing page: 10,000 visitors
- Signup form started: 2,400 (24%)
- Signup completed: 1,800 (75% of started)
- First action taken: 540 (30% of completed)
- Activated (defined as 3+ actions in first week): 216 (40% of first action)
- Overall: 2.16% landing → activated

**Sample output excerpt:**
> **Biggest Lever:** First action taken (30% of completed signups)
>
> This is the largest single drop-off (70% loss) and it's post-signup, meaning these users already showed intent. Improving this from 30% to 45% would increase end-to-end activation from 2.16% to 3.24% — a 50% relative improvement.
>
> *Math: 10,000 × 24% × 75% × **45%** × 40% = 324 activated (vs. current 216)*

---

## Tips

- **Paste raw data, not just percentages.** Absolute numbers matter — a 50% drop-off from 100 users is very different from 50% of 100,000 users.
- **The "Biggest Lever" math is the key output.** Use it to justify where to invest resources.
- **Take the segmentation hypotheses seriously.** An overall 30% conversion might hide a 60% rate for one segment and a 10% rate for another.
- **Don't skip "What This Funnel Doesn't Tell Us."** It prevents over-indexing on a single data source.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Original to PM-Kit, synthesized from product analytics best practices and conversion optimization frameworks.

**What we changed and why:** Written from scratch. Existing funnel analysis prompts (from [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and others) ask the AI to "interpret funnel data" without providing an analytical framework. Our version structures the analysis into diagnosis, leverage calculation, action categorization, and segmentation — making the output immediately actionable.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Clear role, five-section analysis framework, requires math for leverage calculation |
| **Structure** | 3/3 | Five sections progressing from diagnosis to action to limitations |
| **Reasoning Guidance** | 3/3 | Requires hypothesis generation per step, leverage math, and segmentation thinking |
| **Output Quality** | 3/3 | Diagnosis + math + quick wins vs. investigations + segmentation + limitations |
| **Robustness** | 3/3 | "What this doesn't tell us" prevents over-interpretation; segmentation catches hidden patterns |
| **Total** | **15/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.