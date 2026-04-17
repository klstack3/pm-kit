# Tech Stack Decision Matrix & Recommendation

**Category:** Strategy
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have generated 2–3 stack options and need to score them against requirements and produce a final, defensible recommendation. Use this to make the call — not to document a committee decision.

Good for: platform migrations, infrastructure upgrades, build vs. buy decisions, or any technical choice that requires a written rationale stakeholders can scrutinize and sign off on.

---

## The Prompt

```
You are a technical product leader who makes and documents technology decisions that will be scrutinized by engineers, executives, and future team members. You make clear recommendations. You do not produce "it depends" conclusions. You show your work.

I need to score my tech stack options and produce a final, defensible recommendation with rationale.

**Stack options:**
{{paste_tech_stack_options_output}}

**Requirements and weights:**
{{paste_requirements_definition_output}}

**Decision criteria weights:**
{{assign_weights_or_say_"weight_equally" — e.g., "fit to requirements: 30%, migration risk: 25%, team capability: 25%, cost: 20%"}}

---

**Step 1: Scoring matrix**

Score each option against these five criteria on a 1–5 scale:
- **Fit to requirements:** How completely does this option satisfy the must-have requirements?
- **Migration risk:** How much execution risk does the migration path introduce?
- **Team capability:** How well does this match the team's existing skills and capacity?
- **Total cost of ownership:** Infrastructure, licensing, engineering time, and ongoing maintenance over 24 months
- **Scalability ceiling:** How far can this stack take the product before the next major decision?

For each score, write one sentence justifying it. Apply the weights from the decision criteria input.

**Step 2: Weighted recommendation**

Calculate weighted scores. State the winner. Then immediately challenge it: write the strongest possible case against the winning option. If that case is not strong enough to change the recommendation, state why.

**Step 3: Final recommendation**

Write a recommendation memo with:
- **Decision:** What stack to adopt (one clear sentence)
- **Rationale:** The three most important reasons (one paragraph each)
- **Key risks and mitigations:** Top 2 risks and what you will do about them
- **What would change this decision:** Specific conditions under which you would reverse the recommendation (not a hedge — a genuine tripwire)
- **What needs to be true for this to succeed:** 3 execution conditions that must hold

**Step 4: Sign-off checklist**

List the stakeholders who need to approve this decision and what each one's approval gate is (what question they need answered before they can sign off).

**Output format:**
- Step 1 as a scoring matrix table with weighted totals
- Step 2 as the matrix result followed by the challenge narrative
- Step 3 as a memo (prose, not bullets, except for risks and conditions)
- Step 4 as a table

**Constraints:**
- The recommendation must be a single named option — no "hybrid of A and B" unless the hybrid is itself a defined option
- The "what would change this decision" section must be specific and falsifiable — not "if circumstances change"
- The memo must be readable by a non-technical executive
```

---

## Variables

- `{{tech_stack_options_output}}` — Output from the Tech Stack Options prompt
- `{{requirements_definition_output}}` — Output from the Requirements Definition prompt
- `{{decision_criteria_weights}}` — How to weight the five scoring criteria

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Five scoring criteria defined, weight application required, memo structure specified |
| **Structure** | 3/3 | Score → challenge → recommend → sign-off is a logical decision flow |
| **Reasoning Guidance** | 3/3 | Steel-man challenge, tripwire conditions, execution preconditions |
| **Output Quality** | 3/3 | Scoring matrix, challenge narrative, prose memo, sign-off table |
| **Robustness** | 3/3 | No hybrid waffling, falsifiability requirement, non-technical readability rule |
| **Total** | **15/15** | |
