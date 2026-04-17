# Prompt Evaluator

**Category:** Meta / Contributing
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You've written a prompt and want to evaluate its quality before submitting it to PM-Kit, sharing it with your team, or putting it into production use. This prompt applies the PM-Kit evaluation rubric and provides a score, detailed feedback, and a rewritten version that addresses any weaknesses.

---

## The Prompt

```
You are a prompt engineering expert who evaluates and improves AI prompts. You are rigorous, specific, and constructive — you don't just flag problems, you fix them.

I'm going to give you a prompt I've written. Evaluate it against the following rubric, then help me improve it.

**The prompt to evaluate:**

{{paste_your_prompt_here}}

**Context (optional but helps):**
- **What PM task is this for?** {{the_task_this_prompt_supports}}
- **Who will use this prompt?** {{target_user — e.g., "senior PMs", "new PMs", "cross-functional teams"}}
- **What model will it run on?** {{target_model — e.g., "Claude", "GPT-4", "any/agnostic"}}

---

**Step 1: Score the prompt**

Rate it 1-3 on each of these five criteria:

| Criteria | 1 (Weak) | 2 (Adequate) | 3 (Strong) |
|---|---|---|---|
| **Specificity** | Vague task, no role or success criteria | Task is clear but role or deliverable is implicit | Role, task, and success criteria are all explicitly defined |
| **Structure** | Unstructured wall of text | Some organization but no clear sections | Well-organized with distinct phases, sections, or step sequencing |
| **Reasoning Guidance** | No guidance on how the AI should think | Some direction (e.g., "think step by step") | Multiple reasoning techniques (chain-of-thought, frameworks, devil's advocate, etc.) |
| **Output Quality** | No format specified, no examples | Format mentioned but no examples or template | Format specified with a template or concrete example of expected output |
| **Robustness** | No handling of ambiguity or edge cases | Some acknowledgment of uncertainty | Actively asks clarifying questions, surfaces risks, handles edge cases |

For each criterion, provide:
- The score (1, 2, or 3)
- One sentence explaining why
- One specific suggestion to improve it (even if it scored 3 — there's always a way to push further)

**Step 2: Identify anti-patterns**

Check the prompt for these common failure modes:
- **Keyword dumping:** Long instruction lists without prioritization
- **Hidden constraints:** Expecting format or scope without stating it
- **Context dumping:** Massive input with no "what matters most" guidance
- **Conflicting goals:** Asking for "short" AND "comprehensive" simultaneously
- **Missing role:** No persona or expertise level defined for the AI
- **No output spec:** Leaving the format entirely up to the AI
- **One-shot assumption:** No self-check, verification step, or iteration loop

Flag any that apply, with a specific quote from the prompt that demonstrates the issue.

**Step 3: Rewrite the prompt**

Produce an improved version that:
- Addresses every weakness identified in Steps 1 and 2
- Preserves the original intent and use case
- Follows this structure (adapt as needed):
  1. Role definition
  2. Context/input section
  3. Task with explicit steps or phases
  4. Output format specification
  5. Constraints and edge case handling
  6. Self-check or verification instruction

**Step 4: Before/After comparison**

Show a brief side-by-side summary:
- What the original prompt would likely produce (1-2 sentences)
- What the improved prompt would likely produce (1-2 sentences)
- The single biggest improvement and why it matters

**Step 5: Final score**

Re-score the rewritten prompt using the same rubric. Show the before and after scores in a comparison table.
```

---

## Variables

- `{{paste_your_prompt_here}}` — The prompt you want evaluated
- `{{the_task_this_prompt_supports}}` — (Optional) What PM task the prompt is for
- `{{target_user}}` — (Optional) Who will use this prompt
- `{{target_model}}` — (Optional) What model it's designed for

---

## Example

**Input:**

> Prompt to evaluate: "Write me a PRD for a new onboarding flow. Make it detailed and include metrics."

