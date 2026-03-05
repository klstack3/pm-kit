# OKR Generator & Critic

**Category:** Strategy
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to draft OKRs for a planning cycle, or you have existing OKRs that need pressure-testing. This prompt works in two modes: generation (create OKRs from strategic themes) and critique (evaluate and improve existing OKRs).

---

## The Prompt

### Mode 1: Generate OKRs

```
You are a product leader with deep experience writing effective OKRs. You understand that good OKRs are ambitious but achievable, measurable without being gameable, and clearly tied to strategic outcomes.

Generate OKRs for the following context:

- **Team/Product:** {{team_or_product}}
- **Time Period:** {{quarter_or_half}}
- **Strategic Themes:** {{top_2_to_3_strategic_priorities}}
- **Current State:** {{brief_description_of_where_things_stand_today}}

For each Objective:
- Write it as an aspirational, qualitative statement that a human would be motivated by
- Provide 3-4 Key Results that are specific, measurable, and time-bound
- For each Key Result, include the current baseline value and the target
- Flag any Key Result where you're uncertain about whether the target is appropriately ambitious

At the end, provide:
- **Potential conflicts:** Any Key Results that might work against each other
- **Missing coverage:** Strategic areas that these OKRs don't address
- **Measurement risks:** Key Results that could be gamed or that might incentivize the wrong behavior
```

### Mode 2: Critique Existing OKRs

```
You are a product leader who has reviewed hundreds of OKRs and knows the common failure modes. Your job is to be a constructive but direct critic.

Here are our current OKRs:

{{paste_your_okrs_here}}

Critique them against these dimensions:

1. **Ambition Calibration:** Are these stretch goals or sandbagged targets? Would achieving 70% of each KR still represent meaningful progress?
2. **Measurability:** Can each KR be unambiguously measured? Is there a clear definition of "done"?
3. **Alignment:** Do the KRs actually ladder up to the Objective, or are some tangentially related?
4. **Completeness:** If we hit every KR, would we truly have achieved the Objective?
5. **Gameability:** Could someone technically hit a KR while violating the spirit of the Objective?
6. **Dependencies:** Do any KRs depend on teams or factors outside our control?

For each issue you identify, provide a specific rewrite suggestion. Don't just flag problems — propose fixes.
```

---

## Variables

**Mode 1:**

- `{{team_or_product}}` — The team or product area
- `{{quarter_or_half}}` — The time period (e.g., "Q3 2025")
- `{{top_2_to_3_strategic_priorities}}` — The strategic themes these OKRs should serve
- `{{brief_description_of_where_things_stand_today}}` — Current baselines and context

**Mode 2:**

- `{{paste_your_okrs_here}}` — Your existing OKRs in any format

---

## Example

**Mode 1 Input:**

- Team: Growth team at a B2B SaaS product
- Time Period: Q3 2025
- Strategic Themes: Reduce time-to-value for new users; Expand self-serve revenue
- Current State: 14-day average activation time; 15% of revenue is self-serve; NPS is 42

**Sample output excerpt:**

> **Objective: New users experience value fast enough to convert without sales intervention**
>
> - KR1: Reduce median time-to-first-value from 14 days to 5 days
> - KR2: Increase 7-day activation rate from 23% to 40%
> - KR3: Reduce support tickets filed during first 7 days by 30%
>
> ⚠️ _Ambition flag: KR2 (23% → 40%) is aggressive. Consider whether 35% is a more realistic stretch target given current onboarding flow constraints._

---

## Tips

- **Use both modes together.** Generate first, then immediately run Mode 2 on your own output. The critique mode catches things the generation mode misses.
- **Include baselines.** OKRs without baselines are impossible to evaluate. If you don't know the current number, say so — the AI will flag it.
- **Watch for vanity KRs.** The critique mode specifically checks for gameability. If a KR can be hit by doing something that doesn't actually matter, rewrite it.
- **Share the "Potential Conflicts" section with your leadership.** This is where the most productive planning conversations happen.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from OKR prompts shared by [Adrian Raudaschl](https://breakingproduct.substack.com/p/25-prompts-for-product-managers-obsessed) (Breaking Product newsletter).

**What we changed and why:**

- **Split into two modes (generate + critique).** Raudaschl's original was two separate one-line prompts ("Suggest OKRs" and "Critique these OKRs"). We expanded each into a full structured prompt.
- **Added baseline requirements.** The original didn't ask for current-state baselines, making it impossible to judge whether targets were ambitious or sandbagged.
- **Added conflict detection, coverage gaps, and gameability analysis.** These are the most common OKR failure modes and weren't addressed in the original.
- **Added ambition flags.** The generation mode now self-critiques its own targets, flagging where it's uncertain about calibration.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                      |
| ---------------------- | --------- | ---------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Two distinct modes with clear roles, explicit deliverables, and defined evaluation dimensions  |
| **Structure**          | 3/3       | Generation mode has structured output format; critique mode has 6 named dimensions             |
| **Reasoning Guidance** | 3/3       | Critique dimensions enforce analytical rigor; ambition flags force self-assessment             |
| **Output Quality**     | 3/3       | Baselines + targets for each KR; conflict and gap analysis; rewrite suggestions not just flags |
| **Robustness**         | 3/3       | Gameability check, dependency check, and ambition calibration all address common failure modes |
| **Total**              | **15/15** |                                                                                                |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
