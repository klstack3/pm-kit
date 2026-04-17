# Post-Launch Review: Did the Upgrade Work?

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

It is 30–90 days post-launch and you need to run a structured review of whether the upgrade achieved its goals. Use this to produce a metric verdict, requirements retrospective, and lessons learned — not a celebration document.

Good for: post-launch reviews, platform migration retrospectives, feature release evaluations, or any initiative where you committed to specific outcomes upfront and need to honestly assess whether you delivered them.

---

## The Prompt

```
You are a product leader who runs post-launch reviews with discipline and honesty. You do not conduct post-mortems that are really celebrations, and you do not conduct them in a way that assigns blame. You care about whether the product is better for users, whether the team learned something, and whether the next decision will be smarter because of this one.

I need to run a structured post-launch review for a product tech stack upgrade.

**Inputs:**
- Original goals and success metrics: {{paste_metric_definition_output}}
- Actual metrics at 30/60/90 days: {{paste_current_metric_values}}
- Original requirements: {{paste_requirements_definition_output}}
- Known issues or incidents since launch: {{brief_list}}
- Team feedback (optional): {{brief_summary_or_"not_collected"}}

---

**Step 1: Metric verdict**

For each metric in the framework, state:
- Target vs. actual
- Verdict: exceeded, met, missed, or no data
- For any miss: what hypothesis explains the gap?
- For any "no data": what measurement gap needs to be closed?

**Step 2: Requirements retrospective**

For each must-have requirement, state whether it was:
- Fully delivered
- Partially delivered (specify what is missing)
- Not delivered (specify why)

Identify any requirement that was delivered but did not produce the expected outcome. This is the most valuable learning.

**Step 3: What the tech stack change enabled**

Describe concretely what the new stack made possible that was not possible before. Be specific — do not say "improved developer velocity" without a concrete example.

**Step 4: What was harder than expected**

Name the 3 things that were more difficult than the migration plan anticipated. For each, state:
- What the plan assumed
- What actually happened
- What this means for future planning

**Step 5: Decisions and next steps**

Based on the review, produce:
- A prioritized list of the top 3 things to address in the next cycle
- A revised north star metric or target if the data warrants it
- Any requirement that should be promoted to must-have for the next phase

**Step 6: Document for future teams**

Write a one-paragraph "lessons learned" summary that a future product manager on a similar migration could read in 60 seconds and act on. No jargon, no hedging, just what you would tell your past self before starting this.

**Output format:**
- Steps 1 and 2 as tables
- Steps 3 and 4 as narrative paragraphs
- Step 5 as a prioritized numbered list
- Step 6 as a standalone paragraph

**Constraints:**
- Every metric miss must have a hypothesis — "we don't know" is acceptable only if paired with a plan to find out
- Step 4 must be honest — if the plan was wrong, say so
- The lessons learned paragraph must be under 100 words
```

---

## Variables

- `{{metric_definition_output}}` — Output from the Metric Definition prompt
- `{{actual_metrics}}` — Real data at 30/60/90 days post-launch
- `{{requirements_definition_output}}` — Output from the Requirements Definition prompt
- `{{incidents_since_launch}}` — Any issues, outages, or rollbacks that occurred
- `{{team_feedback}}` — Engineering or design retro notes if available

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Six steps, verdict taxonomy, delivered/partial/not matrix, 100-word lessons constraint |
| **Structure** | 3/3 | Metric verdict → requirements retro → what worked → what didn't → next steps → lessons |
| **Reasoning Guidance** | 3/3 | Gap hypothesis requirement, "delivered but no outcome" flag, plan vs. actual framing |
| **Output Quality** | 3/3 | Tables, narratives, numbered list, standalone paragraph — format matched to content |
| **Robustness** | 3/3 | "We don't know" rule, honesty requirement for Step 4, 100-word constraint |
| **Total** | **15/15** | |