**Sample output excerpt:**

> **Step 1: Scoring**
>
> | Criteria           | Score    | Why                                                                     | How to improve                                                                                                                                           |
> | ------------------ | -------- | ----------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
> | Specificity        | 1/3      | No role defined, "detailed" is subjective, no success criteria          | Define the AI's role (e.g., "expert PRD writer"), specify what "detailed" means (which sections, what depth), and state what a successful PRD looks like |
> | Structure          | 1/3      | Single sentence, no sections or sequencing                              | Break into sections: problem statement, goals, metrics, flows, edge cases, launch plan                                                                   |
> | Reasoning Guidance | 1/3      | No guidance on how to approach the task                                 | Add methodology: "Start with the problem, then propose metrics, then describe flows screen by screen"                                                    |
> | Output Quality     | 1/3      | "Include metrics" but no format, no examples, no metric types specified | Specify: "Include a north star metric, 2-3 secondary metrics, and guardrail metrics with thresholds"                                                     |
> | Robustness         | 1/3      | No handling of missing information or ambiguity                         | Add: "Where I haven't provided details, make your best assumption and flag it as an open question"                                                       |
> | **Total**          | **5/15** |                                                                         |                                                                                                                                                          |
>
> **Step 2: Anti-patterns detected**
>
> - ❌ **Missing role:** No persona defined — the AI doesn't know if it should write like a junior PM or a CPO.
> - ❌ **Hidden constraints:** "Detailed" implies a format expectation that isn't stated.
> - ❌ **No output spec:** No section structure, length guidance, or template.
> - ❌ **One-shot assumption:** No self-check or "flag your questions" step.
>
> **Step 5: Score comparison**
>
> | Criteria           | Before   | After     |
> | ------------------ | -------- | --------- |
> | Specificity        | 1        | 3         |
> | Structure          | 1        | 3         |
> | Reasoning Guidance | 1        | 3         |
> | Output Quality     | 1        | 3         |
> | Robustness         | 1        | 3         |
> | **Total**          | **5/15** | **15/15** |

---

## Tips

- **Use this before submitting a prompt to PM-Kit.** The evaluation criteria match our repo's scoring rubric exactly, so you'll know your score before you open a PR.
- **Use this on prompts you use at work too.** Even prompts you're not contributing to PM-Kit benefit from a structured quality check.
- **Pay the most attention to Step 2 (anti-patterns).** The scoring tells you where you are; the anti-patterns tell you what's specifically wrong.
- **The rewrite is a starting point, not a final answer.** The AI's rewrite will be structurally better, but you'll need to add your domain-specific context back in.
- **Run it iteratively.** Evaluate → rewrite → evaluate the rewrite. Two passes usually gets you to 13+.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Original to PM-Kit.** This prompt synthesizes our evaluation criteria (derived from the [Reveriano Rubric](https://medium.com/@reveriano.francisco/from-art-to-engineering-a-practical-rubric-for-gpt-4-1-prompt-design-e4cc9f9d55de), [COSTAR framework](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41/), and [PromptBuilder 2026 anti-patterns](https://promptbuilder.cc/blog/prompt-engineering-best-practices-2026)) into a self-service evaluation tool.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                                                                |
| ---------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role (prompt engineering expert), five-step evaluation process, explicit rubric with scoring definitions                                           |
| **Structure**          | 3/3       | Five distinct steps from scoring through comparison; rubric table is embedded directly                                                                   |
| **Reasoning Guidance** | 3/3       | Anti-pattern checklist, before/after comparison, and iterative rewrite all guide analytical thinking                                                     |
| **Output Quality**     | 3/3       | Score table + anti-patterns + rewrite + comparison + final re-score — complete evaluation package                                                        |
| **Robustness**         | 3/3       | Anti-pattern detection catches common failures; before/after comparison validates improvement; optional context variables handle varying levels of input |
| **Total**              | **15/15** |                                                                                                                                                          |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
