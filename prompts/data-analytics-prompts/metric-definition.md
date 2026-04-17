# Metric Definition: Baseline, Target, and Leading Indicators

**Category:** Data & Analytics
**Model Compatibility:** Model-agnostic (optimized for Claude, GPT-4-class, and Gemini)

---

## When to use

You are about to launch a product upgrade or redesign and need to define the measurement framework that will tell you whether it worked. Use this before a single line of new code ships — not after.

Good for: product launches, feature releases, platform migrations, redesigns, or any initiative where you need to define success in advance and have a rollback trigger if things go wrong.

---

## The Prompt

```
You are a product analytics expert who defines measurement frameworks for product launches and redesigns. You write metric definitions precise enough to prevent arguments about whether the goal was met. You distinguish between north star metrics, secondary metrics, leading indicators, and guardrail metrics — and you know why each matters.

I need to define a complete measurement framework for a product upgrade launch.

**Inputs:**
- North star metric: {{from_north_star_vision_output}}
- Flow redesigns and their intended outcomes: {{from_flow_redesign_mapping_output}}
- Dashboard baseline data: {{from_dashboard_audit_output}}
- Launch timeline: {{when_v1_ships_and_when_full_rollout_occurs}}

---

**Step 1: Metric taxonomy**

Define the four metric types for this product in this context:
- **North star:** The single metric that captures whether users are getting core value
- **Secondary metrics:** 2–3 metrics that must move in concert with the north star for the upgrade to be considered successful
- **Leading indicators:** Metrics that will move before the north star does — early warning signals of success or failure
- **Guardrail metrics:** Metrics that must NOT decline — floors, not targets

**Step 2: Baseline and target table**

For each metric in Step 1, define:
- Current baseline value (or "unknown — needs instrumentation")
- Target value at 30, 60, and 90 days post-launch
- Target-setting rationale (why that target, not higher or lower)
- Data source and instrumentation requirement

**Step 3: Instrumentation gap analysis**

Identify every metric that cannot currently be measured and what needs to be built or configured to track it. Prioritize: which gaps must be closed before launch, and which can be closed post-launch.

**Step 4: Failure definition**

Write explicit failure conditions:
- At what value of each key metric would you declare the launch failed?
- At what value would you trigger a rollback?
- Who makes the call, and within what timeframe?

**Step 5: Weekly review cadence**

Design a weekly metric review structure for the first 90 days:
- Which metrics are reviewed weekly vs. monthly?
- What does a "green/yellow/red" threshold look like for each?
- What action does a red trigger?

**Output format:**
- Steps 1 and 2 as a master metrics table
- Step 3 as a prioritized instrumentation checklist
- Step 4 as a decision table (metric | failure threshold | rollback trigger | decision owner)
- Step 5 as a brief review protocol

**Constraints:**
- Every metric must have a precise definition — "engagement" is not a metric
- Targets must be grounded in baseline data or explicitly stated as estimates with confidence level
- The failure condition for each metric must be more specific than "if it goes down"
```

---

## Variables

- `{{north_star_metric}}` — From the North Star & Vision prompt
- `{{flow_redesign_output}}` — From the Flow Redesign Mapping prompt
- `{{dashboard_baseline}}` — From the Dashboard Audit prompt
- `{{launch_timeline}}` — When each milestone ships

---

## Evaluation

| Criteria | Score | Rationale |
|---|---|---|
| **Specificity** | 3/3 | Four metric types defined, target timeline (30/60/90), failure conditions, rollback trigger |
| **Structure** | 3/3 | Taxonomy → baseline → gaps → failure → cadence is a complete measurement lifecycle |
| **Reasoning Guidance** | 3/3 | Target-setting rationale, failure vs. rollback distinction, instrumentation prioritization |
| **Output Quality** | 3/3 | Master table, checklist, decision table, review protocol |
| **Robustness** | 3/3 | Vague metric prohibition, estimate confidence requirement, specific failure condition rule |
| **Total** | **15/15** | |
