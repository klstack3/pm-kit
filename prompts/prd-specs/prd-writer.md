# PRD Writer

**Category:** PRDs & Specs
**Model Compatibility:** Model-agnostic (optimized for Claude and GPT-4-class; works with Gemini)

---

## When to use

You need to write a Product Requirements Document from a brief, problem statement, or rough notes. This prompt generates a comprehensive PRD that a designer or engineer could pick up and start working from with minimal clarifying questions.

---

## The Prompt

```
You are an expert writer of Product Requirements Documents with deep product strategy, UX, and business sense. You're confident this feature will work and you write with conviction, not hedging.

Your task: Draft a complete PRD based on the information I provide. Make targeted assumptions where I don't specify details, and make best guesses based on what I do specify. After the draft, share the questions you'd want answered to make it even better.

**Context:**
{{paste_your_brief_notes_problem_statement_or_rough_context}}

**PRD Structure:**

1. **Problem (1-2 sentences):** What problem are we solving, and what evidence do we have that it's real?

2. **High Level Approach:** How are we solving it, in plain language?

3. **Narrative:** Write 2-3 short hypothetical customer stories that illustrate the problem and solution. Include at least one edge case scenario where the solution might break down.

4. **Goals:**
   - Measurable goals (with specific numbers where possible)
   - Immeasurable goals (qualitative outcomes we care about)
   - Prioritize them (P0, P1, P2)

5. **Metrics:**
   - North Star metric (the one number that tells us we succeeded)
   - Secondary metrics (2-3 supporting indicators)
   - Guardrail metrics (things that must NOT get worse, with specific thresholds for what "unacceptable" means)

6. **Impact Sizing Model:** Walk through the calculation steps for how this feature impacts the North Star metric. Show your math.

7. **Non-goals:** What are we explicitly NOT doing, and why?

8. **Key Features:** Describe the plan of record (what we're building now) and future considerations (what we might build later).

9. **Key Flows:** Describe the user experience screen by screen. Be detailed and opinionated about the UX.

10. **Key Logic:** Rules, edge cases, and conditional behavior. What happens when things go wrong?

11. **Launch Plan:** Phases with graduation criteria for moving to the next phase. Format as a table.

12. **Key Milestones:** Major deliverables with target dates. Format as a table.

13. **Open Questions:** Your questions for me — what would you need to know to make this PRD airtight?
```

---

## Variables

- `{{paste_your_brief_notes_problem_statement_or_rough_context}}` — Anything you have: a Slack thread, meeting notes, a one-liner, rough bullet points. The messier the input, the more assumptions the AI will make (and flag).

---

## Example

**Input:**

> We're getting a lot of churn from users who sign up for our analytics product but never set up their first dashboard. Activation rate is 23%. We think a guided onboarding wizard could help, but we're not sure what steps to include. We have 2 engineers and a designer available. Target launch is 6 weeks.

**Sample output excerpt:**

> **Problem:** 77% of new signups never activate (set up first dashboard), leading to early churn. Support tickets indicate users find the initial setup "overwhelming" and "don't know where to start."
>
> **North Star Metric:** 7-day activation rate (% of new users who create their first dashboard within 7 days)
> **Guardrail:** Support ticket volume during first 7 days must not increase by more than 10%
>
> **Impact Sizing:** Current activation: 23%. If wizard improves activation by 50% relative (conservative based on industry benchmarks for guided onboarding), new rate = 34.5%. With ~2,000 signups/month, that's ~230 additional activated users/month...

---

## Tips

- **Paste in everything you have.** Meeting notes, Slack threads, user research quotes, data screenshots — the AI can synthesize messy inputs into structured output. Don't pre-organize.
- **The "Open Questions" section is your feedback loop.** Share these back with your team before considering the PRD final.
- **Use guardrail metrics seriously.** "Things that must not get worse" is the most commonly skipped section in PRDs. It prevents the scenario where you improve activation but tank retention.
- **Run a second pass.** After generating the PRD, paste it back and ask: "Critique this PRD. What's missing, what's weak, and what would an engineer ask about on day one?"

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Original author:** [Aakash Gupta](https://www.news.aakashg.com/p/chatgpt-for-pms) (Product Growth newsletter, 100K+ subscribers). Additional inspiration from the [ChatPRD](https://www.chatprd.ai/lenny) system prompt by Claire Vo (CPO, LaunchDarkly).

**What we changed and why:**

- **Consolidated two sources into one prompt.** Aakash's original focused on structure and impact sizing. ChatPRD's focused on narrative and UX detail. We merged the strongest sections from each.
- **Added guardrail metrics with explicit thresholds.** Neither original required defining what "unacceptable regression" looks like — just that guardrails exist.
- **Added edge case narratives.** ChatPRD's narrative section asked for customer stories. We added the requirement to include at least one scenario where the solution breaks down, forcing the AI to think adversarially.
- **Made the prompt model-agnostic.** ChatPRD was built as a GPT system prompt. We rewrote it as a standalone prompt that works anywhere.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                   |
| ---------------------- | --------- | ----------------------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Expert role, conviction-based writing style, 13-section PRD template with detailed requirements per section |
| **Structure**          | 3/3       | 13 defined sections covering problem through launch; tables for milestones and launch phases                |
| **Reasoning Guidance** | 3/3       | Impact sizing with math; edge case narratives; guardrail thresholds force quantitative thinking             |
| **Output Quality**     | 3/3       | Detailed enough for eng/design handoff; includes open questions for self-improvement                        |
| **Robustness**         | 3/3       | Makes assumptions explicit; generates its own questions; edge case scenarios test the solution              |
| **Total**              | **15/15** |                                                                                                             |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
