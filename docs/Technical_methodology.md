# Technical Methodology

## 🔬 Experimental Design

### Study Overview
I conducted a **pre-registered randomized controlled trial (RCT)** to measure the causal impact of financial information on investment behavior. This rigorous experimental design ensures the results are causal, not merely correlational.

**Key Design Features:**
- **Pre-post design:** Captured within-subject changes in investment allocation
- **Randomization:** Ensured causal inference through random treatment assignment
- **Real incentives:** $100 lottery stakes to ensure ecological validity
- **Large sample:** N=2,568 for robust statistical power

### Timeline & Platform
- **Data Collection Period:** January - April 2025
- **Platform:** Experiment is conducted on _Qualtrics_ and participants are recruited through _Prolific Academic_ 
- **Ethics:** Approved by University of Oxford CUREC


## 📊 Data Collection & Quality Control

### Sample Recruitment
**Initial Sample:** 2,737 U.S. adults
- **Eligibility:** U.S. residents, 18+ years old
- **Sampling:** Representative sample balanced on age, gender, and race
- **Comparison:** Demographics aligned with American Community Survey (ACS)

### Data Cleaning Pipeline
I implemented systematic quality controls to ensure data integrity:

| Stage | Sample Size | Exclusions | Reason |
|-------|------------|------------|--------|
| Initial | 2,737 | - | Raw data |
| Bot Detection | 2,703 | 34 | Failed reCAPTCHA (score < 0.5) |
| Attention Check | 2,619 | 84 | Failed embedded attention questions |
| Completeness | 2,568 | 51 | Missing critical responses |
| **Final Sample** | **2,568** | **169 total** | **93.8% retention rate** |

## 🎯 Experimental Protocol

### Stage 1: Baseline Measurement
**Objective:** Capture pre-treatment investment preferences

Participants allocated a hypothetical portfolio across 5 instruments:
- **Individual Stock** 
- **ETF** 
- **Gold** 
- **Savings Account** 
- **Cryptocurrency** 

**Design Choices:**
- Percentage allocations (must sum to 100%)
- Randomized example portfolios to prevent anchoring
- Participants could assign any percentage to any instrument, from 0% to 100%, concentrating in one or spreading across many.

### Stage 2: Covariate Collection
**Pre-treatment measures** to enable heterogeneity analysis:

| Measure | Type | Scale | Purpose |
|---------|------|-------|---------|
| Subjective Financial Knowledge | Self-rated | 0-10 | Confidence assessment |
| Objective Financial Literacy | Test | Binary | Actual knowledge |
| Risk Tolerance | Self-rated | 0-10 | Risk preferences |
| Political Orientation | Self-rated | 0-10 | Ideological factors |
| Trust in Government | Self-rated | 0-10 | Institutional confidence |

### Stage 3: Quality Control
**Attention Check:** Mid-survey verification requiring specific selections
- Position: Strategic midpoint placement
- Design: Clear instructions ("Select hiking AND swimming")
- Purpose: Identify inattentive respondents

### Stage 4: Randomized Treatment

#### Treatment Group (n=1,292)
Received a **one-page educational intervention** featuring:

#### 📈 Investment Basics Guide

##### **Let's start with the basics: what does investing mean?**

When you invest in the stock market, you are buying small pieces (called **shares**) of a company. This means you own a part of that company and can benefit if it grows and makes money.

But instead of just buying shares in one company, you can use something called an **ETF** (*Exchange-Traded Fund*). An ETF lets you own shares in many different companies at once. It's like putting your money into a basket that holds a variety of companies, so you're not relying on just one. This way, you spread your risk - a bit like not putting all your eggs in one basket.

---

##### **Why consider the S&P 500 ETF?**

• Your money goes to the **500 largest U.S. companies**  
• **Low barrier to entry**, you can start with as little as $1  
• **Diversified** across multiple industries: technology, healthcare, finance, and more  
• Buy and sell anytime during trading hours  
• Low annual fees (~0.07%)  
• **Historical growth**: $10,000 invested in January 2015 would have grown to about $28,000 by January 2025  

---

##### **Investment Comparison**

| Instrument | Short-Term Risk | Long-Term Risk | Potential Returns |
|------------|-----------------|----------------|-------------------|
| Individual stock | High | Moderate | High |
| Exchange-Traded Fund (ETF) | Moderate | Low | High |
| Gold | Moderate | Low | Low-Moderate |
| Savings Account | Low | Very Low | Low |
| Cryptocurrency | Very High | Very High | Very High |

