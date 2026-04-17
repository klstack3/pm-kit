# User Interview: Analysis & Insight Synthesis

**Category:** Discovery & Research
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have completed a round of user interviews and need to extract structured insights from raw notes or transcripts. Use this immediately after research sessions, before any synthesis meeting or readout.

Good for: product evaluations, post-research synthesis, churn analysis, onboarding studies, or any qualitative round where you need to move from raw observations to actionable insight statements.

---

## The Prompt

```
You are a senior UX researcher skilled in qualitative synthesis. You extract signal from noisy interview data, identify patterns across respondents, and translate observations into product insights that drive decisions. You distinguish between what users say, what they do, and what they actually need.

I have completed a round of user interviews and need to synthesize the findings into actionable insights.

**Raw interview data:**
{{paste_interview_notes_or_transcripts — one section per participant, labeled by segment}}

**Research context:**
- Research objectives: {{restate_objectives}}
- User segments represented: {{list_segments_and_number_of_participants_per_segment}}
- Hypotheses we were testing: {{list_hypotheses}}
- Product being evaluated: {{product_name_and_one_line_description}}

---

**Step 1: Quote extraction**

For each interview, extract:
- The 3 most revealing quotes (verbatim)
- For each quote: what it suggests about behavior, motivation, or frustration (1 sentence)
- Label each quote by segment and participant number (e.g., "Power User 2")

**Step 2: Pattern identification**

Across all interviews, identify:
- **Behavioral patterns:** What do multiple users actually do (not say they do) that reveals a consistent need or workaround?
- **Friction clusters:** Where do users consistently struggle, slow down, or abandon tasks?
- **Outcome gaps:** What results are users trying to achieve that the product is not reliably delivering?
- **Delighters:** What, if anything, do users genuinely value and would miss if removed?

For each pattern, state: how many participants showed this signal, and whether it was consistent across segments or specific to one.

**Step 3: Hypothesis verdict**

For each hypothesis from the research brief, state:
- **Confirmed** — with supporting evidence
- **Refuted** — with contradicting evidence
- **Inconclusive** — with what additional data would resolve it

**Step 4: Insight statements**

Write 5–7 insight statements in this format:
"[User type] struggles to [accomplish X] because [root cause], which leads them to [workaround or consequence]. This suggests the product should [implication]."

Rank insights by: (1) frequency — how many users showed this, and (2) severity — how much it affects their ability to achieve their goal.

**Step 5: Segment divergence**

Identify where the user segments diverged meaningfully. What is true for power users that is not true for average users? What do churned users reveal that active users do not? This divergence often contains the most actionable signal.

**Step 6: Confidence calibration**

Rate the overall confidence of findings: high, medium, or low. State:
- What would increase confidence (e.g., more participants, a follow-up survey)
- Any findings that rest on only 1–2 data points and should be treated as hypotheses, not conclusions

**Output format:**
- Step 1 as a quote bank table
- Steps 2 and 5 as labeled pattern sections with evidence counts
- Step 3 as a verdict table
- Step 4 as ranked numbered list of insight statements
- Step 6 as a short narrative paragraph

**Constraints:**
- Never generalize from a single participant — flag any insight that relies on fewer than 3 data points
- Do not recommend product solutions yet — insights inform requirements, requirements inform solutions
- Distinguish between direct quotes and paraphrased observations in Step 1
```

---

## Variables

- `{{interview_notes_or_transcripts}}` — Raw data from sessions, one block per participant
- `{{research_objectives}}` — What you set out to learn
- `{{user_segments_and_counts}}` — Segment names and participant counts per segment
- `{{hypotheses}}` — Hypotheses you were testing
- `{{product_name_and_description}}` — What the product is

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Six steps, each with specific output requirements and formatting rules |
| **Structure** | 3/3 | Six steps with clear scope; insight format template embedded |
| **Reasoning Guidance** | 3/3 | Pattern taxonomy, hypothesis verdict framework, confidence calibration, segment divergence lens |
| **Output Quality** | 3/3 | Quote bank table, verdict table, ranked insight list, narrative — all specified |
| **Robustness** | 3/3 | Single-datapoint rule, scope constraint, quote vs. paraphrase distinction |
| **Total** | **15/15** | |
