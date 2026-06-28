# Hypothesis Test Notes
**Name:** Radha Manasa Peesapati  
**Date:** June 2026  
**Experiment:** New Onboarding & Activation Campaign

---

## Metric Tested
**Paid Conversion Rate** — number of users who converted to a paid plan out of total users in each group.

This metric was selected because it directly measures if the campaign achieved its goal.

---

## Hypotheses

**Null:** No improvement in conversion rate was observed in the treatment group.

**Alternate:** A higher conversion rate was observed in the treatment group.

A one-tailed test was used since the goal was to detect improvement.

---

## Numbers Used

| | Control | Treatment |
|---|---|---|
| Total Users | 690 | 710 |
| Conversions | 22 | 50 |
| Conversion Rate | 3.19% | 7.04% |

---

## Test Output

| | Value |
|---|---|
| Z-Statistic | 3.26 |
| P-Value | 0.0005 |
| Significance Level | 0.05 |
| Result | Significant — null rejected |

The p-value of 0.0005 is well below 0.05, so the difference is unlikely to be due to chance.

---

## Interpretation

A more than double conversion rate was observed in the treatment group. An increase in refund rate (0% to 0.42%) and a slight rise in support tickets were also noted. These guardrail metrics need to be reviewed before a full launch decision is made.

---

## Limitations

- Experiment was run for one time period only — results may vary across different months
- Conversion counts are still relatively small (22 vs 50) — monitoring post-launch is recommended
- Group sizes were slightly unequal (690 vs 710) — accounted for in the calculation

