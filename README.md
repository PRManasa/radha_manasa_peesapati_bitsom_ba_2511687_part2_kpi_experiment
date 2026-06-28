# Part 2: 

## Business Context
A subscription-based digital product company ran an A/B experiment to test a new onboarding and activation campaign. Users were split into Control (existing experience) and Treatment (new campaign). The objective was to improve paid conversion and early engagement.

The decision to be made was whether to launch the new experience to all users, a selected segment, or do not launch. Refund rate and support ticket volume were monitored as risk indicators.


## Dataset
**File:** campaign_experiment_data.xlsx  
**Records:** 1408 (original), 1400 (after deduplication)  
**Columns:** 16 — user ID, signup date, experiment group, region, device type, traffic source, plan type, funnel events, revenue, support tickets, refund flag, days to convert, engagement score


## North Star Metric
**Paid Conversion Rate** was selected as the primary metric because it directly measures whether the campaign achieved its revenue objective. A user visiting the landing page or starting a trial does not generate revenue — only a paid conversion does. Trial start rate and engagement score were treated as supporting metrics.


## KPI Tree
The KPI tree was created using draw.io and saved as `outputs/kpi_tree.png`.

Paid Conversion Rate breaks down into three driver areas:
- **Acquisition:** Landing page visit rate → Trial start rate → Onboarding completion rate
- **Engagement:** Engagement score, Days to convert
- **Revenue quality:** Avg revenue per converted user, Refund rate

Guardrail metrics: Refund rate, Support ticket rate, Segment-level conversion decline


## Data Preparation

| Check | Finding | Action |
|---|---|---|
| Duplicate user_ids | 8 duplicates found | First occurrence retained |
| Missing device_type | 18 rows | Retained; excluded from device segment analysis |
| Missing traffic_source | 24 rows | Retained; excluded from traffic segment analysis |
| Missing engagement_score | 14 rows | Retained; excluded from engagement averages |
| Missing days_to_convert | 1336 rows | Expected — non-converters have no conversion date |
| Invalid binary values | None found | No action required |
| Revenue outliers (>1000) | 24 rows | Retained — valid premium plan conversions |


## Experiment Analysis

All 11 required metrics were calculated for Control and Treatment groups. Segment analysis was performed across region, device type, traffic source, and plan type. Full results are in `outputs/experiment_summary.xlsx`.

Key finding: Paid conversion rate more than doubled in the treatment group (7.04% vs 3.19%).


## Hypothesis Test

| Parameter | Value |
|---|---|
| Test | One-tailed z-test for proportions |
| Metric | Paid Conversion Rate |
| Control rate | 3.19% (22/690) |
| Treatment rate | 7.04% (50/710) |
| Z-statistic | 3.26 |
| P-value | 0.0005 |
| Result | Significant — null hypothesis rejected |


## Guardrail Metrics

| Metric | Control | Treatment | Assessment |
|---|---|---|---|
| Refund Rate | 0.00% | 0.42% | Monitor post-launch |
| Support Ticket Rate | 0.22 | 0.37 | Slight increase — track weekly |
| Avg Days to Convert | 8.86 | 6.40 | Improved |


## Final Recommendation
Phased launch recommended. Start with Mobile users in North and South regions, monitor for 4 weeks, then expand to full user base if metrics remain stable.


## Assumptions and Limitations
- Group sizes slightly unequal (690 vs 710) — accounted for in z-test
- Small absolute conversion counts (22 vs 50) — post-launch monitoring needed
- Experiment ran for one cohort only — seasonal effects not controlled
- West region and Social traffic showed weak lift — excluded from initial rollout


## Screenshots

| File | Description |
|---|---|
| summary_metrics.png | Control vs Treatment summary table |
| hypothesis_test_output.png | Z-test calculation and result |
| kpi_tree_preview.png | KPI tree diagram |