> **Note:** This comparison is based on historical data and past performance. Past performance does not guarantee future results.

---

##### 🏛️ **Regulation**
In the U.S., ETFs are regulated by the Securities and Exchange Commission (SEC). They must follow strict guidelines, enhancing investor protection.

##### 👥 **Expert Recommendations**
Experts from various backgrounds, irrespective of political leanings - Republican or Democrat - often endorse ETFs. Support comes from numerous Nobel Prize-winning economists, financial advisors, media personalities, journalists, and academics.


### Stage 5: Incentivized Post-Treatment Allocation

**Real-Stakes Design:**
- **Prize:** $100 investment lottery
- **Duration:** 1-year holding period
- **Payout:** Principal + gains/losses after 1 year

**Investment Options with Defaults:**
| Asset Class | Default Option | Alternatives Allowed |
|------------|----------------|---------------------|
| Savings Account | Capital One 360 | Yes |
| ETF | S&P 500 | Yes |
| Individual Stock | Apple | Yes |
| Gold | Physical Gold | No |
| Cryptocurrency | Bitcoin | Yes |

**Methodological Advantages:**
- Real financial consequences increase external validity
- Default options reduce cognitive burden
- Alternative choices prevent artificial constraints
- 1-year horizon discourages speculation

### Stage 6: Demographics Collection

**Comprehensive profiling** for subgroup analysis:
- **Demographics:** Age, gender, race, relationship status
- **Socioeconomic:** Income, education (self & parents), employment
- **Background:** Parental birthplace, housing status

## 📐 Variable Operationalization

### Outcome Variables

**Primary Outcome:** Percentage allocation to each investment instrument. The total of all allocations should amount to 100% in the Pre- and Post-treatment variables.
- Pre-treatment: Hypothetical ideal portfolio
- Post-treatment: Incentivized lottery allocation
- **Treatment Effect:** Post - Pre allocation difference

### Key Predictors

| Variable | Operationalization |
|----------|-------------------|  
| **Treatment** | Binary (0=Control, 1=Information) |
| **Subjective Financial Knowledge** | Continuous (0-10) |
| **Risk Tolerance** | Continuous (0-10) | 
| **Age** | Continuous | 
| **Objective Financial Knowledge** | Binary (0=Incorrect answer, 1=Correct answer) |
| **Gender** | Binary (0=Men, 1=Women) | 
| **Education** | Binary (0=Some college or lower, 1=Bachelor's+) | 
| **Social Origin** | Binary (0= Low SES, 1=High SES) | 
| **Income** | Binary (0=Below median, 1=Above median) |
| **Parental Birthplace** | Binary (0=Both immigrants, 1=At least one is born US) |
| **Marital Status** | Binary (0=Not in a union, 1=In a union) |
| **Labor Market Status** | Binary (0=Not active, 1=Active) |
| **House** | Binary (0=Not an owner, 1=Owner) |
| **White** | Binary (0=No, 1=Yes) |
| **Black** | Binary (0=No, 1=Yes) |

## 🔍 Statistical Analysis Plan

### First Stage Analysis
- **Method:** OLS regression with robust standard errors
- **Interaction Effects:** Treatment × Demographics
- **Inference:** Two-sided tests, α = 0.05

### Second Stage Analysis
- **Machine Learning:** Causal Forest for automatic subgroup discovery
- **Validation:** Cross-validation with stratification

## 💪 Methodological Strengths

### Internal Validity
✅ **Random assignment** ensures unbiased treatment effects  
✅ **Pre-registration** prevents p-hacking and HARKing  
✅ **Attention checks** ensure data quality  
✅ **Within-subject design** increases statistical power  

### External Validity
✅ **Representative sample** matches U.S. demographics  
✅ **Real financial stakes** increase ecological validity  
✅ **Familiar instruments** reflect actual investment options  
✅ **Natural framing** avoids artificial laboratory effects  

### Statistical Power
✅ **Large sample** (N=2,568) powered for 5% minimum detectable effect  
✅ **Pre-post design** reduces variance through within-subject comparison  
✅ **Machine learning** discovers heterogeneous effects without pre-specification  

## 📋 Data Availability

All data and code are available in this repository:
- **Raw data:** `/data/raw` (anonymized)
- **Processed data:** `/data/processed_df`
- **Analysis code:** `/notebooks/` 
- **Pre-registration:** can be found by clicking on this [link](https://osf.io/c4brf)