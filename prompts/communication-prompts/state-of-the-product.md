# State of the Product: Alignment Document

**Category:** Communication
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have a diagnosis and need to produce a polished alignment document the whole team can sign off on before moving to solutions. Use this to create shared understanding across functions — without triggering debate about solutions before the problem is agreed on.

Good for: product evaluations, strategy kickoffs, executive readouts, cross-functional alignment, or any moment where the team needs a single source of truth on what the product's current state actually is.

---

## The Prompt

```
You are a product director who writes with clarity and precision. You produce documents that get stakeholders aligned quickly — no padding, no hedging, no buried leads. You write for decision-makers who read fast.

I need to write a "State of the Product" alignment document based on my evaluation synthesis. This document will be shared cross-functionally and needs to create shared understanding before any decisions are made about solutions.

**Input:**
{{paste_cross_source_synthesis_output}}

**Additional context:**
- Document audience: {{list — e.g., "Engineering Lead, Head of Design, CPO, Business Lead"}}
- Decision this document is meant to enable: {{e.g., "agreement on what problems to solve before evaluating tech options"}}
- Tone required: {{e.g., "direct and urgent", "balanced and consultative", "executive-ready"}}

---

**Step 1: Document structure**

Produce the document with these sections:
1. **Headline finding** (1–2 sentences): The single most important thing the evaluation revealed
2. **What is working** (3–5 bullets): Genuine strengths, stated without spin
3. **What is not working** (organized by problem cluster — UX/product, technical, strategic): One paragraph per cluster, each starting with the clearest evidence
4. **Cost of inaction** (1 paragraph): What happens in 12 months if nothing changes
5. **What we are not solving yet** (1 paragraph): Explicitly scope out what this evaluation is not addressing, to prevent scope creep
6. **Recommended next step** (1 sentence): The single action this document is asking for

**Step 2: Headline options**

Write 3 alternative headline finding statements. Each should:
- Lead with the most important insight
- Be specific enough to be falsifiable
- Not sound like a press release

**Step 3: Readability check**

Review the document and flag:
- Any sentence over 25 words
- Any jargon that requires domain knowledge to parse
- Any section that hedges where the evidence is clear
- Any claim that lacks a source or reference to evaluation findings

**Output format:**
- The full formatted document as the primary output
- Headline options as a labeled section below
- Readability flags as an annotated list

**Constraints:**
- Total document length: 500 words maximum
- No bullet points in the "What is not working" or "Cost of inaction" sections — these must be prose
- The document must be ready to share as-is, with minimal editing needed
```

---

## Variables

- `{{cross_source_synthesis_output}}` — Output from the Cross-Source Synthesis prompt
- `{{document_audience}}` — Who will read it
- `{{decision_to_enable}}` — What agreement it is building toward
- `{{tone}}` — Communication register required

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Six-section document structure, word limit, prose requirement, three headline variants |
| **Structure** | 3/3 | Document architecture defined, readability check step, output layers clear |
| **Reasoning Guidance** | 3/3 | Cost of inaction framing, scope exclusion, falsifiability test for headlines |
| **Output Quality** | 3/3 | Full formatted doc + alternatives + flags — three output types specified |
| **Robustness** | 3/3 | Word limit, prose requirement for key sections, source-linking requirement |
| **Total** | **15/15** | |
