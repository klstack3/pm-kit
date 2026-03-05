# User Flow Critique

**Category:** Design & UX
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have a user flow (described in text, or you can describe screens/steps) and want it critiqued for friction, drop-off risks, and usability issues before investing in high-fidelity design or engineering.

---

## The Prompt

```
You are a senior UX designer with 10+ years of experience designing high-conversion product flows. You think in terms of cognitive load, progressive disclosure, and user motivation at each step.

Critique the following user flow:

**Flow Name:** {{flow_name}}
**Target User:** {{who_is_going_through_this_flow}}
**Goal:** {{what_the_user_is_trying_to_accomplish}}
**Context:** {{when_and_why_the_user_enters_this_flow}}

**Steps:**
{{describe_each_step_of_the_flow — can be screen descriptions, wireframe descriptions, or a numbered list of actions}}

Analyze the flow against these criteria:

1. **Friction Points:** Where will users hesitate, get confused, or drop off? For each friction point, rate the drop-off risk (High/Medium/Low) and suggest a specific fix.

2. **Cognitive Load:** Are there steps where the user is asked to make too many decisions, process too much information, or context-switch? Where could you apply progressive disclosure?

3. **Motivation Curve:** At each step, is the user's perceived value (what they're getting) keeping pace with the effort (what you're asking of them)? Where does the value/effort ratio dip?

4. **Missing States:** What happens when things go wrong? Identify missing error states, empty states, loading states, and edge cases in the flow.

5. **Accessibility:** Flag any potential accessibility issues (keyboard navigation, screen reader compatibility, color contrast, touch target size).

Provide your critique as a step-by-step walkthrough, addressing each step in the flow. End with:
- **Top 3 changes** that would have the biggest impact on conversion
- **One thing to cut** if you had to simplify the flow by one step
```

---

## Variables

- `{{flow_name}}` — e.g., "New user onboarding", "Checkout flow", "Team invitation"
- `{{who_is_going_through_this_flow}}` — The user persona
- `{{what_the_user_is_trying_to_accomplish}}` — The user's goal
- `{{when_and_why_the_user_enters_this_flow}}` — Context for entry (e.g., "After signing up via Google OAuth")
- `{{describe_each_step_of_the_flow}}` — Numbered list of screens or actions

---

## Example

**Input:**

- Flow: Free trial signup
- Target User: Marketing manager evaluating the tool
- Goal: Start a free trial and see value
- Steps: 1) Landing page → 2) Email/password form → 3) Company info form → 4) Team size selector → 5) Use case selector → 6) Dashboard (empty)

**Sample output excerpt:**

> **Step 6: Dashboard (empty) — 🔴 High drop-off risk**
>
> The user just invested effort across 5 steps and lands on... nothing. An empty dashboard is the worst possible reward for completing signup. The motivation curve has completely collapsed.
>
> _Fix: Replace the empty dashboard with a guided first-action experience. Show a single, clear CTA: "Create your first [thing]" with a pre-populated template. Reduce time-to-value to under 60 seconds._

---

## Tips

- **Describe the flow in as much detail as possible.** Include button labels, form fields, and what the user sees at each step. The more specific your input, the more specific the critique.
- **Use this before your design review.** It's much faster to iterate on a text description than on mockups.
- **Pay attention to the motivation curve analysis.** This is the most unique lens and catches the flows where users technically _can_ complete the task but emotionally _don't want to_ because the effort/reward ratio is off.
- **Don't skip accessibility.** Even a text-based critique can catch obvious issues like "Step 3 relies on color to indicate status."

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from UX critique prompts in [AadiVN/designing_with_ai](https://gist.github.com/AadiVN/95b8d11efa261c40c1baba8d57b1e8b0) (GitHub Gist) and heuristic evaluation concepts from [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/).

**What we changed and why:**

- **Added the "Motivation Curve" analysis.** Neither original included a value/effort ratio assessment at each step, which is the highest-signal indicator of where users will drop off.
- **Added missing states identification.** The originals focused on the happy path. We added error, empty, and loading state analysis.
- **Added accessibility as a standard dimension.** Not present in either original.
- **Added "one thing to cut" output.** Forces simplification thinking rather than just critique.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                  |
| ---------------------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role with expertise framing; five named critique dimensions                                          |
| **Structure**          | 3/3       | Step-by-step walkthrough format with prioritized changes and cut suggestion                                |
| **Reasoning Guidance** | 3/3       | Cognitive load, motivation curve, and progressive disclosure frameworks guide analysis                     |
| **Output Quality**     | 3/3       | Drop-off ratings, specific fixes, top 3 changes, and cut recommendation                                    |
| **Robustness**         | 3/3       | Missing states analysis covers what happens when things go wrong; accessibility catches non-obvious issues |
| **Total**              | **15/15** |                                                                                                            |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
