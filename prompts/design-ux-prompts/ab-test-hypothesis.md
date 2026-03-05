# A/B Test Hypothesis Generator

**Category:** Design & UX
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You want to run an A/B test but need a well-structured hypothesis, clearly defined metrics, and a sanity check on whether the test is worth running at all.

---

## The Prompt

```
You are a growth product manager and experimentation expert. You've designed hundreds of A/B tests and know that a poorly framed experiment wastes more resources than no experiment at all.

I want to design an A/B test for the following:

- **Product:** {{product}}
- **Area of the product:** {{screen_flow_or_feature}}
- **What we want to change:** {{proposed_change — e.g., "Replace the multi-step onboarding with a single-page form"}}
- **Why we think this will work:** {{our_hypothesis_or_intuition}}
- **Current performance:** {{baseline_metrics_if_known}}

Generate a complete experiment design:

**1. Hypothesis Statement**
Write it in this format: "If we [change], then [metric] will [improve/decrease] by [estimated amount], because [reasoning based on user behavior]."

**2. Primary Metric**
The single metric that determines if the test succeeds or fails. Define it precisely (calculation, time window, user segment).

**3. Secondary Metrics (2-3)**
Supporting metrics that help interpret the result. Include at least one that could indicate the change is working for the wrong reasons.

**4. Guardrail Metrics (1-2)**
Things that must NOT get worse. Define the threshold for "unacceptable regression."

**5. Test Design**
- What's in the control vs. variant
- Recommended traffic split and why
- Estimated sample size and test duration (state assumptions)
- Key segments to analyze separately

**6. Pre-Registration Checks**
Before running the test, answer:
- Is the expected effect size large enough to detect with our traffic?
- Are there any confounding factors (seasonality, other launches, marketing campaigns)?
- What would a null result tell us? Is that still useful information?

**7. Decision Framework**
Define in advance:
- What result means "ship it"
- What result means "iterate"
- What result means "kill it"
- What result means "the test was inconclusive and we need to re-run"
```

---

## Variables

- `{{product}}` — Your product
- `{{screen_flow_or_feature}}` — Where in the product the change happens
- `{{proposed_change}}` — What you want to test
- `{{our_hypothesis_or_intuition}}` — Why you think this will work
- `{{baseline_metrics_if_known}}` — Current performance numbers (if available)

---

## Example

**Input:**

- Product: SaaS project management tool
- Area: Pricing page
- Change: Add a "most popular" badge to the mid-tier plan
- Hypothesis: Social proof will nudge users toward the mid-tier plan
- Current performance: 40% choose free, 35% choose mid-tier, 25% choose enterprise

**Sample output excerpt:**

> **Hypothesis:** If we add a "most popular" badge to the Professional plan, then mid-tier plan selection rate will increase by 5-10 percentage points (from 35% to 40-45%), because users experiencing choice overload will anchor to the socially validated option.
>
> **Guardrail:** Enterprise plan selection rate must not drop by more than 3 percentage points. A shift from enterprise to mid-tier would reduce ARPU even if total conversions increase.

---

## Tips

- **The decision framework is the most important section.** Define what you'll do with each outcome BEFORE you see the results. This prevents post-hoc rationalization.
- **Include guardrail metrics seriously.** A test that increases signups but decreases revenue is a failure, not a success.
- **Use the "null result" pre-check.** If a null result teaches you nothing, reconsider whether the test is worth running.
- **Share the full experiment design with your team before launching.** The pre-registration prevents cherry-picking metrics after the fact.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from A/B test prompts on [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and experimentation best practices from Ronny Kohavi's work on controlled experiments.

**What we changed and why:**

- **Added pre-registration checks.** The original asked for hypothesis and metrics but not whether the test was feasible or worth running.
- **Added a decision framework.** No original defined what to do with each possible outcome, which is the #1 failure mode in experimentation programs.
- **Added guardrail metrics with thresholds.** The original mentioned tracking metrics but didn't require defining what "unacceptable" looks like.
- **Added the "wrong reasons" secondary metric.** Requires thinking about how a positive result could be misleading.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                              |
| ---------------------- | --------- | ------------------------------------------------------------------------------------------------------ |
| **Specificity**        | 3/3       | Clear role, structured hypothesis format, seven defined sections                                       |
| **Structure**          | 3/3       | Seven sections from hypothesis through decision framework                                              |
| **Reasoning Guidance** | 3/3       | Pre-registration checks, null result analysis, and "wrong reasons" metric force rigorous thinking      |
| **Output Quality**     | 3/3       | Complete experiment design ready for team review; decision framework prevents post-hoc rationalization |
| **Robustness**         | 3/3       | Pre-registration feasibility check, guardrails, and inconclusive-result handling                       |
| **Total**              | **15/15** |                                                                                                        |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
