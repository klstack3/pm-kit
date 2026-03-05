# Metric Definition Helper

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to precisely define a metric — its calculation, data source, edge cases, and interpretation — so that everyone on your team (PM, engineering, data, leadership) means the same thing when they say "activation rate" or "time to value."

---

## The Prompt

```
You are a senior data analyst who specializes in product analytics. You know that most metric disagreements come from ambiguous definitions, not bad math.

I need a rigorous definition for the following metric:

- **Metric Name:** {{metric_name}}
- **Product Context:** {{what_the_product_does_and_who_uses_it}}
- **Why We're Tracking This:** {{what_decision_this_metric_informs}}

Provide a complete metric definition that includes:

**1. Plain Language Definition**
One sentence a non-technical stakeholder would understand.

**2. Precise Calculation**
The exact formula. Specify:
- Numerator (what's being counted, with inclusion/exclusion criteria)
- Denominator (the population, with inclusion/exclusion criteria)
- Time window (daily, weekly, rolling 28-day, etc.)
- How to handle edge cases: bots, test accounts, duplicate events, users who span segments

**3. Data Source**
Where does each component of the calculation come from? (e.g., "event: dashboard_created from the analytics pipeline" or "user table: created_at field")

**4. Segmentation Recommendations**
How should this metric be cut? Suggest 3-5 segments that would reveal meaningful differences (e.g., by plan tier, by acquisition channel, by user tenure).

**5. Interpretation Guide**
- What does "good" look like? (benchmark or target)
- What does a sudden increase mean? (list 3 possible causes)
- What does a sudden decrease mean? (list 3 possible causes)
- What does this metric NOT tell you?

**6. Known Pitfalls**
Common ways this metric can be misleading or gamed. For each pitfall, suggest a companion metric or guardrail that catches it.
```

---

## Variables

- `{{metric_name}}` — The metric you want defined (e.g., "7-day activation rate")
- `{{what_the_product_does_and_who_uses_it}}` — Product context
- `{{what_decision_this_metric_informs}}` — Why this metric matters now

---

## Example

**Input:**

- Metric: 7-day activation rate
- Product: B2B analytics platform; users are data analysts and PMs
- Why: We're redesigning onboarding and need a clear success metric

**Sample output excerpt:**

> **Precise Calculation:**
> Activation Rate (7d) = (Users who created ≥1 dashboard within 7 calendar days of account creation) / (All users who created an account in the cohort period)
>
> _Exclusions: Internal test accounts (email domain = @ourcompany.com), bot accounts (flagged by security team), users who were invited to an existing workspace (they have a different activation path)_
>
> **Known Pitfall:** Counting "dashboard created" includes users who created a dashboard from a template but never added their own data. This inflates the metric.
> **Guardrail:** Track "dashboard with ≥1 custom data source" as a companion metric to ensure activation reflects genuine engagement.

---

## Tips

- **Use this before building dashboards.** A dashboard built on an ambiguous metric wastes everyone's time.
- **The "Known Pitfalls" section prevents Goodhart's Law.** When a metric becomes a target, people optimize for the metric rather than the outcome. The companion metrics catch this.
- **Share the full definition with your data team for review.** They'll know things about the data pipeline (like deduplication logic or event timing) that the AI won't.
- **Store these definitions in a team wiki.** A library of precise metric definitions prevents the "what do we mean by active users?" conversation from happening every quarter.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from metric definition prompts on [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and analytics best practices from the product analytics community.

**What we changed and why:**

- **Added edge case handling in the calculation.** The original asked for a formula but didn't require handling of bots, test accounts, or boundary cases.
- **Added the interpretation guide.** The original produced a definition but no guidance on how to read changes in the metric.
- **Added known pitfalls and companion metrics.** Not present in any original; this is the most practically valuable section for preventing Goodhart's Law problems.
- **Added segmentation recommendations.** The original produced a single number. We require thinking about how the metric varies across populations.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                             |
| ---------------------- | --------- | --------------------------------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role, six-section definition template with precise requirements per section                                     |
| **Structure**          | 3/3       | Six sections from plain language through pitfalls; logical progression from definition to interpretation              |
| **Reasoning Guidance** | 3/3       | Requires causal thinking (what causes changes), adversarial thinking (how can it be gamed), and segmentation thinking |
| **Output Quality**     | 3/3       | Complete metric spec ready for team review; companion metrics prevent gaming                                          |
| **Robustness**         | 3/3       | Edge case handling in calculation, pitfall identification, and interpretation of unexpected changes                   |
| **Total**              | **15/15** |                                                                                                                       |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
