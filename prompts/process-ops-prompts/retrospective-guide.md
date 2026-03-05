# Retrospective Facilitator

**Category:** Process & Ops
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You're running a sprint retrospective, project post-mortem, or any team reflection and want a structured format that produces actionable outcomes rather than vague complaints.

---

## The Prompt

```
You are an agile coach who runs retrospectives that teams actually look forward to. You know that the #1 failure mode of retros is producing a long list of complaints with no follow-through. Your retros always end with 1-3 specific, owned action items.

Design a retrospective for the following:

- **Team/Project:** {{team_or_project}}
- **Sprint/Period:** {{what_time_period_are_we_reflecting_on}}
- **Team Size:** {{number_of_people}}
- **Duration:** {{meeting_length}}
- **Context:** {{any_relevant_context — e.g., "we just missed a deadline", "new team members joined", "first retro for this team"}}
- **Previous Action Items:** {{action_items_from_last_retro — or "none/first retro"}}

Generate a complete retro plan:

**1. Check-In (5 min)**
A quick icebreaker or mood check appropriate for the context. Not "how are you feeling" — something specific that surfaces the team's energy level.

**2. Data Gathering (10-15 min)**
Choose a retro format appropriate for the context. Options include:
- Start/Stop/Continue (simple, good for regular sprints)
- 4Ls: Liked, Learned, Lacked, Longed For (good for end of project)
- Sailboat: Wind (accelerators), Anchors (slowing us down), Rocks (risks), Island (goal)
- Mad/Sad/Glad (good for emotionally charged periods)

Explain why you chose this format for the given context.

**3. Grouping & Voting (5-10 min)**
How to cluster themes and vote on what to discuss. Specific facilitation instructions.

**4. Discussion (15-20 min)**
For the top 2-3 themes, provide discussion prompts that go beyond "what happened?" to:
- "What's the systemic cause, not just the instance?"
- "Has this happened before? What did we try last time?"
- "What would need to change for this to never happen again?"

**5. Action Items (5-10 min)**
Rules for good retro action items:
- Maximum 3 per retro (more means none get done)
- Each must have a single owner (not "the team")
- Each must be completable before the next retro
- Each must be specific enough that you can answer "did we do this? yes/no"

**6. Check-Out (2 min)**
A quick close that reinforces psychological safety and captures the team's energy level for comparison over time.

**7. Follow-Up Plan**
How and when will action items be tracked and reviewed?

Also review the previous action items I provided and suggest how to open the retro with an accountability check on those items.
```

---

## Variables

- `{{team_or_project}}` — The team or project
- `{{what_time_period_are_we_reflecting_on}}` — The sprint or time period
- `{{number_of_people}}` — Team size
- `{{meeting_length}}` — Duration available
- `{{any_relevant_context}}` — Situational context
- `{{action_items_from_last_retro}}` — Previous retro's action items

---

## Example

**Input:**

- Team: Platform engineering (6 people)
- Sprint: Sprint 14 (2 weeks)
- Context: Just missed a release deadline due to an unexpected production incident mid-sprint
- Previous Action Items: "Improve monitoring alerts (owner: Sarah)" and "Document deployment runbook (owner: James)"

**Sample output excerpt:**

> **Format: Sailboat** — Chosen because the team just dealt with a crisis (production incident = rock they hit), and this format naturally separates what was pushing them forward from what was holding them back, while keeping the goal (island) visible.
>
> **Discussion Prompt for Top Theme:**
> "The production incident consumed 3 days of the sprint. Looking at this systemically: is our incident response process the issue, or is it that we didn't have enough slack in the sprint to absorb unexpected work? What's the root cause — and has this pattern happened before?"
>
> **Action Item Example:**
> ❌ "Improve incident response" (too vague, no owner)
> ✅ "Sarah will draft a 1-page incident response checklist and share it in #platform-eng by Friday" (specific, owned, time-bound, completable)

---

## Tips

- **Start with the previous action items.** If last retro's items didn't get done, discussing why is more valuable than generating new ones.
- **The 3-action-item max is non-negotiable.** More than 3 means none get done. If the team insists on more, they're avoiding prioritization.
- **Rotate the format.** Using the same retro format every sprint leads to diminishing returns. The AI will suggest an appropriate one based on context.
- **Use the systemic discussion prompts.** "What would need to change for this to never happen again?" prevents the retro from being a complaint session.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Original to PM-Kit, synthesized from agile coaching best practices, Esther Derby & Diana Larsen's _Agile Retrospectives_, and the Retromat tool.

**What we changed and why:** Written from scratch. Existing retro prompts ([LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/), [Breaking Product](https://breakingproduct.substack.com/p/25-prompts-for-product-managers-obsessed)) generate generic retro agendas. Our version adds context-aware format selection, previous action item accountability, systemic discussion prompts, and strict action item quality rules.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                               |
| ---------------------- | --------- | --------------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Agile coach role, seven-section retro plan with detailed requirements per section       |
| **Structure**          | 3/3       | Full retro arc from check-in through follow-up; time allocations for each section       |
| **Reasoning Guidance** | 3/3       | Format selection with rationale; systemic discussion prompts; action item quality rules |
| **Output Quality**     | 3/3       | Complete facilitation plan with examples of good vs. bad action items                   |
| **Robustness**         | 3/3       | Previous action item review, format selection based on context, follow-up plan          |
| **Total**              | **15/15** |                                                                                         |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
