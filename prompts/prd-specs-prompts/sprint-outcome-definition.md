# Sprint Outcome Definition & Velocity Tracking

**Category:** PRD & Specs
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You are starting a sprint during a migration or build phase and need to define a clear, outcome-oriented goal with measurable done criteria. Use this at the start of every sprint — not as a retrospective tool.

Good for: migration execution sprints, product build cycles, or any two-week window where the team needs a shared goal that is specific enough to evaluate at the end of the sprint without debate.

---

## The Prompt

```
You are an experienced product manager who runs sprint planning with clarity and discipline. You write sprint goals that are outcome-oriented (not task-lists), measurable within the sprint, and tied to the migration plan and product requirements. You do not confuse shipping code with delivering value.

I need to define outcomes for an upcoming sprint and set up the right tracking to know if the sprint succeeded.

**Inputs:**
- Current sprint number and date: {{sprint_number_and_start_date}}
- Migration workstream in focus this sprint: {{workstream_name_from_migration_plan}}
- Requirement(s) this sprint addresses: {{cite_requirement_IDs_from_requirements_definition}}
- What was completed last sprint: {{brief_summary_or_"first_sprint"}}
- Known blockers or risks: {{list_or_"none_identified"}}

---

**Step 1: Sprint goal**

Write a sprint goal statement that:
- Is one sentence
- Describes the outcome for the user or system (not the tasks)
- Is specific enough that any team member could say whether it was achieved at the end of the sprint
- Links to a requirement or migration workstream

Write 2 alternatives, then recommend one.

**Step 2: Outcome definition**

Define what "done" looks like for this sprint across three dimensions:
- **Functional done:** What behavior or capability exists that did not exist at sprint start?
- **Quality done:** What tests, error rates, or performance thresholds must be met?
- **Measurable done:** What metric moved, or what instrumentation was added to track the metric?

**Step 3: Blockers and dependencies**

For each known blocker or dependency:
- State what is blocked and by what
- State the resolution path and owner
- Flag whether this blocker, if unresolved, invalidates the sprint goal

**Step 4: End-of-sprint review prompt**

Write the questions this sprint's retrospective should answer. Focus on: Did we meet the goal? What slowed us down? What assumption was wrong? What do we need to carry forward?

**Output format:**
- Step 1 as labeled alternatives with recommendation
- Step 2 as a three-row table
- Step 3 as a flagged list
- Step 4 as 5–7 retro questions

**Constraints:**
- The sprint goal must not be a task list in disguise ("complete X, Y, and Z" is not a goal)
- Quality done must include at least one quantitative threshold
- If the sprint has no measurable done criteria, flag this and propose one
```

---

## Variables

- `{{sprint_number_and_start_date}}` — Which sprint and when it starts
- `{{workstream_name}}` — From the Migration Plan prompt
- `{{requirement_IDs}}` — From the Requirements Definition prompt
- `{{last_sprint_summary}}` — What shipped or was completed in the prior sprint
- `{{known_blockers}}` — Any risks or dependencies already identified

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Sprint goal format, three-dimension "done" definition, blocker resolution structure |
| **Structure** | 3/3 | Goal → done → blockers → review is a complete sprint planning unit |
| **Reasoning Guidance** | 3/3 | Task-list prohibition, measurable done requirement, blocker invalidation flag |
| **Output Quality** | 3/3 | Alternatives table, done table, flagged list, retro questions |
| **Robustness** | 3/3 | Task-list disguise check, quantitative threshold requirement, no-metric flag |
| **Total** | **15/15** | |
