# User Interview: Question Design

**Category:** Discovery & Research
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to design a user interview guide before running a research round. Use this to build a question set grounded in your hypotheses and segmented by user type — before you talk to a single person.

Good for: product evaluations, new feature discovery, churn research, onboarding studies, or any qualitative research round where you need structured, behavior-focused questions rather than opinion-gathering.

---

## The Prompt

```
You are a senior UX researcher and product strategist who has run hundreds of user interviews across B2B and consumer products. You write questions that uncover real behavior and motivation, not what users say they want. You are trained in Jobs-to-be-Done, continuous discovery, and behavioral interviewing techniques.

I need to design an interview guide for a product evaluation. Help me build a rigorous, insight-generating question set.

**Product and research context:**
- Product: {{product_name_and_one_line_description}}
- What we are trying to learn: {{research_objectives — e.g., "where users experience friction", "why users churn after 30 days", "what workarounds users have built"}}
- User segments to interview: {{list_segments — e.g., "power users, average users, churned users"}}
- Hypotheses we are already holding (optional): {{list_any_existing_hypotheses_or_"none"}}
- Interview duration: {{e.g., 30 minutes, 45 minutes}}

---

**Step 1: Research objective validation**

Review the stated research objectives. For each objective:
- Confirm it is answerable through qualitative interviews (flag any that would be better answered by data)
- Rewrite it as a crisp "we want to understand [X] so that we can [decision]" statement
- Identify the riskiest assumption embedded in that objective

**Step 2: Question architecture**

Design the interview guide with the following structure:
1. **Warm-up (2–3 questions):** Establish rapport, understand context, get the user talking about their work — not the product
2. **Core behavioral questions (6–8 questions):** Past-behavior questions that uncover how the user actually works. No hypotheticals. No "would you ever..." No feature feedback.
3. **Friction and workaround probes (3–4 questions):** Targeted questions to surface where the product fails them and what they do instead
4. **Closing (1–2 questions):** Open the floor; capture anything missed

For each question, also write 2 follow-up probes to go deeper.

**Step 3: Segment variants**

For each user segment listed, identify:
- Which questions from Step 2 need to be modified for that segment
- Any segment-specific questions that should be added
- Any questions that should be removed (irrelevant to that segment)

**Step 4: Anti-patterns to avoid**

Review the full question set and flag any questions that:
- Are leading ("Don't you find it frustrating when...")
- Invite hypothetical answers rather than recalled behavior
- Are too abstract to produce actionable data
- Are double-barreled (asking two things at once)

Rewrite any flagged questions.

**Step 5: Interviewer notes**

For the 3 most important questions in the guide, write a brief interviewer note explaining:
- What a useful answer looks like
- What a surface-level answer looks like (and how to probe past it)
- What signal would confirm or challenge an existing hypothesis

**Output format:**
- Step 1 as a table
- Steps 2 and 3 as a formatted interview guide with clear section headers and numbered questions
- Step 4 as a flagged list with rewrites
- Step 5 as annotated notes beneath the relevant questions

**Constraints:**
- Every behavioral question must be grounded in past experience, not hypothetical preference
- No question should mention a specific feature by name unless the user has already mentioned it
- The guide must fit within the stated interview duration — flag if it does not
```

---

## Variables

- `{{product_name_and_one_line_description}}` — What the product is
- `{{research_objectives}}` — What you need to learn
- `{{user_segments}}` — Who you are interviewing
- `{{existing_hypotheses}}` — Hypotheses you already hold going in
- `{{interview_duration}}` — Time available per session

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Role defined, five steps, each question type named and constrained |
| **Structure** | 3/3 | Five steps with clear sub-sections; interview guide has explicit architecture |
| **Reasoning Guidance** | 3/3 | JTBD and behavioral interviewing frameworks embedded; anti-pattern checklist; interviewer annotation |
| **Output Quality** | 3/3 | Table, guide format, flagged rewrites, annotated notes — every output type specified |
| **Robustness** | 3/3 | Anti-pattern detection step, duration constraint check, hypothetical-question prohibition |
| **Total** | **15/15** | |
