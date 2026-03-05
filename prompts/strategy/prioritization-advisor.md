# Prioritization Advisor

**Category:** Strategy
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have a list of features, projects, or initiatives and need help prioritizing them. This prompt supports RICE, ICE, and MoSCoW frameworks and helps you think through scoring rather than just assigning arbitrary numbers.

---

## The Prompt

```
You are a senior product manager who specializes in prioritization frameworks. You understand that the value of prioritization isn't the final ranking — it's the structured conversation it forces.

I need help prioritizing the following items:

{{paste_your_list_of_features_or_initiatives}}

**Context:**
- **Product/Team:** {{product_or_team}}
- **Planning Horizon:** {{time_period}}
- **Key Constraints:** {{resource_constraints_or_dependencies}}
- **Strategic Goals:** {{what_the_team_is_optimizing_for}}

Use the {{RICE / ICE / MoSCoW}} framework. For each item:

1. **Score each dimension independently.** Show your reasoning for each score, not just the number. Reference the strategic goals and constraints I provided.
2. **Flag uncertainty.** If you don't have enough information to confidently score a dimension, say so and explain what information would change your score.
3. **Check for biases.** After scoring everything, review your own scores for:
   - Recency bias (did you over-weight things mentioned first?)
   - Complexity bias (did you under-rate simple things?)
   - Confidence bias (did you over-rate things you understand well?)

**Output:**
- A scored table sorted by priority
- Your top 3 recommendation with one-sentence rationale each
- A "parking lot" of items you'd deprioritize and why
- 2-3 questions that, if answered, would most change the ranking
```

---

## Variables

- `{{paste_your_list_of_features_or_initiatives}}` — Your feature list in any format
- `{{product_or_team}}` — Context on the team doing the work
- `{{time_period}}` — e.g., "Next quarter", "H2 2025"
- `{{resource_constraints_or_dependencies}}` — e.g., "2 engineers, 1 designer, no ML infra"
- `{{what_the_team_is_optimizing_for}}` — e.g., "Reduce churn in enterprise segment"
- `{{RICE / ICE / MoSCoW}}` — Pick your framework

---

## Example

**Input:**

- Features: Dark mode, API rate limit dashboard, SSO for enterprise, onboarding wizard revamp, Slack integration
- Product: Developer tools platform
- Horizon: Q3 2025
- Constraints: 3 engineers, no dedicated designer
- Goals: Increase enterprise adoption

**Sample output excerpt:**

> | Feature                  | Reach | Impact | Confidence | Effort | RICE Score |
> | ------------------------ | ----- | ------ | ---------- | ------ | ---------- |
> | SSO for enterprise       | 8     | 9      | 9          | 6      | 108        |
> | API rate limit dashboard | 7     | 7      | 7          | 3      | 114        |
>
> ...
>
> ⚠️ _Uncertainty flag: "Onboarding wizard revamp" — I scored Impact at 6, but this could be an 8 or a 3 depending on whether the drop-off is actually in onboarding vs. a deeper product-market fit issue. Recommend running a funnel analysis before committing._

---

## Tips

- **The bias check is the most unique part of this prompt.** Most prioritization exercises don't ask you to audit your own scoring. Review that section carefully.
- **Don't use this as a calculator.** The AI's specific numbers aren't the point. The reasoning behind each score is what matters — use it to spark debate with your team.
- **Pair with real data.** Replace the AI's Reach and Impact estimates with actual metrics where you have them. The AI is best at structuring the framework, not providing the data.
- **Try running it with two different frameworks on the same list.** If RICE and ICE produce very different rankings, that tells you something important about your uncertainty.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from prioritization prompts shared by [Adrian Raudaschl](https://breakingproduct.substack.com/p/25-prompts-for-product-managers-obsessed) (Breaking Product newsletter) and [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/).

**What we changed and why:**

- **Added explicit reasoning requirements.** The originals asked the AI to score items but not explain its reasoning. We require justification for each score.
- **Added bias checking.** No original prompt included a self-audit for scoring biases, which is one of the biggest failure modes in prioritization exercises.
- **Added uncertainty flags.** The originals treated all scores as equally confident. We require the AI to flag where it lacks information.
- **Added the "questions that would change the ranking" output.** This turns the prioritization from a static exercise into an action plan for what to go learn.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                      |
| ---------------------- | --------- | ---------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role, framework selection, explicit scoring requirements with reasoning                  |
| **Structure**          | 3/3       | Scored table + recommendations + parking lot + open questions                                  |
| **Reasoning Guidance** | 3/3       | Requires reasoning per score, bias self-check, and uncertainty flags                           |
| **Output Quality**     | 3/3       | Multiple output formats (table, narrative, questions); parking lot prevents "everything is P1" |
| **Robustness**         | 3/3       | Bias checking, uncertainty flags, and "what would change this" questions all handle ambiguity  |
| **Total**              | **15/15** |                                                                                                |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
