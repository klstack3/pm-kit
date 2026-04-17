# Requirements Definition: User, Product, and Engineering

**Category:** PRD & Specs
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have an aligned vision and diagnosis and need to translate them into a three-layer requirements set before any design or technical work begins. Use this to define what must be true — not how to build it.

Good for: product upgrades, platform migrations, new feature development, or any initiative where UX, product, and engineering requirements need to be defined in one place and checked for conflicts before work starts.

---

## The Prompt

```
You are a senior product manager who writes requirements that are precise enough for engineering to act on and clear enough for design to visualize. You write requirements that express outcomes, not implementations. You know the difference between a requirement, a constraint, a preference, and a nice-to-have — and you enforce that distinction.

I need to define requirements across three layers to support a product upgrade and tech stack evaluation.

**Inputs:**
- Vision and north star: {{paste_north_star_vision_output}}
- Diagnosis: {{paste_state_of_the_product_document}}
- Known constraints: {{e.g., team size, timeline, budget, non-negotiable dependencies}}

---

**Step 1: Requirement tiering**

Before writing requirements, define the three tiers for this evaluation:
- **Must have at launch:** Without this, the product cannot replace its current version
- **Must have within 90 days of launch:** Needed for full parity or the core value proposition of the upgrade
- **Future / nice to have:** Valid ideas that are explicitly out of scope for now

**Step 2: User experience requirements**

Write 5–8 UX requirements grounded in user research findings. Each must:
- State the outcome required (not the feature or interaction)
- Name the user segment it serves
- Specify the success threshold (how would you know it is met?)
- Assign a tier (from Step 1)

Format: "A [user segment] must be able to [accomplish X] within [constraint], as evidenced by [measurable signal]."

**Step 3: Product capability requirements**

Write 5–8 product capability requirements — things the product must be able to do that it currently cannot, or currently does poorly. Same format and tiering as Step 2.

**Step 4: Engineering requirements**

Write 4–6 engineering requirements that define what the technical system must deliver. These should cover:
- Performance thresholds (load time, uptime, latency)
- Developer experience (deployment, testing, observability)
- Scalability ceiling required
- Security or compliance constraints (if applicable)

Each must have a measurable threshold, not a qualitative description ("fast" is not a requirement — "p95 load time under 2 seconds" is).

**Step 5: Requirement conflict detection**

Review the full requirements set and identify:
- Any two requirements that are in tension with each other
- Any requirement that would force a specific technology choice (flag it — requirements should not constrain implementation unless it is a genuine hard constraint)
- Any requirement that is actually a preference, not a requirement (remove or re-tier)

**Output format:**
- Step 1 as a brief framing statement
- Steps 2, 3, and 4 as structured tables (requirement | user segment or scope | success threshold | tier)
- Step 5 as a flagged list with resolution recommendations

**Constraints:**
- No requirement may use the word "should" — every requirement either must or will not
- Requirements must be testable — if you cannot write a test for it, it is not a requirement
- Total requirements across Steps 2–4: no more than 20
```

---

## Variables

- `{{north_star_vision_output}}` — Output from the North Star & Vision prompt
- `{{state_of_the_product_document}}` — Output from the State of the Product prompt
- `{{known_constraints}}` — Hard limits on solutions

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Requirement format template, tiering framework, 20-requirement cap, "should" prohibition |
| **Structure** | 3/3 | Five steps from tiering through conflict detection |
| **Reasoning Guidance** | 3/3 | Conflict detection, implementation-forcing flag, preference vs. requirement distinction |
| **Output Quality** | 3/3 | Structured tables for all three requirement layers, flagged list for conflicts |
| **Robustness** | 3/3 | Testability rule, "should" ban, implementation-forcing check |
| **Total** | **15/15** | |
