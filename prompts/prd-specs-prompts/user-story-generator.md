# User Story Generator

**Category:** PRDs & Specs
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need to break a feature or epic into well-formed user stories with acceptance criteria. Works best when you have a PRD, brief, or feature description and need to decompose it into implementable units.

---

## The Prompt

```
You are a technical product manager specializing in agile development. You write user stories that development teams can pick up and implement without ambiguity.

Break the following feature into detailed user stories:

**Feature Description:**
{{feature_description}}

**Target Users:**
{{who_will_use_this}}

**Technical Context:**
{{any_relevant_technical_constraints_or_architecture_notes}}

For each user story, provide:

1. **Epic:** The high-level feature category this belongs to
2. **User Story:** "As a [user type], I want [goal] so that [benefit]"
3. **Acceptance Criteria:** Written in Given/When/Then format. Include:
   - The happy path (expected behavior)
   - At least one edge case
   - At least one error/failure scenario
4. **Dependencies:** Other stories or systems this depends on
5. **Estimation Notes:** Anything that would affect sizing (e.g., "requires new API endpoint", "UI only — no backend changes")

Apply the INVEST criteria — each story should be:
- **I**ndependent (can be built without completing other stories first, where possible)
- **N**egotiable (details can be discussed with the team)
- **V**aluable (delivers user value on its own)
- **E**stimable (team can roughly size it)
- **S**mall (completable in one sprint)
- **T**estable (acceptance criteria are unambiguous)

Flag any story that violates INVEST and explain which criterion it fails.

After generating all stories, provide:
- A suggested implementation order
- Stories that could be parallelized
- Anything you'd cut if the team needed to ship a thinner v1
```

---

## Variables

- `{{feature_description}}` — The feature to decompose (can be a PRD section, brief, or rough description)
- `{{who_will_use_this}}` — The user personas involved
- `{{any_relevant_technical_constraints_or_architecture_notes}}` — e.g., "We use React + Node.js, data lives in Postgres, auth is handled by Auth0"

---

## Example

**Input:**
- Feature: "Users can invite team members to their workspace via email"
- Target Users: Workspace admins
- Technical Context: Existing user service with REST API; no current invitation model in the database

**Sample output excerpt:**
> **Epic:** Team Management
>
> **Story 1:** As a workspace admin, I want to invite a new team member by email so that they can access our shared workspace.
>
> **Acceptance Criteria:**
> - Given I am a workspace admin, When I enter a valid email and click "Send Invite", Then an invitation email is sent and a pending invitation record is created
> - Given I enter an email that already has an account, When I click "Send Invite", Then the existing user is added directly and I see a confirmation message
> - Given the email service is unavailable, When I click "Send Invite", Then I see an error message and the invitation is queued for retry
>
> **Dependencies:** Requires invitation data model (new DB migration)
> **Estimation Notes:** Requires new API endpoint + DB migration + email template. Medium complexity.
>
> ⚠️ *INVEST flag: This story may be too large for a single sprint if the email service integration is new. Consider splitting into "Create invitation record" and "Send invitation email" as separate stories.*

---

## Tips

- **Feed it your PRD.** This prompt works best when the feature description is rich. Paste in a full PRD section rather than a one-liner.
- **The INVEST flags are the most valuable part.** They catch stories that are too big, too coupled, or untestable before your sprint planning meeting.
- **Don't skip the "thinner v1" suggestion.** It forces a conversation about MVP scope that's often skipped in story decomposition.
- **Review the Given/When/Then criteria carefully.** These become your QA test cases — make sure they're actually testable.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from the user story prompt chain in [AadiVN/designing_with_ai](https://gist.github.com/AadiVN/95b8d11efa261c40c1baba8d57b1e8b0) (GitHub Gist — 11-step PM prompt chain).

**What we changed and why:**
- **Added Given/When/Then acceptance criteria with mandatory edge cases and error scenarios.** The original generated user stories but left acceptance criteria unstructured.
- **Added INVEST criteria enforcement with violation flags.** The original mentioned INVEST but didn't ask the AI to flag violations.
- **Added implementation ordering and parallelization.** The original produced stories as a flat list. We added sequencing guidance for sprint planning.
- **Added "thinner v1" cut suggestions.** Not in the original; forces MVP scoping.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Clear role, INVEST criteria explicitly defined, structured output per story |
| **Structure** | 3/3 | Epic → Story → AC → Dependencies → Notes; plus implementation order and parallelization |
| **Reasoning Guidance** | 3/3 | INVEST enforcement, Given/When/Then format, mandatory edge case and error scenarios |
| **Output Quality** | 3/3 | Stories are sprint-ready with estimation notes, ordering, and v1 cut suggestions |
| **Robustness** | 3/3 | INVEST violation flags, error scenario requirements, and dependency mapping |
| **Total** | **15/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.