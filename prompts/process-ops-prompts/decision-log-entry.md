# Decision Log Entry

**Category:** Process & Ops
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You've just made a product decision and want to document it properly so future-you (and your teammates) can understand not just what was decided, but why — and under what conditions you'd revisit it.

---

## The Prompt

```
You are a senior PM who is meticulous about decision documentation. You know that the most expensive decisions are the ones that get relitigated because nobody documented the original reasoning.

I need to write a decision log entry. Here's the raw context:

{{paste_your_context — meeting notes, Slack threads, your own rough notes, whatever you have}}

**Decision Details:**
- **Decision Area:** {{what_category — e.g., "architecture", "pricing", "feature scope", "go-to-market"}}
- **Who Made the Decision:** {{the_decision_maker_and_key_stakeholders}}
- **Date:** {{date}}

Structure the decision log entry as:

**1. Decision:** One clear sentence stating what was decided.

**2. Context:** 2-3 sentences on why this decision was needed now. What triggered it?

**3. Options Considered:** For each option that was on the table:
- Description (1-2 sentences)
- Key argument for
- Key argument against
- Who championed this option (if relevant)

**4. Rationale:** Why this option was chosen over the alternatives. Be specific about the deciding factors.

**5. What We're Giving Up:** The most important trade-off. What's the cost of this decision?

**6. Revisit Conditions:** Under what circumstances should we reconsider this decision? Be specific — "if X metric drops below Y" or "if [assumption] turns out to be wrong."

**7. Action Items:** What happens next as a result of this decision?

If the raw context I provided is ambiguous about any of the above, flag it and tell me what you'd need me to clarify.
```

---

## Variables

- `{{paste_your_context}}` — Raw materials (meeting notes, Slack threads, etc.)
- `{{what_category}}` — Decision category
- `{{the_decision_maker_and_key_stakeholders}}` — Who decided
- `{{date}}` — When

---

## Example

**Input:** Rough notes from a Slack thread about whether to build a custom notification system or use a third-party service.

**Sample output excerpt:**

> **Decision:** Use Customer.io for transactional notifications; defer building custom notification infrastructure to H2.
>
> **What We're Giving Up:** Full control over delivery timing and retry logic. Customer.io's retry behavior is configurable but not as granular as a custom system.
>
> **Revisit Conditions:** If notification delivery rate drops below 99.5%, or if Customer.io's pricing exceeds $3K/month (currently ~$800/month at our volume), revisit the build decision.

---

## Tips

- **Paste in the mess.** This prompt is designed to take raw, unstructured context (Slack threads, meeting notes) and produce a clean decision record. Don't pre-organize.
- **The "Revisit Conditions" section prevents endless relitigating.** When someone says "should we reconsider this?", point them to the conditions. If they haven't been met, the answer is no.
- **"What We're Giving Up" forces honesty.** Every decision has a cost. Documenting it prevents revisionist history where the chosen path was "obvious."
- **Store these in a team-accessible location.** A decision log is only useful if people can find it. Use a shared doc, wiki, or repo.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Original to PM-Kit, synthesized from decision documentation best practices and the "Revisit Conditions" concept from Amazon's "Type 1 / Type 2 decisions" framework.

**What we changed and why:** Written from scratch. Existing decision log prompts are minimal (typically just "document this decision"). Our version adds options considered with champion attribution, explicit trade-off documentation, and revisit conditions — the three most commonly missing elements in decision records.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                        |
| ---------------------- | --------- | -------------------------------------------------------------------------------- |
| **Specificity**        | 3/3       | Clear role, seven-section structure, accepts messy raw input                     |
| **Structure**          | 3/3       | Seven sections progressing from decision through action items                    |
| **Reasoning Guidance** | 3/3       | Options with for/against arguments, explicit rationale, trade-off acknowledgment |
| **Output Quality**     | 3/3       | Complete decision record with revisit conditions and action items                |
| **Robustness**         | 3/3       | Handles messy input, flags ambiguity, revisit conditions prevent relitigating    |
| **Total**              | **15/15** |                                                                                  |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
