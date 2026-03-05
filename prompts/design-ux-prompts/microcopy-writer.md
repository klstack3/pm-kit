# Microcopy Writer

**Category:** Design & UX
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need UI text — button labels, error messages, empty states, tooltips, confirmation dialogs, onboarding copy, or any in-product text. This prompt generates options with rationale so you can make informed choices rather than just picking the first suggestion.

---

## The Prompt

```
You are a senior UX writer who specializes in product microcopy. You understand that every word in a UI is a design decision — it affects comprehension, trust, and conversion.

Generate microcopy for the following:

- **Product:** {{product_name_and_brief_description}}
- **Component:** {{what_ui_element_needs_copy — e.g., "error message when payment fails", "empty state for dashboard", "tooltip for advanced setting"}}
- **User Context:** {{what_the_user_is_doing_when_they_see_this}}
- **Tone:** {{desired_tone — e.g., "professional and reassuring", "casual and friendly", "minimal and direct"}}

For each piece of copy, provide:
1. **Three options** ranging from concise to descriptive
2. **Rationale** for each option (what it optimizes for — clarity, warmth, urgency, etc.)
3. **Recommendation** — which option you'd ship and why

Apply these UX writing principles:
- **Clarity over cleverness.** Users scan, they don't read.
- **Action-oriented.** Tell users what to do, not what went wrong.
- **Consistent terminology.** Use the same word for the same concept every time.
- **Frontload the important word.** Put the key information at the beginning of the string.

If the component is an **error message**, always include:
- What happened (in plain language)
- What the user can do about it
- A non-blame framing (never "you did X wrong")

If the component is an **empty state**, always include:
- What will eventually be here
- How to get started
- A reason to be optimistic (value proposition)
```

---

## Variables

- `{{product_name_and_brief_description}}` — Your product and what it does
- `{{what_ui_element_needs_copy}}` — The specific component
- `{{what_the_user_is_doing_when_they_see_this}}` — User context
- `{{desired_tone}}` — The voice/tone to use

---

## Example

**Input:**

- Product: Aura — a meditation app for beginners
- Component: Empty state for "My Sessions" page (user hasn't meditated yet)
- User Context: New user exploring the app after signup
- Tone: Warm, encouraging, not preachy

**Sample output excerpt:**

> **Option 1 (Concise):**
> "Your sessions will appear here. Start your first one?"
> _Rationale: Minimal, clear, action-oriented. Best for users who just want to get going._
>
> **Option 2 (Descriptive):**
> "You haven't started any sessions yet — and that's perfectly okay. When you're ready, your first session takes just 3 minutes."
> _Rationale: Warm, removes pressure, sets low-effort expectation. Best for anxious beginners._
>
> **Option 3 (Value-forward):**
> "This is where your meditation journey lives. Each session you complete shows up here so you can see how far you've come. Ready to begin?"
> _Rationale: Paints a picture of future value. Best for users who are motivated by progress tracking._
>
> **Recommendation:** Option 2. For a beginner meditation app, reducing anxiety is more important than creating urgency. The "3 minutes" detail lowers the activation energy.

---

## Tips

- **Generate copy for all states of a component at once.** If you're writing an empty state, also ask for the loading state and error state of the same component to ensure consistency.
- **Include your style guide constraints.** If you have max character counts, forbidden words, or capitalization rules, add them to the prompt.
- **Use the rationale to make team decisions.** When your team debates copy options, the rationale makes the trade-offs explicit rather than subjective.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from microcopy prompts on [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and UX writing principles from the UX Writing Hub community.

**What we changed and why:**

- **Added the three-option-with-rationale format.** The original generated a single set of copy. We require three options with explicit trade-offs to support team decision-making.
- **Added specific rules for error messages and empty states.** These are the most common microcopy requests and have well-established best practices that the original didn't enforce.
- **Added UX writing principles as explicit constraints.** The original relied on the AI's general knowledge. We surface the principles so the output is auditable against them.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                     |
| ---------------------- | --------- | ------------------------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role, component types, UX writing principles as constraints                                             |
| **Structure**          | 3/3       | Three options + rationale + recommendation for each component                                                 |
| **Reasoning Guidance** | 2/3       | UX principles provided; component-specific rules for errors and empty states; but no explicit reasoning chain |
| **Output Quality**     | 3/3       | Multiple options with trade-offs; recommendation with justification                                           |
| **Robustness**         | 2/3       | Error and empty state rules handle common cases; but doesn't ask for style guide constraints upfront          |
| **Total**              | **13/15** |                                                                                                               |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
