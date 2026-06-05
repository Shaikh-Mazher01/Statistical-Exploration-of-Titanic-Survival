🚢 Statistical Exploration of Titanic Survival 
Role: Data Analyst
Objective: Clean raw passenger data, engineer impactful features, and apply statistical hypothesis testing to identify the core socio-demographic drivers of survival.

1. Data Integrity & Cleaning Actions
Before exploring patterns, the raw dataset was audited and restructured to ensure accurate statistical modeling:

Missing Data Resolution: The Cabin column was dropped due to catastrophic missingness (>75%). Missing Embarked values were imputed using the statistical mode (S). Missing Age entries were handled dynamically using median imputation grouped by passenger characteristics to eliminate bias.
Feature Engineering: The confusing and mathematically redundant columns SibSp (siblings/spouses) and Parch (parents/children) were consolidated into a single metric: FamilySize ( FamilySize=SibSp+Parch+1 ).
Outlier Stabilization: The heavily right-skewed Fare feature was normalized using a log-transformation (np.log1p), preventing extreme values from distorting distance-based metrics or linear variance.

2. Key Analytical Insights & Statistical Validations
📊 Insight 1: Gender was the Primary Shield
The data overwhelmingly confirms the historical "Women and children first" protocol. Females achieved a massive survival rate (exceeding 70%), while adult males faced a staggering mortality rate with over 450 casualties.

🔬 Statistical Validation (Chi-Square Test of Independence): A Chi-Square test was conducted between Sex and Survived. The resulting p-value was exceptionally close to 0 ( p<0.05 ), allowing us to formally reject the Null Hypothesis ( H0 ). This mathematically proves that the survival discrepancy between genders was not a random coincidence, but a highly significant systematic effect.
📊 Insight 2: Socio-Economic Class Dictated Access
Passenger class heavily modulated survival probability, heavily tied to ship architecture and cabin proximity to the upper boat deck. 1st-class passengers were highly prioritized, whereas 3rd-class passengers suffered a catastrophic density of casualties (over 350 deaths).

The Intersection: A 1st-class male still had a lower statistical probability of survival ( ≈37% ) than a 3rd-class female ( ≈50% ), proving gender filters overrode class privilege.
📊 Insight 3: The "Sweet Spot" of Family Dynamics
When analyzing the engineered FamilySize feature, a clear non-linear relationship emerged:

Solo Travelers ( FamilySize=1 ): Suffered the highest raw volume of deaths, representing a vulnerable baseline of lower-class individuals.
Nuclear Units ( FamilySize=2,3,4 ): Represented the survival sweet spot where survivors actually outnumbered casualties due to mutual assistance.
Large Families ( FamilySize≥5 ): Survival rates completely collapsed, as navigating a chaotic, flooding ship with large groups proved logisting impossible.
📊 Insight 4: The Childhood Priority Exception
While adult males faced near-total casualty rates, young boys (Ages 0–10) showed a prominent spike in density on the survival side of the distribution, confirming their prioritization during evacuation.

🔬 Statistical Validation (Independent Two-Sample T-Test): An Independent T-Test was performed comparing the ages of survivors versus non-survivors. The test yielded a statistically significant result ( p=0.0031<0.05 ), rejecting the Null Hypothesis ( H0 ). This confirms that the age difference between survivors (who skewed younger in the male cohort) and casualties is mathematically meaningful and driven by systematic emergency protocols.

3. Final Strategic Conclusion
The ideal profile for survival on the Titanic was a 1st or 2nd-class female traveling in a small family unit. Conversely, the highest risk profile was an adult, 3rd-class male traveling alone or as part of a massive family unit.
