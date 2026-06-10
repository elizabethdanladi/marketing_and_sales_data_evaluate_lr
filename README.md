Marketing and Sales data evaluation

Project Overview:

This project investigates the impact of advertising expenditures on sales using Multiple Linear Regression. The objective is to identify which marketing channels contribute most significantly to sales performance and provide data-driven recommendations for budget allocation.

Dataset:

The dataset contains 4,572 observations with the following variables:

TV Advertising Spend
Radio Advertising Spend
Social Media Advertising Spend
Sales (Target Variable)
After data cleaning and removal of missing values, 4,546 observations were used for model training and analysis.

Technologies Used:

Python
Pandas
NumPy
Matplotlib
Seaborn
Statsmodels
SciPy

Installation:
Clone the repository:

git clone https://github.com/elizabethdanladi/marketing_and_sales_data_evaluate_lr

Analysis Workflow:

Data Inspection and Cleaning
Missing Value Treatment
Exploratory Data Analysis (EDA)
Correlation Analysis
Multiple Linear Regression (OLS)
Model Diagnostics
ROI Analysis
Marketing Budget Recommendations
Correlation Analysis

Correlation with Sales:

Variable and	Correlation
TV	0.9995
Radio	0.8686
Social Media	0.5274

Key Insight:

TV advertising showed the strongest relationship with sales, exhibiting an almost perfect positive correlation (r = 0.9995).

Regression Model

The fitted regression equation is:

Sales = -0.134 + 3.563(TV) - 0.004(Radio) + 0.005(Social_Media)

Model Performance

Metric	Value
R²	0.9990
Adjusted R²	0.9990
F-Statistic	1,504,986.33
Observations	4,546
AIC	22,740.25
BIC	22,765.93
Interpretation

The model explains approximately 99.9% of the variation in sales, indicating an exceptionally strong fit.

Coefficient Results

Variable	Coefficient	p-value	Significant?
Intercept	-0.1340	0.1927	No
TV	3.5626	< 0.001	Yes
Radio	-0.0040	0.6848	No
Social Media	0.0050	0.8419	No
Interpretation

A one-unit increase in TV advertising is associated with an average increase of 3.56 units in sales, holding other variables constant.
Radio advertising did not have a statistically significant effect on sales.
Social Media advertising did not have a statistically significant effect on sales.
ROI Analysis

Estimated increase in sales per $100 invested:

Channel	Sales Increase
TV	$356.26
Social Media	$0.50
Radio	-$0.40
ROI Ranking

TV Advertising
Social Media Advertising
Radio Advertising
Business Recommendations

Based on the analysis:

Allocate 60–70% of the marketing budget to TV advertising.
Allocate 20–30% to Social Media advertising as a supporting channel.
Reserve approximately 10% for experimentation, testing, and optimization.
Retrain the model periodically to account for changing market conditions.
Example Business Impact

For every $10,000 increase in TV advertising spend, the model predicts:

Expected sales increase: $35,626
Approximate Return on Ad Spend (ROAS): 356.3%

Conclusion

The analysis demonstrates that TV advertising is the dominant driver of sales performance in this dataset. With a coefficient of 3.56, a statistically significant p-value (< 0.001), and the highest ROI among all channels, TV advertising should receive the largest share of future marketing investments. The model achieved an R² of 0.999, indicating excellent predictive capability.
