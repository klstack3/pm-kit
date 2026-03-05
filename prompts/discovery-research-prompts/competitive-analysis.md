# Competitive Analysis Brief

**Category:** Discovery & Research
**Model Compatibility:** Model-agnostic (works well across Claude, GPT-4-class, and Gemini; benefits from web search capability if available)

---

## When to use

You need a structured competitive analysis for a strategy review, investor deck, PRD context section, or your own situational awareness. Works best when you already know who your competitors are and want to organize your thinking — the AI won't have perfect market data, but it's excellent at structuring analysis frameworks.

---

## The Prompt

```
You are a strategic product analyst with expertise in competitive intelligence and market analysis.

I need a competitive analysis for the following:

- **My Product:** {{your_product_and_one_line_description}}
- **Competitors to Analyze:** {{competitor_1, competitor_2, competitor_3}}
- **Market/Segment:** {{market_or_segment}}
- **Analysis Purpose:** {{what_this_analysis_is_for — e.g., "informing our Q3 roadmap", "board deck context", "evaluating a new market entry"}}

Produce the analysis in this structure:

**1. Competitive Landscape Overview (2-3 paragraphs)**
Summarize the market dynamics, key trends, and where the competitive intensity is highest.

**2. Competitor Profiles**
For each competitor, provide:
- **Positioning:** Who they serve and how they describe themselves
- **Key Strengths:** What they do better than anyone else (2-3 bullets)
- **Key Weaknesses:** Where they fall short or are vulnerable (2-3 bullets)
- **Recent Moves:** Notable product launches, pivots, or strategic shifts in the last 12 months
- **Threat Level to Us:** Low / Medium / High, with a one-sentence rationale

**3. Feature Comparison Matrix**
A markdown table comparing key capabilities across all competitors and my product. You choose the most relevant feature dimensions based on the market context.

**4. Strategic Implications for Us (3-5 bullets)**
What does this competitive landscape mean for our product strategy? Where are the gaps we can exploit? Where are we most vulnerable?

**5. Open Questions**
List 3-5 things you couldn't determine from available information that would materially change this analysis if answered.

Be direct and opinionated in your assessments. I'd rather have a wrong-but-specific take I can push back on than a hedged-but-useless one.
```

---

## Variables

- `{{your_product_and_one_line_description}}` — Your product and what it does in one sentence
- `{{competitor_1, competitor_2, competitor_3}}` — The competitors to analyze (can be more or fewer)
- `{{market_or_segment}}` — The market category (e.g., "B2B project management for mid-market")
- `{{what_this_analysis_is_for}}` — Context on why you need this and who will read it

---

## Example

**Input:**

- My Product: Loom — async video messaging for work
- Competitors: Vidyard, mmhmm, Vimeo Record
- Market: Async video communication for B2B teams
- Purpose: Informing our 2025 product strategy

**Sample output excerpt:**

> **Vidyard — Threat Level: Medium**
> Vidyard has the strongest sales-specific positioning, with deep CRM integrations that Loom lacks. However, their product is narrowly focused on sales enablement, leaving them vulnerable in the broader "async communication" space where Loom has stronger brand recognition...

---

## Tips

- **Supplement with real data.** The AI's competitive intelligence is based on training data and won't include the latest moves. Use this as a structural starting point, then validate with actual product pages, G2 reviews, and earnings calls.
- **The "Open Questions" section is the most valuable part.** It tells you what you still need to go find out — treat it as a research agenda.
- **Use the "be opinionated" instruction deliberately.** It forces the AI to take positions you can react to, rather than producing wishy-washy "it depends" analysis.
- **Run it with web search enabled if your model supports it.** This dramatically improves the "Recent Moves" section.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from prompts shared by [Adrian Raudaschl](https://breakingproduct.substack.com/p/25-prompts-for-product-managers-obsessed) (Breaking Product newsletter) and competitive analysis frameworks from [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/).

**What we changed and why:**

- **Expanded from a single SWOT table to a full brief.** Raudaschl's original produced a Company|Strengths|Weaknesses|Opportunities|Threats table. We expanded to include landscape overview, threat levels, feature matrix, strategic implications, and open questions.
- **Added the "Analysis Purpose" variable.** The original didn't account for audience or use case, which significantly affects what the analysis should emphasize.
- **Added "Open Questions" section.** Neither original asked the AI to flag gaps in its own knowledge — this is critical because competitive analysis from an AI will always be incomplete.
- **Added the "be opinionated" instruction.** Without this, AI competitive analyses tend to be balanced to the point of uselessness.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                        |
| ---------------------- | --------- | ------------------------------------------------------------------------------------------------ |
| **Specificity**        | 3/3       | Clear role, defined deliverable structure, explicit instructions for each section                |
| **Structure**          | 3/3       | Five distinct sections with defined formats; feature matrix as table                             |
| **Reasoning Guidance** | 2/3       | "Be opinionated" instruction helps, but no explicit analytical framework (e.g., Porter's) guided |
| **Output Quality**     | 3/3       | Complete brief structure with threat levels, matrix, implications, and open questions            |
| **Robustness**         | 3/3       | "Open Questions" section explicitly surfaces what the AI doesn't know                            |
| **Total**              | **14/15** |                                                                                                  |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
