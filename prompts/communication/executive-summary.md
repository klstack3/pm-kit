# Executive Summary Condenser

**Category:** Communication
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have a long document (PRD, research report, strategy doc, analysis) and need to distill it into a crisp executive summary that a time-pressed leader can act on in under 2 minutes.

---

## The Prompt

```
You are a chief of staff who writes executive briefs for a CEO. You know that executives don't need all the detail — they need the signal, the decision, and the risk.

Condense the following document into an executive summary:

{{paste_the_full_document}}

**Summary Parameters:**
- **Target Audience:** {{who_will_read_this — e.g., "CEO", "Board", "VP of Engineering"}}
- **Desired Length:** {{word count or format — e.g., "under 250 words", "one page", "5 bullet points"}}
- **Decision Needed:** {{what_decision_does_the_reader_need_to_make — or "informational only"}}

**Structure the summary as:**

1. **Bottom Line:** One sentence — the single most important thing the reader needs to know.
2. **Context:** 2-3 sentences — why this matters now.
3. **Key Findings/Recommendations:** 3-5 bullet points — the core content, prioritized by importance to the reader.
4. **Risks:** 1-2 bullets — what could go wrong or what the reader should worry about.
5. **Decision/Ask:** What you need from the reader, stated as a clear, concrete ask. If informational only, state what the reader should do with this information (e.g., "No action needed — for awareness ahead of Q4 planning").

**Rules:**
- Never include information just because it's interesting — only include it if it affects the decision or risk assessment
- Cut all jargon unless the audience is technical
- If the original document is ambiguous on a key point, flag it rather than guessing
- Bold the single most important sentence in the entire summary
```

---

## Variables

- `{{paste_the_full_document}}` — The document to condense
- `{{who_will_read_this}}` — Target audience
- `{{word count or format}}` — Desired length
- `{{what_decision_does_the_reader_need_to_make}}` — The decision context

---

## Example

**Input:** A 2,500-word competitive analysis document, for VP of Product, decision needed on whether to accelerate feature X to counter competitor move.

**Sample output excerpt:**
> **Bottom Line:** Competitor Y launched a feature directly competitive with our core differentiator. **We have a 3-month window before their enterprise rollout to ship our advanced version and retain positioning.**
>
> **Decision:** Approve reallocating 2 engineers from Project Z to accelerate Feature X, targeting 8-week delivery vs. the current 14-week timeline.
>
> **Risk:** Pulling engineers from Project Z delays its launch by ~6 weeks, which affects the Q4 partnership commitment with [Partner].

---

## Tips

- **Specify the decision upfront.** An executive summary for "should we do this?" is very different from one for "FYI, here's what happened." The decision context shapes what to emphasize.
- **Use the "bold the most important sentence" rule.** It forces you to identify the single most critical piece of information, which is a surprisingly hard exercise.
- **Run it twice with different audiences.** An exec summary for engineering leadership will emphasize different things than one for the board. Generate both if you need both.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from executive summary prompts shared by [Sushant Kumar](https://sushantkr17.medium.com/everything-about-prompt-engineering-for-product-managers-in-2025-even-after-the-gpt-5-release-ddceee806906) (Medium) and BLUF communication principles.

**What we changed and why:**
- **Added the "Decision Needed" variable.** The original summarized documents generically. We require the user to state what decision the summary needs to support, which fundamentally changes what gets included.
- **Added the "bold the most important sentence" rule.** Forces prioritization that the original didn't require.
- **Added the ambiguity flag rule.** The original let the AI fill in gaps silently. We require it to flag when the source document is unclear.
- **Added the "informational only" path.** Not every summary leads to a decision — the original didn't handle this case.

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Clear role (chief of staff), audience-aware, decision-context-aware, explicit structure |
| **Structure** | 3/3 | Five-section format from bottom line through ask |
| **Reasoning Guidance** | 2/3 | "Only include if it affects the decision" is strong guidance; but no explicit analytical framework |
| **Output Quality** | 3/3 | Scannable, decision-oriented output with bold emphasis on the key sentence |
| **Robustness** | 3/3 | Ambiguity flagging, informational-only path, jargon-awareness |
| **Total** | **14/15** | |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.