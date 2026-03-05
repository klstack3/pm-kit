# RACI Matrix Generator

**Category:** Process & Ops
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You're kicking off a cross-functional initiative and need to clarify who is Responsible, Accountable, Consulted, and Informed for each workstream. Works for product launches, org changes, platform migrations, or any project involving multiple teams.

---

## The Prompt

```
You are a program manager who specializes in cross-functional coordination. You know that most cross-functional failures happen because of unclear ownership, not incompetence.

Build a RACI matrix for the following initiative:

- **Initiative:** {{initiative_name_and_description}}
- **Teams/Roles Involved:** {{list_all_teams_and_key_roles}}
- **Key Workstreams or Deliverables:** {{list_the_major_workstreams — or say "you suggest them based on the initiative"}}
- **Timeline:** {{high_level_timeline}}
- **Known Tensions:** {{any_areas_where_ownership_is_unclear_or_contested — or "none"}}

Generate:

**1. RACI Matrix**
A markdown table with workstreams as rows and roles as columns. Each cell contains R, A, C, I, or — (not involved).

Rules:
- Every row must have exactly ONE "A" (single point of accountability)
- Every row must have at least one "R" (someone doing the work)
- "A" and "R" can be the same person, but flag when they're not
- Minimize "C" — too many consulted people slows everything down

**2. Accountability Gaps**
Flag any workstream where:
- There's no obvious single accountable person
- The A and R are on different teams (coordination risk)
- There are more than 2 people in "C" (consultation bottleneck)

**3. Escalation Paths**
For each major workstream, define: if this workstream is blocked or behind, who makes the call?

**4. RACI Review Questions**
Generate 5 questions to ask the team during RACI review to surface hidden disagreements (e.g., "Does the [Role] agree they're accountable for [Workstream]? What would they need to succeed?")
```

---

## Variables

- `{{initiative_name_and_description}}` — The initiative
- `{{list_all_teams_and_key_roles}}` — Everyone involved
- `{{list_the_major_workstreams}}` — Workstreams to assign (or let the AI suggest)
- `{{high_level_timeline}}` — Timeline context
- `{{any_areas_where_ownership_is_unclear_or_contested}}` — Known tensions

---

## Example

**Input:**
- Initiative: Launch new enterprise SSO feature
- Teams: Product (PM), Engineering (2 backend, 1 frontend), Security, Sales Engineering, Documentation, Customer Success
- Workstreams: Let AI suggest
- Timeline: 8 weeks
- Tensions: Security and Engineering disagree on who owns the auth architecture decision

**Sample output excerpt:**
> | Workstream | PM | Backend Eng | Frontend Eng | Security | Sales Eng | Docs | CS |
> |---|---|---|---|---|---|---|---|
> | Auth architecture decision | C | R | — | **A** | C | — | — |
> | API implementation | C | **A/R** | — | C | — | — | — |
> | Admin UI | C | — | **A/R** | — | C | I | — |
> | Security review & pen test | I | C | — | **A/R** | — | — | — |
> | Customer documentation | C | C | — | — | — | **A/R** | I |
> | Sales enablement | C | — | — | — | **A/R** | C | C |
>
> ⚠️ **Accountability Gap:** Auth architecture decision has Security as A and Backend Eng as R. These are on different teams — high coordination risk. Recommend a joint kickoff meeting in week 1 with a written decision doc due by end of week 2.

---

## Tips

- **The "Known Tensions" variable is the most important one.** If you already know where ownership is contested, name it. The AI will address it directly in the matrix and flag it in the gaps analysis.
- **Review the RACI with the team, don't just distribute it.** The review questions in Section 4 are designed to surface disagreements in a structured way.
- **Fewer Cs is better.** Every "Consulted" person is a potential blocker. Challenge each one.
- **Update the RACI at the midpoint.** Ownership often shifts as projects evolve. Re-run this prompt with updated context at the halfway mark.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Original to PM-Kit, based on standard RACI methodology and program management best practices.

**What we changed and why:** Written from scratch. Existing RACI prompts (from [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and others) generate basic matrices without accountability gap analysis, escalation paths, or review questions. Our version adds the analytical layers that make a RACI actually useful rather than a checkbox exercise.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Program manager role, four-section output, explicit RACI rules (single A, minimize C) |
| **Structure** | 3/3 | Matrix table + gap analysis + escalation + review questions |
| **Reasoning Guidance** | 3/3 | Rules for valid RACI, gap detection criteria, review questions that surface disagreements |
| **Output Quality** | 3/3 | Formatted matrix with flags, escalation paths, and facilitation questions |
| **Robustness** | 3/3 | Known tensions as input, gap analysis, and review questions all handle ambiguity |
| **Total** | **15/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.