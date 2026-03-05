# Experiment Design

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You're planning a product experiment (A/B test, feature flag rollout, beta program) and need to design it rigorously — hypothesis, metrics, sample size, duration, and analysis plan. Distinct from the A/B Test Hypothesis prompt (in Design & UX) in that this focuses on the statistical and analytical design rather than the UX framing.

---

## The Prompt

```
You are a data scientist specializing in product experimentation. You've designed and analyzed hundreds of controlled experiments and you're rigorous about statistical validity.

Design an experiment for the following:

- **What we're testing:** {{what_change_or_feature}}
- **Current baseline:** {{current_metric_values}}
- **Minimum detectable effect:** {{smallest_change_worth_detecting — e.g., "a 5% relative increase in conversion"}}
- **Traffic/user volume:** {{approximate_daily_or_weekly_volume}}
- **Risk tolerance:** {{how_much_risk_is_acceptable — e.g., "low risk, this is a core flow" or "high risk tolerance, this is a new feature"}}

Provide a complete experiment design:

**1. Hypothesis**
Clearly state the null and alternative hypotheses.

**2. Experiment Structure**
- Control vs. treatment description
- Randomization unit (user, session, device, etc.) and why
- Traffic allocation and ramp-up plan
- Experiment duration estimate (show your math: significance level, power, baseline rate, MDE, sample size calculation)

**3. Metric Framework**
- Primary decision metric (one only)
- Secondary metrics (2-3, with rationale for each)
- Guardrail metrics (with specific thresholds for what triggers an automatic rollback)

**4. Segmentation Plan**
Which segments should we analyze separately? (e.g., new vs. returning users, mobile vs. desktop, plan tier). For each, explain why it might show a different effect.

**5. Analysis Plan**
- Statistical test to use and why
- One-sided or two-sided test?
- How to handle multiple comparisons (if analyzing segments)
- What to do if results are directional but not statistically significant

**6. Risks & Mitigations**
- Novelty effect: how to detect and handle it
- Simpson's paradox: segments that could reverse the overall result
- Interference: could treatment users affect control users?
- Sample ratio mismatch: how to detect and what to do

**7. Decision Criteria**
Define in advance what each outcome means for the product decision.
```

---

## Variables

- `{{what_change_or_feature}}` — The thing being tested
- `{{current_metric_values}}` — Baseline metrics
- `{{smallest_change_worth_detecting}}` — Minimum detectable effect
- `{{approximate_daily_or_weekly_volume}}` — Traffic available for the experiment
- `{{how_much_risk_is_acceptable}}` — Risk tolerance

---

## Example

**Input:**
- Testing: New checkout flow (single page vs. current multi-step)
- Baseline: 3.2% checkout completion rate
- MDE: 0.5 percentage points (3.2% → 3.7%)
- Traffic: ~15,000 checkout sessions per week
- Risk: Low — checkout is a core revenue flow

**Sample output excerpt:**
> **Duration Estimate:**
> - Significance level (α): 0.05
> - Power (1-β): 0.80
> - Baseline rate: 3.2%
> - MDE: 0.5pp (15.6% relative increase)
> - Required sample per variant: ~24,500 sessions
> - With 15K sessions/week at a 50/50 split: ~3.3 weeks
> - **Recommendation:** Run for 4 full weeks to capture weekly cyclicality
>
> **Guardrail:** Revenue per session must not decrease by more than 2%. An automated alert triggers if the treatment variant shows >2% revenue regression at any daily checkpoint.

---

## Tips

- **The sample size math is the most important output.** If you don't have enough traffic for your desired MDE, you need to either accept a larger MDE, run longer, or question whether an experiment is the right approach.
- **Use the novelty effect mitigation.** Exclude the first 48 hours from analysis, or run the experiment long enough that novelty wears off.
- **Pre-register the analysis plan.** Share it with your team before results come in to prevent p-hacking and narrative-fitting.
- **The "directional but not significant" scenario is the most common.** Having a plan for it in advance saves weeks of debate.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Original to PM-Kit, synthesized from experimentation best practices (Ronny Kohavi's *Trustworthy Online Controlled Experiments*), and statistical design patterns from the data science community.

**What we changed and why:** This prompt was written from scratch. While [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) has an experiment design prompt, it focuses on hypothesis and metrics without addressing statistical rigor (sample size, power analysis, multiple comparisons, novelty effects). Our version includes the full analytical design that a data scientist would need.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Data scientist role, seven sections, statistical parameters explicitly requested |
| **Structure** | 3/3 | Seven sections from hypothesis through decision criteria; math shown for duration |
| **Reasoning Guidance** | 3/3 | Null/alternative hypotheses, sample size calculation with shown math, multiple comparison handling |
| **Output Quality** | 3/3 | Complete experiment spec including ramp plan, automated rollback triggers, and analysis plan |
| **Robustness** | 3/3 | Novelty effect, Simpson's paradox, interference, and SRM all addressed |
| **Total** | **15/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.