# Edge Case Finder

**Category:** PRDs & Specs
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have a feature spec, PRD, or design and want to stress-test it for gaps, edge cases, and scenarios your team hasn't considered. Best used before engineering handoff or design review.

---

## The Prompt

```
You are a senior QA engineer and product thinker who specializes in finding the things other people miss. Your job is to break things — to find the edge cases, race conditions, and user scenarios that will cause problems if not addressed before engineering begins.

Here is the feature spec:

{{paste_your_spec_prd_or_feature_description}}

Analyze it across these dimensions:

**1. User Edge Cases**
What happens when users do unexpected things? Consider: first-time users, power users, users with accessibility needs, users with slow connections, users who leave mid-flow and come back, users who try to game the system.

**2. Data Edge Cases**
What happens with unusual data? Consider: empty states, maximum values, special characters, unicode, extremely long inputs, null/missing values, duplicate entries, concurrent edits.

**3. Timing & State Edge Cases**
What happens with timing? Consider: race conditions, stale data, expired sessions, timezone differences, daylight saving time, actions taken during deployments, background jobs that fail.

**4. Integration Edge Cases**
What happens when external dependencies fail? Consider: API timeouts, third-party service outages, webhook delivery failures, rate limiting, auth token expiration.

**5. Business Logic Edge Cases**
What happens at the boundaries of your business rules? Consider: permission edge cases (user has partial access), billing edge cases (plan changes mid-cycle), feature flag interactions, migration from old to new behavior.

For each edge case:
- Describe the scenario in one sentence
- Rate severity: 🔴 Critical (data loss/security) / 🟡 High (broken flow) / 🟢 Low (cosmetic/minor)
- Suggest a resolution approach in one sentence

End with: "Top 5 things most likely to become production incidents if not addressed."
```

---

## Variables

- `{{paste_your_spec_prd_or_feature_description}}` — The spec, PRD, or feature description to stress-test

---

## Example

**Input:** A PRD for a collaborative document editing feature with real-time sync.

**Sample output excerpt:**
> **Timing & State Edge Cases:**
>
> 🟡 **Scenario:** Two users edit the same paragraph simultaneously, one on a slow connection. The slow user's changes arrive after the fast user's, potentially overwriting them.
> **Resolution:** Implement operational transforms or CRDTs for conflict resolution at the paragraph level.
>
> 🔴 **Scenario:** User A shares a document with User B, then immediately downgrades their plan (losing the sharing feature). User B still has the document open.
> **Resolution:** Define grace period behavior — do active sessions persist, or is access revoked immediately? This is a product decision, not just a technical one.

---

## Tips

- **Run this BEFORE your design review, not after.** Edge cases found before engineering starts are 10x cheaper to fix.
- **The "Top 5 production incidents" list is your action item.** These are the ones to add to your spec immediately.
- **Feed it the richest input possible.** A full PRD with flows and logic will produce much better edge cases than a one-paragraph summary.
- **Share the output with your engineer.** They'll add cases the AI missed based on the actual codebase, and the AI's output gives them a structured framework to think through.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Original to PM-Kit, synthesized from QA engineering best practices and common PRD failure modes observed across product teams.

**What we changed and why:** This prompt was written from scratch for PM-Kit. While several sources (including [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and [Lenny's Newsletter community](https://www.lennysnewsletter.com/)) have published "find the weaknesses" style prompts, none structured the analysis across five distinct dimensions with severity ratings and resolution suggestions. Our five-dimension framework (user, data, timing, integration, business logic) is based on common production incident categories.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Clear role (QA + product thinker), five named analysis dimensions with example considerations |
| **Structure** | 3/3 | Five distinct categories; each edge case has scenario, severity, and resolution |
| **Reasoning Guidance** | 3/3 | Each dimension includes specific sub-scenarios to consider; severity rating forces prioritization |
| **Output Quality** | 3/3 | Severity-rated edge cases with resolutions; "Top 5 production incidents" prioritizes action |
| **Robustness** | 3/3 | Covers five orthogonal failure dimensions; severity ratings prevent treating all edge cases equally |
| **Total** | **15/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.