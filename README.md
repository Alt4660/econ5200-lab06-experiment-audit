
# Experiment Design Audit — Power, Selection & Weighting

## Objective
I audited an underpowered A/B test and a biased wellness-program comparison, and fixed both using power analysis and inverse probability weighting.

## Methodology
- Ran a power analysis on an A/B test that gave a new onboarding flow to 2% of users (1,000 treatment users), using Cohen's h and statsmodels.
- Wrote my own `power_check` function from the power formula and checked it against statsmodels.
- Simulated a voluntary wellness program where healthier employees were more likely to join, then compared the naive estimate to the known true effect of -$500.
- Estimated propensity scores with logistic regression and used inverse probability weighting to correct the comparison.
- Simulated a biased online poll and computed Meng's data defect correlation and the effective sample size.

## Key Findings
- The A/B test had only 19.8% power to detect a 0.8pp lift. To reach 80% power, it needed 12,514 users per group.
- The same 50,000 users split evenly would have had 97.7% power.
- The naive wellness-program estimate was -$1,396 against a true effect of -$500, because healthier people chose to join.
- Inverse probability weighting brought the estimate to -$522.
- In the poll, 389,090 biased responses were worth about 140 random ones.
