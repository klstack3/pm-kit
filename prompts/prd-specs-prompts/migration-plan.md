# Migration Plan: Strategy, Sequencing, and Rollback

**Category:** PRD & Specs
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

Your stack decision is made and you need a migration plan before any new code is written. Use this to produce a workstream sequence, rollback protocol, and risk register — the three artifacts that separate a migration plan from a migration wish.

Good for: platform migrations, major infrastructure upgrades, legacy system replacements, or any technical initiative where sequencing and reversibility are as important as the destination.

---

## The Prompt

```
You are a senior engineering program manager and technical product lead who has managed multiple platform migrations. You plan migrations to minimize disruption, deliver user-facing value early, and preserve the ability to reverse course if something goes wrong. You know that a migration plan with no rollback is not a plan — it is a bet.

I need to produce a migration plan for a product tech stack upgrade.

**Inputs:**
- Stack decision: {{paste_tech_stack_decision_matrix_output}}
- Current stack: {{paste_technical_audit_stack_map}}
- Requirements: {{paste_requirements_definition_output}}
- Engineering team size and structure: {{describe}}
- Timeline target: {{e.g., "v1 in 5 months, full migration in 9 months"}}

---

**Step 1: Migration strategy selection**

Evaluate three migration strategies for this context:
- **Big bang:** Full replacement shipped at once
- **Strangler fig:** Incrementally replace components while old system stays live
- **Parallel run:** New and old systems run simultaneously, traffic split by feature flag or user segment

For each strategy, state the fit for this specific context (pros/cons given team size, risk tolerance, and timeline). Recommend one and justify it in 3 sentences.

**Step 2: Workstream decomposition**

Break the migration into workstreams. For each workstream:
- Name it and describe what it covers
- State its dependency relationships (what must be done before this can start)
- Estimate duration (weeks)
- Identify the owner role (not a name — a role)
- Flag whether it delivers visible user value or is infrastructure-only

**Step 3: Sequencing rationale**

Order the workstreams into a sequence. Justify the order by:
- Which workstream, if completed first, de-risks the most downstream work?
- Where is the earliest point that a user can see a meaningful improvement?
- What is the longest continuous chain of dependent workstreams (the critical path)?

**Step 4: Rollback plan**

Define rollback for each major phase:
- What triggers a rollback decision (specific observable conditions, not "if something goes wrong")
- What exactly is reversed (which components, which user traffic)
- How long a rollback takes to execute
- Who owns the rollback decision and who executes it

**Step 5: Risk register**

Produce a migration risk register with the top 6 risks. For each:
- Risk description
- Likelihood (low/medium/high)
- Impact (low/medium/high)
- Mitigation strategy
- Early warning signal (what you would observe before the risk materializes)

**Output format:**
- Step 1 as a comparison table followed by a recommendation paragraph
- Step 2 as a workstream table
- Step 3 as a Gantt-style sequence description (text-based) with critical path called out
- Step 4 as a rollback protocol per phase
- Step 5 as a risk register table

**Constraints:**
- The plan must deliver visible user value within the first 60 days — if it does not, flag this as a risk and propose how to address it
- Rollback conditions must be specific enough for an on-call engineer to evaluate at 2am
- No workstream can be marked "owner: TBD" — every workstream needs an assigned role
```

---

## Variables

- `{{tech_stack_decision_output}}` — Output from the Tech Stack Decision Matrix prompt
- `{{technical_audit_stack_map}}` — Stack map from the Technical Audit prompt
- `{{requirements_definition_output}}` — Output from the Requirements Definition prompt
- `{{team_size_and_structure}}` — Engineering team description
- `{{timeline_target}}` — When v1 and full migration need to land

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Three migration strategies compared, workstream table format, rollback specificity requirement |
| **Structure** | 3/3 | Strategy → decompose → sequence → rollback → risk is a complete migration planning flow |
| **Reasoning Guidance** | 3/3 | Critical path framing, de-risking sequence logic, 2am rollback clarity test |
| **Output Quality** | 3/3 | Comparison table, workstream table, Gantt-style sequence, rollback protocol, risk register |
| **Robustness** | 3/3 | 60-day user value requirement, specific rollback trigger rule, no TBD owner rule |
| **Total** | **15/15** | |
