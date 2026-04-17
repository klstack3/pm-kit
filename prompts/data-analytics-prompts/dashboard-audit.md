# Dashboard Audit: Metric Interpretation & Anomaly Detection

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You have access to a product health dashboard and want a structured read of the data before forming any hypotheses. Use this before any diagnosis, redesign, or tech decision — bad data interpretation upstream contaminates everything downstream.

Good for: product evaluations, quarterly health checks, post-launch reviews, pre-roadmap planning, or any moment where you need to translate raw metrics into a defensible picture of product health.

---

## The Prompt

```
You are a senior product analyst with deep experience reading usage dashboards for B2B and consumer software products. You interpret data without jumping to conclusions, surface anomalies clearly, and distinguish between signals that require action and noise that can be ignored.

I am going to share my product's current dashboard metrics. Analyze them and produce a structured audit report.

**Dashboard data:**
{{paste_dashboard_data_or_describe_metrics}}

**Product context:**
- Product type: {{e.g., SaaS platform, internal tooling, consumer app}}
- Primary user type: {{e.g., enterprise PMs, retail traders, knowledge workers}}
- Current phase: {{e.g., growth, maturity, post-rebrand}}
- North star metric (if defined): {{metric_name_and_current_value}}

---

**Step 1: Metric inventory**

List every metric provided. For each, state:
- What it measures in plain language
- Whether it is a leading or lagging indicator
- Whether its current value appears healthy, concerning, or unclear (and why)

**Step 2: Patterns and trends**

Identify:
- The 2-3 strongest positive signals in the data
- The 2-3 most concerning signals or declining trends
- Any metrics that appear contradictory or that create tension with each other (e.g., high activation but high churn)

**Step 3: Anomaly flagging**

Flag any metric that:
- Has an unexplained directional change in the last 30–90 days
- Is performing significantly above or below industry benchmarks (state the benchmark you are using and its source)
- Appears to be tracking the wrong thing for the stated north star

**Step 4: Measurement gap analysis**

Based on the product type and north star, identify:
- What is not being measured that should be
- Any metrics that are likely being double-counted or conflated
- Leading indicators that are absent but would give earlier warning of problems

**Step 5: Prioritized questions**

Produce a list of the 5 most important questions this data raises that need answers before a diagnosis can be formed. Frame each as a testable hypothesis, not an open-ended question.

**Output format:**
- Section headers for each step
- Metric inventory as a table
- Patterns, anomalies, and gaps as labeled bullet lists
- Hypotheses numbered and formatted as: "We believe [X] because [data signal], which we can test by [method]"

**Constraints:**
- Do not recommend solutions or fixes yet — this is a diagnostic step only
- Where data is ambiguous, say so explicitly rather than guessing
- If a metric name is unclear, ask for clarification before interpreting it
```

---

## Variables

- `{{paste_dashboard_data_or_describe_metrics}}` — Raw export, screenshot description, or metric list with values
- `{{product_type}}` — SaaS, internal tool, marketplace, etc.
- `{{primary_user_type}}` — Who the product serves
- `{{current_phase}}` — Where the product is in its lifecycle
- `{{north_star_metric}}` — The metric the product is ultimately optimizing for

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Role defined, five explicit steps, output format and constraints stated |
| **Structure** | 3/3 | Five sequential steps, each with distinct scope and output type |
| **Reasoning Guidance** | 3/3 | Hypothesis framing, leading vs. lagging distinction, anomaly detection criteria all guide reasoning |
| **Output Quality** | 3/3 | Table for inventory, labeled bullets for patterns, numbered hypothesis format |
| **Robustness** | 3/3 | Handles ambiguity explicitly, instructs AI to flag unclear metrics, constrains scope to diagnosis only |
| **Total** | **15/15** | |
