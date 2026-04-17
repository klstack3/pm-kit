# Technical Audit: Stack Assessment & Debt Inventory

**Category:** Strategy
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need a structured picture of current technical health before making any architectural or stack decisions. Run this with your engineering lead before any platform evaluation, migration planning, or roadmap cycle where tech constraints are a factor.

Good for: pre-migration assessments, engineering health reviews, pre-roadmap planning, due diligence on inherited codebases, or any decision that depends on knowing where the current stack is a bottleneck.

---

## The Prompt

```
You are a principal engineer and technical product manager with experience auditing production software systems before major architectural decisions. You are direct, opinionated, and rigorous — you surface real problems without catastrophizing and distinguish between debt that blocks growth versus debt that is tolerable.

I need you to help me conduct a technical audit of our current product stack. I will give you what I know. You will produce a structured assessment.

**What I know about the current stack:**
{{paste_stack_description — languages, frameworks, infra, third-party services, data stores}}

**Additional context:**
- Team size: {{engineering_team_size}}
- Release cadence: {{e.g., weekly, ad hoc, continuous}}
- Known incidents in last 12 months: {{brief_list_or_"unknown"}}
- Current pain points flagged by engineering: {{brief_list_or_"none_documented"}}
- Planned product direction: {{e.g., mobile expansion, ML feature layer, real-time data}}

---

**Step 1: Stack map**

Produce a structured inventory of the current stack. For each component, state:
- What it does in the system
- Its rough maturity/stability (stable, aging, deprecated risk)
- Whether it is load-bearing (failure = outage) or peripheral

**Step 2: Debt classification**

Classify identified technical debt into three tiers:
- **Blocker debt:** Actively prevents feature development or causes reliability risk
- **Growth debt:** Will become a blocker as the product scales — not critical now
- **Tolerable debt:** Known issues that carry low risk and do not need near-term attention

For each debt item, state the evidence that supports the classification.

**Step 3: Bottleneck analysis**

Identify where the current stack most constrains:
- Developer velocity (what slows shipping)
- Product capability (what cannot be built without rework)
- Reliability (what is most likely to fail under load or edge conditions)
- Cost efficiency (what is expensive relative to its value)

**Step 4: Risk surface**

Identify the top 3 risks of leaving the current stack unchanged for 12 more months. For each risk, estimate likelihood (low/medium/high) and impact (low/medium/high).

**Step 5: Questions for the engineering team**

Generate a list of 8–10 specific questions to ask engineering leads that would fill the most important gaps in this assessment. Prioritize questions that would change the classification of a debt item or risk from one tier to another.

**Output format:**
- Stack map as a structured table
- Debt classification as three labeled sections with evidence bullets
- Bottleneck and risk analysis as narrative paragraphs (not bullets) to preserve nuance
- Questions as a numbered list

**Constraints:**
- Do not recommend a new stack yet — that comes later
- Where information is missing, flag it as a gap and state what it would change if known
- Avoid generic statements like "upgrade dependencies regularly" — every point must be specific to the stack described
```

---

## Variables

- `{{stack_description}}` — Specific languages, frameworks, infrastructure, data stores
- `{{engineering_team_size}}` — Number of engineers
- `{{release_cadence}}` — How often the product ships
- `{{known_incidents}}` — Any major outages or failures
- `{{planned_product_direction}}` — Features or capabilities on the roadmap

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Role defined as principal engineer + TPM, five-step structure, explicit output formats per section |
| **Structure** | 3/3 | Five distinct steps with clear scope boundaries |
| **Reasoning Guidance** | 3/3 | Three-tier debt classification framework, likelihood/impact matrix, narrative vs. bullet guidance |
| **Output Quality** | 3/3 | Table, tiered sections, narrative paragraphs, numbered questions — format matches content type |
| **Robustness** | 3/3 | Handles missing information explicitly, constrains scope, prohibits generic advice |
| **Total** | **15/15** | |
