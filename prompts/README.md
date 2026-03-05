# 🤖 Prompt Library

Structured AI prompts for every phase of PM work. Each prompt is a standalone file — grab what you need, skip what you don't.

For how we evaluate prompt quality, see [Evaluation Criteria](./EVALUATION-CRITERIA.md).
For more on writing effective prompts, see: [Prompt Writing Best Practices]({{MEDIUM_ARTICLE_LINK}})

## How to Use

1. Find a prompt relevant to your current task
2. Copy it and fill in the `{{variable}}` placeholders with your context
3. Paste into Claude, ChatGPT, or your preferred AI tool
4. Iterate on the output — treat it as a draft, not a final answer

## Prompts

### 🔍 Discovery & Research

| Prompt | What it does | Score |
|---|---|---|
| [Customer Interview Questions](./discovery-research/customer-interview-questions.md) | Generate non-leading, Mom Test-style interview scripts with follow-up probes | 14/15 |
| [Competitive Analysis](./discovery-research/competitive-analysis.md) | Produce a structured competitive brief with threat levels, feature matrix, and strategic implications | 14/15 |
| [Market Sizing](./discovery-research/market-sizing.md) | Walk through TAM/SAM/SOM estimation with assumptions table and sensitivity analysis | 15/15 |

### 🎯 Strategy

| Prompt | What it does | Score |
|---|---|---|
| [Decision-Making Co-Pilot](./strategy/decision-making-copilot.md) | Multi-phase thinking partner for complex product decisions with decision doc output | 15/15 |
| [OKR Generator & Critic](./strategy/okr-generator.md) | Generate OKRs from strategic themes or critique existing OKRs for ambition, measurability, and gameability | 15/15 |
| [Prioritization Advisor](./strategy/prioritization-advisor.md) | Run RICE/ICE/MoSCoW with reasoning, bias checking, and uncertainty flags | 15/15 |

### 📋 PRDs & Specs

| Prompt | What it does | Score |
|---|---|---|
| [PRD Writer](./prd-specs/prd-writer.md) | Generate a comprehensive PRD from rough notes with impact sizing, guardrail metrics, and edge case narratives | 15/15 |
| [User Story Generator](./prd-specs/user-story-generator.md) | Break features into INVEST-compliant user stories with Given/When/Then acceptance criteria | 15/15 |
| [Edge Case Finder](./prd-specs/edge-case-finder.md) | Stress-test a spec across five dimensions (user, data, timing, integration, business logic) with severity ratings | 15/15 |

### 🎨 Design & UX

| Prompt | What it does | Score |
|---|---|---|
| [User Flow Critique](./design-ux/user-flow-critique.md) | Critique a flow for friction, cognitive load, and motivation curve with specific fixes | 15/15 |
| [Microcopy Writer](./design-ux/microcopy-writer.md) | Generate UI text with three options, rationale, and recommendations | 13/15 |
| [A/B Test Hypothesis](./design-ux/ab-test-hypothesis.md) | Design a complete experiment with hypothesis, metrics, pre-registration checks, and decision framework | 15/15 |

### 📊 Data & Analytics

| Prompt | What it does | Score |
|---|---|---|
| [Metric Definition Helper](./data-analytics/metric-definition-helper.md) | Precisely define a metric with calculation, edge cases, interpretation guide, and known pitfalls | 15/15 |
| [Experiment Design](./data-analytics/experiment-design.md) | Full statistical experiment design with sample size math, analysis plan, and risk mitigations | 15/15 |
| [Funnel Analysis](./data-analytics/funnel-analysis.md) | Interpret funnel data with step-by-step diagnosis, leverage math, and segmentation hypotheses | 15/15 |

### 💬 Communication

| Prompt | What it does | Score |
|---|---|---|
| [Stakeholder Update](./communication/stakeholder-update.md) | Write concise BLUF-style status updates with prominent asks | 13/15 |
| [Executive Summary](./communication/executive-summary.md) | Condense long documents into decision-oriented executive briefs | 14/15 |
| [Meeting Agenda Builder](./communication/meeting-agenda-builder.md) | Build focused agendas with Info/Discussion/Decision typing and clear outcomes | 13/15 |

### ⚙️ Process & Ops

| Prompt | What it does | Score |
|---|---|---|
| [Retrospective Facilitator](./process-ops/retrospective-guide.md) | Design context-aware retros with format selection, systemic discussion prompts, and action item quality rules | 15/15 |
| [RACI Generator](./process-ops/raci-generator.md) | Build RACI matrices with accountability gap analysis, escalation paths, and review questions | 15/15 |
| [Decision Log Entry](./process-ops/decision-log-entry.md) | Document decisions with options considered, trade-offs, and revisit conditions | 15/15 |

---

## Contributing

Have a prompt that works well for you? PRs welcome — follow the format in any existing prompt file and review our [Evaluation Criteria](./EVALUATION-CRITERIA.md) before submitting.
