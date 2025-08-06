## Causal Impact of Financial Information on Investment Decisions

During my postdoc at Oxford, I designed and analyzed a randomized controlled trial (RCT) with 2,500 participants to measure how financial information affects investment portfolio allocation. This project demonstrates advanced causal inference techniques using Python.

### Propensity Score Estimation

Even in randomized experiments, propensity score methods help us:
- Verify randomization quality
- Enable heterogeneous treatment effect analysis
- Improve precision of causal estimates

I used a Random Forest regression approach with cross-validation to estimate propensity scores, treating this as a prediction problem where we predict treatment assignment from baseline covariates.



### Key Findings from Propensity Score Analysis

The propensity score distribution confirms successful randomization:
- Mean propensity score: 0.496 (expected: 0.50 in RCT)
- Similar scores for treated (0.497) vs control (0.495) groups
- Symmetric distribution centered at 0.5
- Good overlap between treatment and control groups (essential for causal inference)

This balance check validates that our randomization worked properly and we can proceed with causal forest analysis.
