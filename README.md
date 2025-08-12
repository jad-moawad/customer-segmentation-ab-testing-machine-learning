dasdad<<<<<<< HEAD
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
=======
# 🎯 Business Problem
Financial services companies struggle with low adoption rates of profitable investment products, 
particularly among key demographic segments (women, younger customers, lower-income groups). 
This project demonstrates how data science can drive 18% adoption increases while reducing 
demographic disparities by 75-100%.

# 💡 Solution Approach
A two-phase data science project combining:
1. **A/B Testing**: Randomized controlled experiment (N=2,568) testing targeted information interventions
2. **Machine Learning**: Causal Forest analysis to identify customer segments for personalized targeting

# 🚀 Key Results
- **18% increase** in ETF adoption through optimized information delivery
- **Eliminated gender gap** in investment product adoption (306% reduction in gap)
- **Machine Learning model identified** 4 key customer segments with differential responses (8-27% effect range)
- **$X million potential revenue impact** for a medium-sized brokerage (you can calculate this)



## **Part 1: A/B Testing: Information Design for Product Adoption

### Business Context
- **Industry Challenge**: Only 27% of retail investors use ETFs despite superior risk-adjusted returns
- **Revenue Opportunity**: Each 1% increase in ETF adoption = $X in AUM growth
- **Target KPI**: Increase ETF allocation in customer portfolios

### Experimental Design
- **Sample Size**: 2,568 users (powered for 5% minimum detectable effect)
- **Randomization**: 50/50 split with stratification
- **Treatment**: Targeted product comparison interface
- **Control**: Standard product selection interface
- **Primary Metric**: % allocation to ETF products
- **Secondary Metrics**: Allocation shifts from low-yield products


## **Part 2: Machine Learning for Personalization**

## ML-Driven Customer Segmentation with Causal Forests for Personalized Marketing

### Business Objective
Identify which customers respond best to financial education interventions 
to optimize marketing spend and personalization strategies.

### Technical Implementation

#### 1. Causal Forest Model Development

# Technologies used:
- grf (Generalized Random Forests) package
- 5-fold cross-validation with stratification
- Hyperparameter grid search (9 configurations)
- Custom scoring function balancing heterogeneity detection (40%) and precision (60%)

# Optimal Model Configuration:
- Trees: 4,000
- Min samples per leaf: 20
- Sampling rate: 45%
- Feature selection: Adaptive


#### 2. Feature Engineering & Selection

* 20+ customer features including:
    * **Behavioral:** risk tolerance, financial knowledge
    * **Demographic:** age, education, income
    * **Psychographic:** trust indices, political orientation
* Automated feature importance extraction
* Dimensionality reduction for interpretability

#### 3. Customer Segmentation Results

### **High-Response Segments** (20-27% effect):

* Low financial confidence and Age 60+
* Lower socioeconomic background and Risk-averse
* **Business Insight:** Target these segments first for 1.5x ROI

### **Medium-Response Segments** (15-20% effect):

* Moderate financial knowledge
* Middle-aged (40-60)

### **Low-Response Segments** (8-15% effect):

* High financial confidence
* High risk tolerance
* **Business Insight:** Require different intervention strategies


## 🛠️ Technical Stack

### Statistical Methods
- Randomized Controlled Trials (RCT)
- Causal Inference (Average Treatment Effects, CATE)
- Regression Analysis (OLS, Interaction Effects)
- Multiple Testing Corrections
- Propensity Score Methods

### Machine Learning
- Causal Forests (grf)
- Hyperparameter Tuning
- Cross-Validation Strategies
- Feature Importance Analysis
- Policy Learning/Decision Trees

### Programming & Tools
- **Languages**: Python/R (for analysis), SQL (for data prep)
- **Libraries**: grf, scikit-learn, pandas, numpy, matplotlib, seaborn
- **Statistical**: statsmodels, scipy.stats
- **Visualization**: plotly, ggplot2
- **Version Control**: Git/GitHub
- **Documentation**: Jupyter Notebooks, Markdown

### Business Analytics
- A/B Test Design & Power Analysis
- Customer Segmentation
- Personalization Strategies
- ROI Calculation
- KPI Development
>>>>>>> edb2064 (initial commit)
