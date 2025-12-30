
# Financial Decision-Making: An Experimental Study with Causal ML

## Overview

This project combines experimental methods (RCT) with causal machine learning to understand how information interventions affect investment decisions, and crucially, *for whom* they work best.

**Why this matters for industry:** 

The methodology presented here translates directly to personalization, targeting optimization, and intervention design in any field where behavior change is the goal. It achieves this by focusing on three core pillars:

* **Running clean experiments** to establish clear causal links.
* **Estimating heterogeneous treatment effects** to understand how impacts vary across different groups.
* **Identifying high-response segments** to ensure resources are directed where they will have the greatest influence.

By moving away from "one-size-fits-all" approaches, organizations can use these techniques to create more precise, data-driven strategies that maximize impact and efficiency.

---

## What I Did

### Phase 1: Randomized Experiment

Designed and fielded a randomized controlled trial (N=2,568) testing whether a financial literacy intervention affects ETF investment decisions.

| Design Element | Details |
|----------------|---------|
| Sample Size | 2,568 participants (powered for 5% MDE) |
| Randomization | 50/50 split with stratification |
| Treatment | Targeted financial information intervention |
| Control | Standard information interface |
| Incentive Structure | Lottery-based with real financial stakes |
| Primary Metric | % allocation to ETF products |

**Result:** 18 percentage point increase in ETF allocation among treated group.

---

### Phase 2: Heterogeneity Analysis with Causal Forests

Rather than stopping at the average effect, I used EconML's CausalForestDML to estimate individual-level treatment effects and identify who responds most.

#### Model Development

- **Algorithm:** EconML's CausalForestDML
- **Validation:** 5-fold cross-validation with stratification
- **Tuning:** Hyperparameter grid search (9 configurations)
- **Scoring:** Custom function balancing heterogeneity detection (40%) and precision (60%)

#### Optimal Model Configuration

| Parameter | Value |
|-----------|-------|
| Trees | 4,000 |
| Min samples per leaf | 20 |
| Sampling rate | 45% |
| Feature selection | sqrt |

#### Features Used

20+ customer features across three categories:

- **Behavioral:** risk tolerance, financial knowledge, investment experience
- **Demographic:** age, education, income
- **Psychographic:** trust indices, political orientation

---

## Key Findings

Treatment effects varied substantially (8–27% range), with clear segment patterns:

### High Responders (20–27% effect)
- Lower financial confidence
- Age 60+
- Lower socioeconomic background
- Risk-averse profiles

### Medium Responders (15–20% effect)
- Moderate financial knowledge
- Middle-aged (40–60)

### Low Responders (8–15% effect)
- Already financially confident
- High risk tolerance

**Implication:** If you're deploying an intervention with a cost, these segments tell you where to focus resources for maximum impact.


---

## Technical Stack

### Statistical Methods
- Randomized Controlled Trials (RCT)
- Causal Inference (ATE, CATE)
- Regression Analysis (OLS, Interaction Effects)
- Propensity Score Methods

### Machine Learning
- Causal Forests (EconML)
- Hyperparameter Tuning
- Cross-Validation Strategies
- Feature Importance Analysis
- Policy Learning / Decision Trees

### Programming & Tools
- **Languages:** Python
- **Libraries:** econml, scikit-learn, pandas, numpy, matplotlib, seaborn, plotly
- **Version Control:** Git/GitHub
- **Documentation:** Jupyter Notebooks, Markdown

---

## Limitations & Context

- This was an academic study with lottery-based incentives, not a deployed business intervention
- External validity to real brokerage settings would require field testing
- The methodology, however, is directly applicable to industry A/B testing and personalization

---
## Contact

Feel free to reach out on moawad.jad@gmail.com if you have questions about the methodology or want to discuss applications.



