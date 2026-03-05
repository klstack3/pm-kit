# Customer Interview Questions Generator

**Category:** Discovery & Research
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You're planning customer interviews and need non-leading, insight-generating questions. Works for discovery sprints, usability research, churn investigations, or any scenario where you need to understand user behavior and motivation without biasing the conversation.

---

## The Prompt

```
You are a senior user researcher with deep expertise in qualitative research methods and the Mom Test (the principle that you should ask about the customer's life, not your idea — from Rob Fitzpatrick's book).

I'm planning customer interviews for the following context:

- **Product/Feature:** {{product_or_feature}}
- **Research Goal:** {{what_you_want_to_learn}}
- **Target Users:** {{who_you_are_interviewing}}
- **Known Assumptions:** {{what_you_currently_believe_to_be_true}}

Generate a structured interview script with the following sections:

1. **Warm-up Questions (2-3):** Build rapport, understand their role/context. No product mentions yet.
2. **Behavioral Questions (5-7):** Ask about their actual past behavior, not hypotheticals. Every question should be grounded in specific, real events ("Tell me about the last time you..."). Never ask "Would you use...?" or "Do you think...?"
3. **Problem Exploration (3-5):** Dig into pain points, workarounds, and unmet needs. Use follow-up probes like "Walk me through exactly how you handle that today" and "What happens when that goes wrong?"
4. **Closing Questions (2-3):** Open-ended prompts that surface things you didn't think to ask about. Include "What should I have asked you that I didn't?"

For each question, include:
- The question itself
- A brief note on what signal you're listening for in the answer
- One follow-up probe to go deeper

Do NOT include any questions that:
- Lead the user toward a specific answer
- Ask about future behavior or hypothetical scenarios
- Mention the product by name in a way that biases the response
- Can be answered with just "yes" or "no"
```

---

## Variables

- `{{product_or_feature}}` — The product, feature, or area you're researching
- `{{what_you_want_to_learn}}` — Your core research question (e.g., "Why are users churning after week 2?")
- `{{who_you_are_interviewing}}` — Description of interviewees (e.g., "Power users who've been active 6+ months")
- `{{what_you_currently_believe_to_be_true}}` — Your existing assumptions to be tested

---

## Example

**Input:**

- Product/Feature: Project management tool's new timeline view
- Research Goal: Understand how PMs currently plan and track project timelines
- Target Users: Product managers at companies with 50-200 employees
- Known Assumptions: We believe PMs find Gantt charts too rigid and want something more flexible

**Sample output question:**

> "Tell me about the last project where the timeline changed significantly after you'd already planned it. Walk me through what happened and how you adjusted."
>
> _Signal: How they adapt to change — do they rebuild from scratch, patch, or have a system? Are they frustrated or resigned?_
>
> _Follow-up: "What tool or method did you use to communicate that change to your team?"_

---

## Tips

- **Run this before, not instead of, talking to your team.** Share the generated script with your research partner or PM lead for gut-check before using it live.
- **The "Known Assumptions" variable is the most important one.** The better you articulate what you currently believe, the better the AI can generate questions that test those beliefs.
- **Edit ruthlessly.** The AI will generate more questions than you need. A 30-minute interview supports 8-12 questions max. Pick the ones that map most directly to your research goal.
- **Pair with a note-taking template.** Use the "signal" notes as a lightweight coding framework during the interview.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from prompts shared by [Adrian Raudaschl](https://breakingproduct.substack.com/p/25-prompts-for-product-managers-obsessed) (Breaking Product newsletter) and customer interview frameworks from [Juma.ai/Team-GPT](https://juma.ai/blog/chatgpt-prompts-for-product-managers).

**What we changed and why:**

- **Combined two separate prompts into one structured script.** Raudaschl's original was a single-line prompt referencing the Mom Test. Juma's was a collaborative planning prompt. We merged the best of both into a full script generator with sections, signals, and follow-ups.
- **Added the "Known Assumptions" variable.** Neither original prompted the user to state their assumptions, which is critical for generating questions that actually challenge existing beliefs.
- **Added anti-pattern constraints.** We explicitly tell the AI what NOT to generate (leading questions, yes/no questions, hypotheticals) to prevent common interview script failures.
- **Added signal notes and follow-up probes.** The originals only generated questions. We added researcher guidance for each question to make the output immediately usable in a live interview.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                          |
| ---------------------- | --------- | ------------------------------------------------------------------------------------------------------------------ |
| **Specificity**        | 3/3       | Defines role (senior user researcher), task (generate interview script), methodology (Mom Test), and anti-patterns |
| **Structure**          | 3/3       | Four clear sections with distinct purposes; each question includes the question, signal, and follow-up             |
| **Reasoning Guidance** | 3/3       | Grounds questions in past behavior, prohibits hypotheticals, requires follow-up probes                             |
| **Output Quality**     | 3/3       | Script format with sections, signals, and probes is immediately usable                                             |
| **Robustness**         | 2/3       | Strong constraints on what not to generate, but doesn't ask clarifying questions before producing output           |
| **Total**              | **14/15** |                                                                                                                    |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
