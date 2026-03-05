# Market Sizing Estimator

**Category:** Discovery & Research
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You need a TAM/SAM/SOM estimate for a pitch deck, business case, PRD, or opportunity assessment. This prompt walks through the estimation step by step so you can see (and challenge) every assumption rather than getting a single unsupported number.

---

## The Prompt

```
You are a strategy consultant with expertise in market sizing and business case development. You are rigorous about showing your work and making assumptions explicit.

I need a market size estimate for the following:

- **Product/Concept:** {{product_or_concept}}
- **Target Users:** {{who_the_product_serves}}
- **Geography:** {{geographic_scope}}
- **Problem Being Solved:** {{the_core_problem}}

Walk me through a TAM/SAM/SOM estimate using the following approach:

**Step 1: Define the Market**
State clearly what market we're sizing. Define the boundaries — what's in scope and what's out.

**Step 2: TAM (Total Addressable Market)**
Estimate the total market opportunity if every potential customer adopted a solution. Use a top-down approach (industry data, total population of potential buyers × average revenue per buyer). Show every number and cite where you'd find real data to validate each one.

**Step 3: SAM (Serviceable Addressable Market)**
Narrow to the segment we can realistically serve given our product's current capabilities, positioning, and geographic reach. Explain each filter you're applying and why.

**Step 4: SOM (Serviceable Obtainable Market)**
Estimate what we could realistically capture in the first 2-3 years. Factor in competitive dynamics, go-to-market motion, and adoption rates. Be conservative and explain your reasoning.

**Step 5: Assumptions Table**
List every assumption you made in a table:
| Assumption | Value Used | Confidence (Low/Med/High) | How to Validate |

**Step 6: Sensitivity Analysis**
Identify the 2-3 assumptions that most affect the final number. Show what happens to the SOM if each one is 2x higher or 2x lower.

**Step 7: Bottom-Up Sanity Check**
Do a quick bottom-up estimate (e.g., "If we acquire X customers/month at Y ARPU, we'd hit Z ARR in 2 years") and compare it to the top-down SOM. Flag any major discrepancies.

Format all dollar figures clearly. Use ranges rather than false-precision point estimates wherever possible.
```

---

## Variables

- `{{product_or_concept}}` — What you're sizing the market for
- `{{who_the_product_serves}}` — Target customer segment
- `{{geographic_scope}}` — e.g., "US only", "Global", "EMEA"
- `{{the_core_problem}}` — The problem your product solves

---

## Example

**Input:**

- Product: AI-powered contract review tool for legal teams
- Target Users: In-house legal teams at mid-market companies (200-2000 employees)
- Geography: United States
- Problem: Contract review takes too long and misses key risk clauses

**Sample output excerpt:**

> **Step 2: TAM**
> There are approximately 30,000 companies in the US with 200-2000 employees that have in-house legal functions (source: Bureau of Labor Statistics + IBISWorld). Average legal tech spend per mid-market company is ~$50K-$150K/year. Using the midpoint ($100K):
> TAM = 30,000 × $100,000 = **$3B**
>
> _To validate: Check Gartner legal tech market reports, cross-reference with ACC (Association of Corporate Counsel) survey data on legal tech adoption._

---

## Tips

- **The assumptions table is the deliverable, not the final number.** Share it with your stakeholders so they can challenge specific assumptions rather than arguing about the bottom line.
- **Use the sensitivity analysis to know what matters.** If your SOM swings 5x based on one assumption, that's the thing you need to go validate first.
- **Supplement with real data.** The AI will generate plausible numbers, but you should replace key assumptions with real data points from industry reports, SEC filings, or customer interviews.
- **Run the bottom-up check seriously.** If your top-down SOM is $50M but your bottom-up says you'd need 10,000 enterprise customers to get there, something's wrong.

For more on writing and evaluating effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

---

## Attribution

**Inspiration:** Adapted from market sizing prompts on [LearnPrompt.org](https://learnprompt.org/chatgpt-prompts-for-product-managers/) and business case frameworks from strategy consulting practice.

**What we changed and why:**

- **Expanded from a single estimation to a 7-step methodology.** The original LearnPrompt prompt asked for TAM/SAM/SOM and data sources in a single request. We broke this into distinct steps with explicit methodology at each stage.
- **Added the assumptions table with confidence levels.** The original didn't require the AI to surface its assumptions, making the output impossible to validate or challenge.
- **Added sensitivity analysis and bottom-up sanity check.** These are standard strategy consulting practices that prevent market sizing from being a single meaningless number.
- **Added "use ranges, not point estimates" instruction.** False precision in market sizing is a common failure mode.

---

## Evaluation

| Criteria               | Score     | Rationale                                                                                                                |
| ---------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Specificity**        | 3/3       | Clear role, 7-step methodology with defined output for each step                                                         |
| **Structure**          | 3/3       | Seven distinct steps, each building on the previous; includes table format for assumptions                               |
| **Reasoning Guidance** | 3/3       | Top-down then bottom-up cross-check; sensitivity analysis on key variables; explicit assumption surfacing                |
| **Output Quality**     | 3/3       | Assumptions table with confidence levels and validation methods; ranges over point estimates                             |
| **Robustness**         | 3/3       | Sensitivity analysis handles uncertainty; bottom-up sanity check catches errors; confidence levels flag weak assumptions |
| **Total**              | **15/15** |                                                                                                                          |

> **Scoring guide:** Below 9 = not ready for the repo. 9–12 = solid, worth including. 13+ = exceptional. See our [evaluation criteria](../EVALUATION-CRITERIA.md) for details.
