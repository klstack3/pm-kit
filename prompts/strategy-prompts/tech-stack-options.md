# Tech Stack Options Generation

**Category:** Strategy
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have a defined requirements set and need to generate realistic tech stack options before scoring them. Use this to produce 2–3 grounded options — not a wishlist — before any decision matrix work.

Good for: platform migrations, greenfield builds, major infrastructure upgrades, or any technical decision where options need to be generated rigorously before being evaluated.

---

## The Prompt

```
You are a principal engineer and technical advisor who has led multiple platform migrations. You generate stack options based on requirements and constraints — not based on what is trendy. You know that the best stack is the one the team can execute and maintain, not the most technically impressive one.

I need to generate 2–3 realistic tech stack options for a product upgrade. Each option must be grounded in the requirements defined for this product.

**Requirements input:**
{{paste_requirements_definition_output}}

**Current stack:**
{{paste_technical_audit_stack_map}}

**Team context:**
- Engineering team size: {{number}}
- Current tech familiarity: {{list_of_languages_and_frameworks_team_knows_well}}
- Appetite for migration risk: {{low/medium/high — and why}}
- Timeline target for upgrade: {{e.g., "v1 in 6 months", "incremental over 12 months"}}

---

**Step 1: Constraint extraction**

From the requirements, extract the hard constraints that any stack must satisfy. List them. These are non-negotiable filters — a stack that fails one of these is eliminated regardless of its other merits.

**Step 2: Option generation**

Generate 2–3 stack options. For each option, provide:
- **Name / label:** A short descriptor (e.g., "Incremental modernization," "Full rebuild on [X]," "Hybrid with [Y] layer")
- **Core components:** Frontend, backend, data layer, infrastructure, key third-party services
- **Migration approach:** How you get from current to this stack (strangler fig, big bang, parallel run)
- **What it solves well:** Which requirements it addresses most cleanly
- **What it does not solve:** Which requirements require compromise or workarounds
- **Team ramp time estimate:** Honest assessment of how long the team needs before it is productive in this stack

**Step 3: Constraint compliance check**

For each option, run it against the hard constraints from Step 1. Mark each constraint as: met, partially met, or not met. Any option with a "not met" is disqualified unless a specific exception is justified.

**Step 4: Risk profile**

For each surviving option, state the top 3 risks specific to that stack and migration path. Assign likelihood and impact (low/medium/high).

**Step 5: Recommendation framing**

Do not make a final recommendation yet — that comes after scoring. Instead, frame the decision by stating:
- The single most important tradeoff between the options
- The question that, if answered, would make the best option obvious
- Any option that appears dominant and why it is not a clear winner despite that

**Output format:**
- Step 1 as a bulleted constraint list
- Step 2 as structured option cards (one section per option)
- Steps 3 and 4 as tables
- Step 5 as a short narrative

**Constraints:**
- Do not generate an option you would not genuinely recommend — this is not a straw man exercise
- Every option must be achievable by the stated team within the stated timeline
- Avoid options that exist only as thought experiments
```

---

## Variables

- `{{requirements_definition_output}}` — Output from the Requirements Definition prompt
- `{{technical_audit_stack_map}}` — Stack map from the Technical Audit prompt
- `{{engineering_team_size}}` — Number of engineers
- `{{tech_familiarity}}` — Languages and frameworks the team knows well
- `{{migration_risk_appetite}}` — Low/medium/high with rationale
- `{{timeline_target}}` — When v1 and full migration need to land

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Option card structure defined, constraint compliance format, risk matrix |
| **Structure** | 3/3 | Five steps from constraint extraction to decision framing |
| **Reasoning Guidance** | 3/3 | Hard constraint filter, dominant-option skepticism, decision-forcing question |
| **Output Quality** | 3/3 | Option cards, compliance table, risk table, narrative |
| **Robustness** | 3/3 | No straw man rule, achievability requirement, team ramp time requirement |
| **Total** | **15/15** | |
