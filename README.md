NBA Player Longevity Prediction

Feature Engineering Project — NBA Players Dataset

Project Overview:
This project analyses an NBA player performance dataset (1,340 players, 21 features)
using Python and pandas to engineer a clean, model-ready feature set for predicting
whether a player will remain active in the NBA for at least 5 years ( target_5yrs ).
The pipeline covers target variable definition, removal of non-predictive columns,
correlation analysis to resolve multicollinearity, creation of meaningful composite metrics,
missing value handling, and full documentation of every feature engineering decision.

Dataset:
Property Value
Source nba-players.csv
Rows 1,340 players
Original Features 21 (after dropping index/name)
Target Variable target_5yrs (1 = played 5+ years, 0 = did not)
Class Balance 62.0% career ≥5 yrs, 38.0% career <5 yrs
Missing Values None

Core Project Goals:
1. Define the target variable target_5yrs as the dependent variable for modelling
2. Drop non-predictive columns ( name , index) that add noise or risk data leakage
3. Perform correlation analysis to identify and resolve multicollinearity among predictors
4. Engineer at least one composite feature that captures player efficiency or impact
5. Handle missing values appropriately to ensure ML-readiness without introducing bias
6. Document all feature engineering decisions with clear Markdown rationale
7. 
Tools & Libraries
Tool and Purpose
Python 3 Core language
pandas Data loading, cleaning, transformation
NumPy Numerical operations, correlation matrix
Matplotlib Data visualisation
Seaborn Correlation heatmap
Jupyter Notebook Interactive analysis environment

Feature Engineering Workflow:
1. Load & Inspect Dataset
Loaded nba-players.csv and confirmed 1,340 rows, 22 columns, zero null values
Identified target_5yrs as the binary classification target
2. Drop Non-Predictive Columns
Removed:
Unnamed: 0 — row index with no predictive value
name — player identifier; inclusion would cause data leakage and model overfitting
3. Correlation Analysis & Multicollinearity Reduction
A correlation matrix was computed on all numeric features. Pairs with correlation > 0.85
were flagged as redundant. Key findings:

Feature Pair and Correlation
fgm ↔ pts 0.991
fga ↔ fgm 0.980
fga ↔ pts 0.980
3pa ↔ 3p_made 0.983
ftm ↔ fta 0.981
dreb ↔ reb 0.978
oreb ↔ reb 0.933
min ↔ pts 0.912

Decision: Dropped redundant volume stats ( fga , fgm , fta , ftm , 3pa , oreb , dreb ) and
retained percentage-based or summary features ( fg , ft , 3p , pts , reb ) to eliminate
multicollinearity while preserving information.

5. Composite Feature Engineering
Three new features were created to capture player efficiency in ways raw statistics cannot:
New Feature Formula Rationale
pts_per_min pts / min Measures scoring efficiency — removes
volume bias from high-minute players
efficiency_rating
pts + reb + ast +
stl + blk − tov
Composite all-round impact metric widely
used in basketball analytics
ast_tov_ratio ast / tov Decision-making quality — high assists
with low turnovers signals durability

7. Missing Value Handling:
No null values existed in the raw dataset
After feature creation, rows where min = 0 (zero minutes played) were handled with
np.nan replacement to avoid division-by-zero in pts_per_min and ast_tov_ratio ,
followed by median imputation to prevent bias.

Key Findings:
Top Predictors of 5-Year Career Longevity (Correlation with target_5yrs )
Rank and Feature and Correlation
1 gp (games played) +0.397
2 efficiency_rating (engineered) +0.339
3 min (minutes per game) +0.318
4 fgm +0.318
5 pts +0.316
6 reb +0.299
7 ftm +0.297

Notable: The engineered efficiency_rating feature ranks 2nd overall among all
predictors — demonstrating that composite metrics can outperform individual raw stats for
longevity prediction.

Weakest Predictors (candidates for removal)
3p (three-point percentage): correlation ≈ 0.000
3pa (three-point attempts): correlation ≈ +0.018
ast_tov_ratio : correlation ≈ −0.013
These features contribute minimal signal and were flagged for removal in the final modelready dataset.

Final Model-Ready Dataset
After the full pipeline the clean dataset retains:
Dropped: Unnamed: 0 , name , fga , fgm , fta , ftm , 3pa , oreb , dreb
Retained: gp , min , pts , fg , 3p_made , 3p , ft , reb , ast , stl , blk , tov
Added: pts_per_min , efficiency_rating , ast_tov_ratio
Target: target_5yrs.

Limitations & Next Steps
The dataset does not include positional data — position (guard vs centre) likely
influences longevity and should be encoded in future iterations
efficiency_rating is highly correlated with pts (0.968) and min (0.945); for linear
models, one of the two should be dropped to avoid introducing new multicollinearity
With a larger dataset, recursive feature elimination (RFE) with cross-validation would
provide a more rigorous feature selection method
Next step: feed the cleaned feature set into a classification model (Logistic Regression,
Random Forest) to validate predictive power.

Repository Structure
- nba_feature_engineering.ipynb # Main analysis notebook (all cells executed)
- nba-players.csv # Dataset
- README.md # This file
  
Project submitted by Elizabeth Danladi Sabatu as part of the Feature Engineering Mini Project — DH Foundation AI/ML COHORT 4
