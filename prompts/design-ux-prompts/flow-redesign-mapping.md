# Flow Redesign: Current State to Target State Mapping

**Category:** Design & UX
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You are about to redesign core product flows as part of a product upgrade or tech stack migration. Use this before any design or prototyping work to map what is changing, why, and what success looks like — grounded in research, not assumptions.

Good for: product redesigns, platform migrations, feature overhauls, or any initiative where existing flows need to be evaluated and improved rather than just rebuilt.

---

## The Prompt

```
You are a principal UX designer and product strategist with experience redesigning core product flows for software products. You do not redesign for redesign's sake — every change you propose is traceable to a user insight or a product requirement. You identify where a new tech stack is an opportunity to fix broken experiences, not just re-skin them.

I need to map current-state flows to target-state flows as part of a product upgrade.

**Inputs:**
- User research insights: {{paste_user_interview_analysis_insight_statements}}
- Requirements: {{paste_requirements_definition_output}}
- Product vision: {{paste_north_star_vision_output}}
- Core flows to redesign: {{list_the_2–4_flows_most_important_to_address}}

---

**Step 1: Current state audit per flow**

For each flow listed, describe:
- The current experience step by step (based on what you know or what is described — flag gaps)
- Where users experience friction, confusion, or failure (from research insights)
- What users do instead (workarounds)
- What the current tech enables and what it forces (constraints from technical audit)

**Step 2: Target state definition**

For each flow, define the target experience:
- What the user should be able to accomplish, and in how many steps
- What the experience should feel like (emotional quality — not a mood board, a behavioral description)
- What the tech stack upgrade enables that was previously impossible
- What is explicitly NOT changing (to constrain scope)

**Step 3: Change justification**

For each change from current to target state, write a one-sentence justification that traces the change to either a user insight (cite the insight number from the analysis output) or a requirement (cite the requirement from the requirements table). If you cannot cite a source, the change should be removed.

**Step 4: Risk and prototype flags**

For each flow, flag:
- Any change that introduces new complexity the user may not expect
- Any assumption about user behavior that is not yet validated
- Any change that requires a prototype and user validation before building

**Step 5: Success metrics per flow**

For each flow, define:
- The current baseline metric (from dashboard data if available)
- The target metric for 90 days post-launch
- The leading indicator to watch weekly

**Output format:**
- Steps 1 and 2 as parallel sections per flow (current state → target state)
- Step 3 as a change log table (change | justification | source citation)
- Step 4 as a flagged list per flow
- Step 5 as a metrics table

**Constraints:**
- Do not describe UI components or visual design — this is a flow and outcome exercise, not a mockup
- Every target state change must have a justification in Step 3
- Unsourced changes must be removed, not marked "nice to have"
```

---

## Variables

- `{{user_interview_analysis_insight_statements}}` — Insight statements from the User Interview Analysis prompt
- `{{requirements_definition_output}}` — Output from the Requirements Definition prompt
- `{{north_star_vision_output}}` — Output from the North Star & Vision prompt
- `{{core_flows}}` — The 2-4 flows that most need redesign

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Five steps, change log with citation requirement, metrics format |
| **Structure** | 3/3 | Audit → target → justify → risk → measure is a complete design process |
| **Reasoning Guidance** | 3/3 | Citation requirement forces traceability; unsourced removal rule enforces discipline |
| **Output Quality** | 3/3 | Parallel current/target sections, change log table, flagged list, metrics table |
| **Robustness** | 3/3 | Prototype flags, unsourced removal rule, no UI scope creep |
| **Total** | **15/15** | |
