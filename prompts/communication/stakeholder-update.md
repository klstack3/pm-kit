# Stakeholder Update Writer

**Category:** Communication
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to write a status update email, Slack message, or brief for leadership, cross-functional partners, or your team. This prompt generates concise, well-structured updates that respect your audience's time.

---

## The Prompt

```
You are a senior PM who writes the kind of stakeholder updates that people actually read. You know that the #1 failure mode of status updates is being too long and burying the important information.

Write a stakeholder update with the following:

- **Audience:** {{who_is_receiving_this — e.g., "VP of Engineering and Product leads", "cross-functional team", "board of directors"}}
- **Project/Product:** {{project_or_product_name}}
- **Format:** {{email / Slack message / brief document}}
- **Cadence:** {{weekly / biweekly / monthly / one-time}}

**Content to include:**
- **Status:** {{on track / at risk / blocked — with one-sentence explanation}}
- **Key accomplishments since last update:** {{2-3 bullet points of what got done}}
- **Upcoming milestones:** {{what's coming next and when}}
- **Risks/Blockers:** {{anything that could derail the timeline — be specific about what you need}}
- **Asks:** {{any decisions, resources, or support you need from this audience}}

**Writing rules:**
- Lead with the most important information (BLUF — Bottom Line Up Front)
- Total length: under 200 words for Slack, under 300 words for email
- Use bold for scannable key points
- If there are asks, make them impossible to miss
- Never use filler phrases like "I wanted to give you an update on..." — just start with the update
- Match the formality level to the audience
```

---

## Variables

- `{{who_is_receiving_this}}` — Your audience
- `{{project_or_product_name}}` — The project
- `{{email / Slack message / brief document}}` — Format
- `{{weekly / biweekly / monthly / one-time}}` — Cadence
- `{{on track / at risk / blocked}}` — Current status with explanation
- `{{2-3 bullet points}}` — Recent accomplishments
- `{{what's coming next}}` — Upcoming milestones
- `{{anything that could derail}}` — Risks and blockers
- `{{decisions, resources, or support}}` — Asks from the audience

---

## Example

**Input:**
- Audience: VP of Product, weekly sync
- Project: Onboarding redesign
- Format: Slack
- Status: At risk — design review delayed by 3 days
- Accomplishments: User research complete (12 interviews), wireframes for steps 1-3 done
- Upcoming: Design review (rescheduled to Thursday), eng estimation next week
- Risks: If design review slips again, eng start pushes to week 4 (only 3 weeks to launch)
- Asks: Need VP sign-off on reduced scope option if timeline is at risk

**Sample output:**
> **Onboarding Redesign — At Risk** ⚠️
>
> Design review slipped 3 days (rescheduled to Thursday). If it slips again, eng start pushes to week 4, leaving only 3 weeks to launch.
>
> **Done:** User research complete (12 interviews), wireframes for steps 1-3 done.
> **Next:** Design review Thursday → eng estimation next week.
>
> **Need from you:** If timeline stays at risk after Thursday, I'll bring a reduced-scope option for your sign-off by Friday EOD.

---

## Tips

- **Write the asks first, then work backward.** If you don't need anything from the audience, question whether you need to send the update at all.
- **The word count constraint is intentional.** If you can't fit your update in 200-300 words, you're probably including too much detail. Link to a doc for supporting info.
- **Use this weekly and build a template.** After generating one or two, you'll internalize the structure and can write them faster without the prompt.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from stakeholder update prompts on [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and BLUF communication principles from military briefing formats.

**What we changed and why:**
- **Added strict word count constraints.** The original had no length limits, which is the primary failure mode of status updates.
- **Added explicit writing rules.** BLUF, bold for scanning, no filler phrases — these enforce conciseness that the original didn't require.
- **Added the "Asks" as a first-class section.** The original buried action items. We make them prominent and required.
- **Added format-specific guidance.** Slack vs. email have different norms. The original was format-agnostic.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Clear role, audience-aware, format-specific constraints, word count limits |
| **Structure** | 3/3 | BLUF format with status → done → next → asks; format-appropriate length |
| **Reasoning Guidance** | 2/3 | Writing rules enforce good communication; but no analytical framework — this is a drafting prompt |
| **Output Quality** | 3/3 | Concise, scannable output with prominent asks |
| **Robustness** | 2/3 | Format and audience flexibility; but doesn't ask clarifying questions or handle ambiguity |
| **Total** | **13/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.