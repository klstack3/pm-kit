# Stakeholder Interview: Question Design & Alignment Mapping

**Category:** Discovery & Research
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to design interview guides for internal stakeholder interviews as part of a product evaluation or strategy cycle. Use this before talking to engineering, design, business, or customer success leadership — when you need honest input and need to surface hidden disagreements before they become blockers.

Good for: product evaluations, roadmap planning, post-mortem preparation, org alignment work, or any situation where stakeholder misalignment is a risk to execution.

---

## The Prompt

```
You are an experienced product leader who facilitates strategic alignment conversations. You know how to surface hidden disagreements between stakeholders, expose conflicting success definitions, and create the conditions for honest input without triggering defensiveness.

I need to design interview guides for stakeholder interviews as part of a product evaluation. These are internal interviews — not user research.

**Context:**
- Product being evaluated: {{product_name_and_one_line_description}}
- Stakeholder groups to interview: {{list — e.g., "Head of Engineering, Head of Design, Business Lead, Customer Success Lead"}}
- Known tensions or disagreements (optional): {{brief_description_or_"none_known"}}
- What the evaluation will influence: {{e.g., "tech stack decision and 12-month roadmap"}}

---

**Step 1: Stakeholder objective mapping**

For each stakeholder group, write:
- What they most likely want from this product (their definition of success)
- Where their definition of success is most likely to conflict with another group's
- What they are most likely to understate or avoid saying unless specifically asked

**Step 2: Universal questions**

Write 5 questions to ask every stakeholder regardless of role. These should:
- Surface their honest assessment of what is working and what is not
- Reveal their definition of success and timeframe
- Uncover what they believe is being ignored or deprioritized
- Identify what they would do first if given full authority

**Step 3: Role-specific questions**

For each stakeholder group, write 3–4 role-specific questions that:
- Probe the domain they own (engineering asks about debt and velocity; design asks about user signal; business asks about revenue and retention impact)
- Surface their constraints and non-negotiables
- Reveal what tradeoffs they have already made and why

**Step 4: Conflict probes**

Write 3 questions specifically designed to surface hidden disagreements across stakeholders — questions where different answers from different people would reveal a misalignment that needs to be resolved before any decisions are made.

**Step 5: Synthesis setup**

After running these interviews, what would a meaningful disagreement look like? Describe 3 scenarios where stakeholder answers would directly conflict, and explain what decision that conflict would force.

**Output format:**
- Step 1 as a table (stakeholder group | likely success definition | likely blind spot | likely avoidance)
- Steps 2 and 3 as formatted interview guides with headers
- Steps 4 and 5 as narrative sections

**Constraints:**
- Questions must not be leading or signal the "right" answer
- Avoid questions that invite stakeholders to rate or score the product numerically — qualitative only
- The tone of questions should be curious and diagnostic, not evaluative
```

---

## Variables

- `{{product_name_and_description}}` — What the product is
- `{{stakeholder_groups}}` — Who you are interviewing
- `{{known_tensions}}` — Any misalignments you already know about
- `{{what_evaluation_influences}}` — What decisions these interviews feed into

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Role defined, five steps, output format explicit per section |
| **Structure** | 3/3 | Clear step progression from mapping to synthesis |
| **Reasoning Guidance** | 3/3 | Hidden disagreement framing, conflict probe logic, avoidance surfacing — all guide analytical thinking |
| **Output Quality** | 3/3 | Table, interview guides, narrative — format matched to content type |
| **Robustness** | 3/3 | Anti-leading-question rule, qualitative-only constraint, conflict scenario descriptions |
| **Total** | **15/15** | |
