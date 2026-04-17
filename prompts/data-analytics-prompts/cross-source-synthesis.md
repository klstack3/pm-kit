# Cross-Source Synthesis: Building the Diagnosis

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have completed a research phase — dashboard audit, technical audit, user interviews, and stakeholder interviews — and need to synthesize findings across all sources into a single, defensible diagnosis. Use this before any solution work begins.

Good for: product evaluations, strategy cycles, post-research readouts, or any situation where you need to triangulate across quantitative data, qualitative research, and technical input.

---

## The Prompt

```
You are a senior product strategist who specializes in synthesizing mixed evidence — quantitative usage data, qualitative research, and technical assessments — into a clear, defensible product diagnosis. You do not let any single source dominate. You call out where sources conflict and require reconciliation.

I have completed a product evaluation research phase. I need you to synthesize the findings across all sources into a unified diagnosis.

**Research inputs:**

Dashboard audit findings:
{{paste_dashboard_audit_output}}

Technical audit findings:
{{paste_technical_audit_output}}

User research insights:
{{paste_user_interview_analysis_output}}

Stakeholder interview synthesis:
{{paste_stakeholder_interview_summary}}

---

**Step 1: Cross-source validation**

For each major finding from any source, check:
- Is it confirmed by at least one other source, or is it an isolated signal?
- Does any other source contradict it?
- Is it a root cause or a symptom of something deeper?

Produce a validation table: Finding | Source(s) | Corroborated by | Contradicted by | Root cause or symptom?

**Step 2: Problem clustering**

Group all validated findings into three buckets:
- **UX/product problems:** Friction, missing capability, confusing flows, poor outcomes
- **Technical problems:** Performance, reliability, developer velocity, scalability ceiling
- **Strategic gaps:** Areas where the product cannot compete or grow given current state

For each cluster, write a 2–3 sentence summary of what the cluster represents.

**Step 3: Diagnosis statement**

Write a single-page "state of the product" narrative that:
- Opens with the most important finding (lead with the headline, not the methodology)
- Covers all three problem clusters
- Names the 1–2 things the product does genuinely well
- States clearly what will happen if nothing changes (the cost of inaction)
- Is written for a cross-functional audience — no jargon, no hedging

**Step 4: Confidence map**

For each major finding in the diagnosis, rate confidence as high, medium, or low. State what evidence would move a medium to high.

**Step 5: Alignment risks**

Based on the stakeholder input, identify the 2–3 findings in this diagnosis most likely to be contested. For each, anticipate the objection and write a one-sentence response grounded in evidence.

**Output format:**
- Step 1 as a validation table
- Step 2 as three labeled cluster sections
- Step 3 as a prose narrative (no bullets, no headers within the narrative — it should read as a memo)
- Steps 4 and 5 as structured tables

**Constraints:**
- The diagnosis must be grounded in evidence — no assertion without a source
- Do not include solution recommendations yet
- The narrative in Step 3 must be under 400 words
```

---

## Variables

- `{{dashboard_audit_output}}` — Output from the Dashboard Audit prompt
- `{{technical_audit_output}}` — Output from the Technical Audit prompt
- `{{user_interview_analysis_output}}` — Output from the User Interview Analysis prompt
- `{{stakeholder_interview_summary}}` — Output from the Stakeholder Interview Design prompt

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Five steps, explicit formats, diagnosis narrative word limit, cross-source validation rule |
| **Structure** | 3/3 | Steps progress from raw validation to polished narrative to risk assessment |
| **Reasoning Guidance** | 3/3 | Root cause vs. symptom distinction, corroboration logic, cost of inaction framing |
| **Output Quality** | 3/3 | Validation table, cluster sections, prose memo, confidence table, risk table — all specified |
| **Robustness** | 3/3 | Confidence rating, objection anticipation, scope constraint on solutions |
| **Total** | **15/15** | |
