# Meeting Agenda Builder

**Category:** Communication
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to create a focused meeting agenda with clear outcomes. Works for any recurring or one-off meeting: sprint planning, design reviews, stakeholder syncs, strategy sessions, or 1:1s.

---

## The Prompt

```
You are a senior PM who runs meetings that people don't hate. You know that a good meeting has a clear purpose, defined outcomes, and ends early when possible.

Build a meeting agenda for the following:

- **Meeting Type:** {{type — e.g., "sprint planning", "design review", "stakeholder sync", "strategy brainstorm"}}
- **Duration:** {{length_in_minutes}}
- **Attendees:** {{who_is_in_the_room_and_their_roles}}
- **Goal:** {{the_single_most_important_outcome_of_this_meeting}}
- **Context:** {{any_background — e.g., "we're 2 weeks from launch", "there's disagreement on approach X"}}

Generate an agenda that includes:

1. **Meeting Purpose (1 sentence):** Why are we here? What's the outcome we need?

2. **Pre-Read/Pre-Work:** What should attendees review or prepare BEFORE the meeting? Be specific — link-level specific.

3. **Agenda Items:** For each item:
   - Topic name
   - Time allocation (minutes)
   - Owner (who leads this section)
   - Type: 🔵 Information (one-way share) / 🟡 Discussion (need input) / 🔴 Decision (need a call)
   - Desired output (what do we leave this section with?)

4. **Parking Lot Rules:** How will off-topic items be captured and handled?

5. **Meeting Hygiene:**
   - Who takes notes?
   - How are action items captured and followed up?
   - What's the "end early" trigger? (If we achieve the goal before time's up, we stop.)

Apply these principles:
- Decisions first, discussions second, information last
- No agenda item without an owner
- No meeting without a defined outcome
- If it can be an email/Slack message, say so
```

---

## Variables

- `{{type}}` — Meeting type
- `{{length_in_minutes}}` — Duration
- `{{who_is_in_the_room_and_their_roles}}` — Attendees with roles
- `{{the_single_most_important_outcome_of_this_meeting}}` — The meeting's purpose
- `{{any_background}}` — Relevant context

---

## Example

**Input:**

- Type: Design review
- Duration: 45 minutes
- Attendees: PM (me), lead designer, 2 engineers, design director (approver)
- Goal: Get design director approval on the onboarding wireframes
- Context: We've iterated 3 times based on user testing. This should be the final review.

**Sample output excerpt:**

> **Meeting Purpose:** Get design director approval on onboarding wireframes (v3) to unblock engineering start.
>
> **Pre-Read:** Review wireframes in Figma [link]. Focus on steps 2-4 where the biggest changes from v2 are.
>
> | #   | Topic                                              | Time   | Owner    | Type           | Output                                                 |
> | --- | -------------------------------------------------- | ------ | -------- | -------------- | ------------------------------------------------------ |
> | 1   | Decision: Approve wireframes v3                    | 20 min | Designer | 🔴 Decision    | Approved / approved with changes / needs another round |
> | 2   | Discussion: Open question on step 4 error handling | 10 min | PM       | 🟡 Discussion  | Agreed approach to error states                        |
> | 3   | Information: Eng estimation timeline               | 5 min  | Lead Eng | 🔵 Information | Shared estimate, questions noted                       |
> | —   | Buffer                                             | 10 min | —        | —              | Overflow or end early                                  |

---

## Tips

- **If the AI says "this could be an email," listen to it.** If the meeting goal is purely informational, consider whether you actually need a meeting.
- **The color-coded types (🔵🟡🔴) are the key innovation.** They set expectations for each agenda item — attendees know whether they're listening, contributing, or deciding.
- **Always include buffer time.** Meetings that run over are worse than meetings that end early.
- **Share the agenda 24+ hours before the meeting.** The pre-read only works if people have time to do it.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from meeting facilitation prompts on [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and meeting design principles from _The Surprising Science of Meetings_ by Steven Rogelberg.

**What we changed and why:**

- **Added the Information/Discussion/Decision type system.** The original generated topic lists without distinguishing what type of engagement each item needs.
- **Added pre-work requirements.** The original didn't address meeting preparation, which is essential for productive meetings.
- **Added meeting hygiene section.** Notes, action items, and end-early triggers aren't in any original prompt.
- **Added the "could be an email" principle.** Forces the AI to question whether the meeting should exist at all.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                |
| ---------------------- | --------- | -------------------------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role, meeting type awareness, explicit agenda item format with owners and types                    |
| **Structure**          | 3/3       | Purpose → pre-read → agenda table → parking lot → hygiene; table format for agenda items                 |
| **Reasoning Guidance** | 2/3       | Good meeting principles embedded; type system guides engagement; but no explicit facilitation strategies |
| **Output Quality**     | 3/3       | Table format with owners, times, types, and outputs; immediately usable                                  |
| **Robustness**         | 2/3       | "Could be an email" check and buffer time handle common failures; but doesn't handle conflict scenarios  |
| **Total**              | **13/15** |                                                                                                          |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
