
# 🎯 Business Problem
Financial services companies struggle with low adoption rates of profitable investment products. This project demonstrates how data science can drive 18% increases in a product adoption.

# 💡 Solution Approach
A two-phase data science project combining:
1. **A/B Testing**: Randomized controlled experiment (N=2,568) testing targeted information interventions
2. **Machine Learning**: Causal Forest analysis to identify customer segments for personalized targeting

# 📈 Key Results
- **18% increase** in ETF adoption through optimized information delivery
- **Machine Learning model identified** 3 key customer segments with differential responses (8-27% effect range)
- **$2.67 million potential revenue impact** for a medium-sized brokerage 



## **Part 1: A/B Testing: Information Design for Product Adoption**

### Business Context
- **Industry Challenge**: Only 28% of retail investors use ETFs despite superior risk-adjusted returns
- **Revenue Opportunity**: Each 1% increase in ETF adoption = $150,000 in annual fee revenue
- **Target KPI**: Increase ETF allocation in customer portfolios

### Experimental Design
- **Sample Size**: 2,568 users (powered for 5% minimum detectable effect)
- **Randomization**: 50/50 split with stratification
- **Treatment**: Targeted product comparison interface
- **Control**: Standard product selection interface
- **Primary Metric**: % allocation to ETF products
- **Secondary Metrics**: Allocation shifts from low-yield products


## **Part 2: Machine Learning Using Causal Forest for Personalized Marketing**

### Business Objective
Identify which customers respond best to financial education interventions 
to optimize marketing spend and personalization strategies.

### Technical Implementation

#### 1. Causal Forest Model Development

##### Technologies used:
- EconML's CausalForestDML
- 5-fold cross-validation with stratification
- Hyperparameter grid search (9 configurations)
- Custom scoring function balancing heterogeneity detection (40%) and precision (60%)

##### Optimal Model Configuration:
- Trees: 4,000
- Min samples per leaf: 20
- Sampling rate: 45%
- Feature selection: sqrt


#### 2. Feature Engineering & Selection

* 20+ customer features including:
    * **Behavioral:** risk tolerance, financial knowledge
    * **Demographic:** age, education, income
    * **Psychographic:** trust indices, political orientation
* Automated feature importance extraction
* Dimensionality reduction for interpretability

#### 3. Customer Segmentation Results

##### **High-Response Segments** (20-27% effect):

* Low financial confidence and Age 60+
* Lower socioeconomic background and Risk-averse
* **Business Insight:** Target these segments first 

##### **Medium-Response Segments** (15-20% effect):

* Moderate financial knowledge
* Middle-aged (40-60)

##### **Low-Response Segments** (8-15% effect):

* High financial confidence
* High risk tolerance
* **Business Insight:** Require different intervention strategies


## 🛠️ Technical Stack

### Statistical Methods
- Randomized Controlled Trials (RCT)
- Causal Inference (Average Treatment Effects, CATE)
- Regression Analysis (OLS, Interaction Effects)
- Propensity Score Methods

### Machine Learning
- Causal Forests 
- Hyperparameter Tuning
- Cross-Validation Strategies
- Feature Importance Analysis
- Policy Learning/Decision Trees

### Programming & Tools
- **Languages**: Python 
- **Libraries**: econml, scikit-learn, pandas, numpy, matplotlib, seaborn
- **Visualization**: plotly
- **Version Control**: Git/GitHub
- **Documentation**: Jupyter Notebooks, Markdown

### Business Analytics
- A/B Test Design & Power Analysis
- Customer Segmentation
- Personalization Strategies
- ROI Calculation
- KPI Development

