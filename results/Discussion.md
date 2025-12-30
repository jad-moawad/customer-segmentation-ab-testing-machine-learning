


### Propensity scores

First we analyze the propensity score, it is important because in a perfectly randomized experiment (like flipping a fair coin), everyone should have a 50% chance of getting the treatment. The propensity score helps us check if our randomization worked well. The left graph (Propensity Score Distribution) shows that most people have propensity scores clustered around 0.5 (the red dashed line), which is exactly what we'd expect in a well randomized experiment. The bell-shaped distribution centered at 0.5 is a good sign, it means the randomization worked well. The right graph (scores by treatment group) shows that both the treatment group (red) and control group (blue) have similar distributions of propensity scores. The substantial purple overlap area is excellent, it means the two groups are comparable. If one group had very different scores than the other, it would suggest the randomization failed somehow.

These results confirm that the experiment's randomization worked properly. This is crucial because it means any differences we observe in portfolio allocation between the treatment and control groups can be confidently attributed to the financial information given to respondents, not to pre-existing differences between the groups.


![Propensity Score Analysis](https://raw.githubusercontent.com/jad-moawad/financial-literacy-experiment/main/Figures/ML_fig_1.png)



### cross-validation and tuning

After validating our randomization through propensity score analysis, we explored whether the financial information intervention affected all participants equally or produced differential impacts across subgroups. We employed causal forest analysis—an advanced machine learning technique that extends random forests for causal inference—to identify these heterogeneous treatment effects.

Unlike traditional methods that estimate only average treatment effects, causal forests automatically discover participant subgroups with varying responses to interventions. In our context, this meant identifying whether certain demographic or behavioral characteristics predicted stronger or weaker responses to the ETF information without pre-specifying which factors might matter.

We conducted systematic hyperparameter tuning to optimize model performance, testing nine configurations that varied the minimum observations per leaf (5 to 50), number of trees (2,000 to 4,000), sampling proportion (45% to 50%), and feature selection methods. To ensure robust results, we implemented five-fold cross-validation with stratification. Our evaluation framework balanced two objectives through a composite scoring function: detecting meaningful heterogeneity (weighted at 40%) and maintaining statistical precision (60%). This approach prioritized reliable estimates while capturing important variation in treatment responses, considering metrics such as treatment effect variance, interquartile range, and confidence interval width.

The analysis yielded compelling findings. The average treatment effect remained remarkably stable across all configurations at approximately 17.9 percentage points. The optimal configuration consisted of 20 samples per leaf, 4,000 trees, and 45% sampling rate. 

### Understanding the Heterogeneity Analysis

After establishing the optimal causal forest configuration, we performed a detailed heterogeneity analysis to understand how the provided financial information influenced different participants.

On the left, a histogram displays the distribution of individualized treatment effects.  The distribution is roughly normal, centered around a mean effect of 17.9 percentage points. This bell curve indicates that most participants' responses cluster around the average, with fewer individuals showing extremely high or low responses. The smooth, continuous nature of this distribution suggests that the treatment effect varies along a spectrum rather than affecting distinct, separate subgroups.

On the right, the plot shows how the treatment effect varied across the whole population. The plot reveals substantial heterogeneity in individual responses. The blue line represents point estimates, which range from approximately 8 to 27 percentage points. In other words, some participants responded nearly three times more strongly to treatment than others. The pink shaded area shows the 95% confidence intervals, which remain narrow and consistently above zero. This confirms that the positive effect of financial information on ETF allocation is statistically significant across the entire sample. 


### Variable of importance

This analysis identifies which participant characteristics drive the heterogeneous treatment effects we discovered. The causal forest algorithm automatically determines which variables best explain why some individuals responded more strongly to the ETF information than others. By extracting feature importances from our optimized model, we can understand the key factors that moderate the intervention's effectiveness.
The results reveal a clear hierarchy of influence. Subjective financial knowledge emerges as the dominant driver, explaining 22.5% of the variation in treatment response. This suggests that participants' self-perceived understanding of finance fundamentally shapes how they process and act on new investment information. Risk tolerance follows as the second most important factor at 13.9%, indicating that individuals' comfort with financial uncertainty moderates their willingness to shift toward ETFs after learning about their characteristics. Age contributes 13.1%, potentially reflecting generational differences in investment attitudes or retirement planning horizons.

The cumulative importance plot demonstrates that seven variables account for nearly 80% of the heterogeneity, with the remaining variables contributing marginally. Here are the contributions of each variableSubj. Fin. Knowledge: 22.5%
,Risk Tolerance: 13.9%, Age: 13.1%, Trust in Gov.: 9.9% , Low Social Origin: 8.8% , Political Placement: 6.7% , Low Education: 4.8%, Woman: 4.4%, High Income: 3.6%, White: 3.2%


### Heterogneity analysis
 
We extract the individual treatment effects (CATEs) directly from our optimized causal forest model and visualizes how these model-predicted effects vary across key participant characteristics. This approach transforms the complex, high-dimensional patterns discovered by the machine learning algorithm into interpretable insights. We focus on the top four variables that explained the most percentage of the heterogeneity. These are  subjective financial knowledge, age, riskt tolerance, trust in government. 

The results reveal fascinating patterns in who benefits most from financial education. Age shows a positive relationship with treatment effects, rising from about 16 percentage points for younger participants to over 20 percentage points for those in their mid sixties and older. This suggests that proximity to retirement may increase receptiveness to investment information. On the other hand, subjective financial knowledge displays a negative relationship, with those rating themselves as highly knowledgeable showing treatment effects near 12 percentage points compared to 23 percentage points for those with low self-rated knowledge. This finding suggests that financial information may be most valuable for those who recognize their knowledge gaps. 

Risk tolerance and trust in government both exhibit negative relationships with treatment effects. The findings suggests that risk-averse individuals and those with lower institutional trust responded more strongly to the objective information about ETFs. It is not surprising that individuals with lower risk tolerance responds better to the financial information. Many individuals do not know much about ETFs, and once they were given information about the short term and long term risk of ETFs compared with other investment instruments, these people opted for more investments in ETFs. We cannot speculate much about the reasoning behind it, but we may think that they found ETFs risks acceptable to their appetite compared to the other instruments. Finally, we found that people who have lower trust in government responds better to the treatment. 


### Policy tree decision 

We estimate heterogeneous effects with a causal forest of 4,000 trees. This ensemble is highly accurate but hard to interpret. It’s like thousands of experts voting: you see the verdict, not the reasoning. To surface the logic, I fit a compact “policy tree” trained to mimic the forest’s predictions. It translates the model into clear if-then rules about who benefits more. While it can’t capture every nuance of the full forest, it highlights the features most associated with larger treatment effects.

In the visualization, darker nodes indicate a higher treatment effect. The root node represents the full sample (100%) with an average treatment effect of 17.9 percentage points. From there, the tree splits on key characteristics to trace subgroups that respond most strongly to the intervention. The primary split is subjective financial knowledge at a threshold of 6.5. The left branch (score < 6.5) covers 70.1% of participants and shows an average treatment effect of 19.8 percentage points. The right branch (score > 6.5) covers 29.9% and shows 13.5 points. This pattern suggests that respondents reporting lower financial knowledge gain more from the treatment.

Among respondents with low subjective financial knowledge (score < 6.5), the tree drills down further. It first splits this group at 4.5, yielding two branches: very low knowledge (< 4.5) and moderately low (4.5–6.5). The very-low branch shows a larger average treatment effect (ATE) of 22.0 percentage points, compared with 18.0 points for the moderately low branch. At the next level (depth 3), the branches introduce different drivers: one splits on social origin, the other on age. Along the social-origin split, participants from lower socioeconomic backgrounds exhibit a stronger effect—23.0 points versus 20.4 points for those from higher-status backgrounds. Along the age split, the effect is 21.3 points among those older than 62, compared with 17.4 points for younger respondents. The findings indicate that within the low-knowledge segment, effects are strongest for those with very low knowledge, from lower-SES backgrounds, and for older adults.

Among respondents with high subjective financial knowledge (score > 6.5), the tree next splits on social origin. At this node (depth 3), those from higher socioeconomic backgrounds show an ATE of 11.9 percentage points, while their peers from lower socioeconomic backgrounds show a larger ATE of 15.9 points. The model then introduces risk tolerance, with different cutoffs by social origin: 6.5 for higher-SES individuals and 5.5 for lower-SES individuals. Within the higher-SES branch, those with lower risk tolerance (≤ 6.5) have an ATE of 14.0 points, compared with 10.9 for their higher–risk-tolerance peers. Within the lower-SES branch, those with lower risk tolerance (≤ 5.5) reach an ATE of 17.7 points, versus 15.0 for those with higher risk tolerance. This tree suggests that among high-knowledge respondents, effects are consistently stronger for lower-SES individuals and for those with lower risk tolerance.

