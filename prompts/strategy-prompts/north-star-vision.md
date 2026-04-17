# North Star & Product Vision Definition

**Category:** Strategy
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have an aligned diagnosis and need to define where the product is going before deciding how to get there. Use this to set a north star metric, a product vision, and strategic bets — all grounded in the diagnosis rather than aspiration.

Good for: product evaluations, annual planning, post-diagnosis strategy work, new PM onboarding, or any moment where the team needs a shared destination before evaluating options.

---

## The Prompt

```
You are a product strategist with experience translating diagnosed problems into clear product vision and measurable direction. You know the difference between a north star metric and a vanity metric, between a vision statement and a marketing tagline, and between a requirement and a preference.

I have completed a product diagnosis and need to define the product's north star outcome and vision for the next 12–18 months.

**Diagnosis input:**
{{paste_state_of_the_product_document}}

**Strategic context:**
- Business goal this product serves: {{e.g., "primary revenue driver", "internal efficiency tool", "customer retention lever"}}
- Competitive pressure (if relevant): {{brief_description_or_"not_applicable"}}
- Constraints: {{e.g., "team size of 6", "must not require a full rewrite", "must support mobile in 6 months"}}
- What "winning" looks like in 18 months: {{your_rough_answer — or "help me define this"}}

---

**Step 1: North star metric definition**

Propose 3 candidate north star metrics for this product. For each:
- State the metric name and definition precisely
- Explain what behavior it captures and why that behavior matters
- Identify its weakest point (what it would fail to detect if optimized for exclusively)
- State what data infrastructure is required to measure it accurately

Recommend one, with your reasoning.

**Step 2: Vision statement**

Write a product vision statement that:
- Is a single sentence
- Describes the experience the user has when the product is working perfectly — not what the product does, but what the user can accomplish
- Is specific enough to rule things out (a good vision statement tells you what NOT to build as clearly as what to build)
- Could still be true in 5 years

Write 3 alternatives and recommend one.

**Step 3: Strategic bets**

Based on the diagnosis and vision, identify 2–3 strategic bets: areas where focused investment would produce disproportionate returns. For each bet, state:
- What you are betting on and why
- What assumption underlies the bet (and how confident you are in it)
- What would cause you to abandon the bet in 6 months

**Step 4: Anti-vision**

Write an explicit "anti-vision" — 3–5 things this product will NOT try to be or do in the next 18 months. This is a tool for focusing the team and saying no.

**Output format:**
- Step 1 as a structured candidate table with recommendation
- Steps 2 and 3 as labeled sections
- Step 4 as a short, punchy list

**Constraints:**
- The vision statement must not contain the words "platform," "seamless," "world-class," "empower," or "leverage"
- Strategic bets must be specific enough that someone could disagree with them — reject anything that sounds universally agreeable
```

---

## Variables

- `{{state_of_the_product_document}}` — Output from the State of the Product prompt
- `{{business_goal}}` — What role this product plays in the business
- `{{competitive_context}}` — Relevant competitive pressure
- `{{constraints}}` — Hard limits on solutions
- `{{what_winning_looks_like}}` — Your rough 18-month definition of success

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Four steps, north star candidate framework, vision constraints, banned word list |
| **Structure** | 3/3 | Metric → vision → bets → anti-vision is a logical progression |
| **Reasoning Guidance** | 3/3 | Weakest-point test for metrics, falsifiability test for bets, anti-vision as focusing tool |
| **Output Quality** | 3/3 | Table, alternatives with recommendation, labeled sections, punchy list |
| **Robustness** | 3/3 | Banned words, "disagree with it" test for bets, measurement infrastructure requirement |
| **Total** | **15/15** | |
