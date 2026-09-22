# 📊 Sales Forecasting Using Machine Learning

## EncoderX Remote Internship — Batch 02 | Data Science Task

A machine learning project for analyzing historical sales patterns and forecasting future monthly sales using time-based feature engineering and regression models.

The project uses historical Superstore sales data to identify trends, seasonality, and sales patterns, followed by the development and evaluation of machine learning models for future sales forecasting.

---

## 📌 Project Overview

Sales forecasting is an important business analytics task that helps organizations plan inventory, manage resources, prepare marketing strategies, and make data-driven operational decisions.

In this project, historical sales transaction data was analyzed and transformed into a monthly time-series forecasting dataset.

The workflow includes:

**Data Collection → Data Cleaning → Exploratory Data Analysis → Feature Engineering → Train/Test Split → Machine Learning → Model Evaluation → Future Forecasting → Business Insights**

Two regression models were developed:

- Linear Regression
- Random Forest Regressor

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

A six-month future sales forecast was then generated for January 2015 to June 2015.

---

# 🎯 Objectives

The main objectives of this project were to:

1. Analyze historical sales data.
2. Identify long-term sales trends.
3. Explore monthly and yearly sales patterns.
4. Analyze seasonal sales behavior.
5. Engineer time-based and lag-based forecasting features.
6. Develop machine learning models for sales prediction.
7. Evaluate model performance using standard regression metrics.
8. Generate future sales forecasts.
9. Extract business-oriented insights from the analysis.
10. Provide recommendations that can support data-driven business planning.

---

# 📂 Dataset

The project uses the **Superstore Data** dataset available through Kaggle.

### Dataset Source

Kaggle dataset:

**Superstore Data**

Dataset identifier:

```text
jr2ngb/superstore-data
The dataset contains historical sales transactions covering the period from 2011 to 2014.

Dataset Statistics
Property	Value
Records	51,290
Original columns	24
Date range	2011–2014
Unique orders	25,035
Unique customers	1,590
Unique products	10,292
Categories	3
Countries	147
Total Sales	$12,642,501.91

The dataset contains information related to:

Orders
Customers
Products
Categories
Sales
Quantity
Discount
Profit
Shipping
Regions
Markets
Order priority
🧹 Data Preprocessing

Several preprocessing steps were performed before developing the forecasting models.

Date Conversion

The Order Date and Ship Date columns were converted from text format into proper datetime objects.

Final historical period:

January 2011 – December 2014

Both date columns were successfully validated with no invalid dates.

Shipping Duration

A new feature called Shipping Days was created:

Shipping Days = Ship Date - Order Date

Summary:

Statistic	Value
Mean	3.97 days
Minimum	0 days
Maximum	7 days
Missing Values

The major missing-value issue was found in the Postal Code column.

Missing Postal Codes: 41,296
Percentage: 80.51%

Since postal code was not required for the forecasting objective, it was removed from the modeling dataset.

Duplicate Records

No duplicate rows were found.

Duplicate rows = 0
📈 Exploratory Data Analysis

Exploratory analysis was performed to understand historical sales behavior.

The analysis included:

Monthly sales trends
Yearly sales performance
Monthly seasonality
Category-level sales
Sub-category sales
Historical sales extremes
📅 Yearly Sales
Year	Total Sales	YoY Change
2011	$2,259,450.90	—
2012	$2,677,438.69	+18.50%
2013	$3,405,746.45	+27.20%
2014	$4,299,865.87	+26.25%

The historical data shows increasing annual sales across the four-year period.

📆 Monthly Seasonality

Average monthly sales based on historical monthly totals:

Month	Average Sales
January	$168,783.42
February	$135,934.84
March	$192,625.24
April	$174,640.30
May	$226,003.08
June	$317,429.19
July	$187,345.46
August	$323,458.29
September	$359,345.03
October	$292,046.10
November	$387,819.34
December	$395,195.19

Historically, December had the highest average monthly sales, while February had the lowest.

🛍️ Sales by Category
Category	Sales	Share
Technology	$4,744,557.50	37.53%
Furniture	$4,110,874.19	32.52%
Office Supplies	$3,787,070.23	29.96%

Technology represented the largest share of total historical sales.

⚙️ Feature Engineering

The transaction-level dataset was aggregated into monthly sales observations for forecasting.

Several forecasting features were created.

Calendar Features
Year
Month
Quarter
Lag Features

Historical sales values from previous months were used to capture temporal dependencies:

Lag_1
Lag_2
Lag_3
Lag_6
Lag_12
Rolling Features

Rolling averages were also calculated:

Rolling_Mean_3
Rolling_Mean_6
Rolling_Mean_12

The rolling features were calculated using previous observations only to prevent future information from leaking into the model.

After applying the required lag and rolling windows:

Initial monthly observations: 48
Final forecasting observations: 36
🔀 Train-Test Split

Because this is a time-based forecasting problem, a random train-test split was not used.

Instead, the observations were divided chronologically using an 80/20 split.

Training Data
January 2012 – April 2014
28 observations
Testing Data
May 2014 – December 2014
8 observations

This preserves the temporal order and prevents future observations from being used during training.

🤖 Machine Learning Models

Two regression models were developed.

1. Linear Regression

Linear Regression was used as a baseline forecasting model.

It learns relationships between the engineered temporal features and monthly sales.

2. Random Forest Regressor

Random Forest Regression was implemented as a tree-based ensemble model capable of learning nonlinear relationships between the forecasting features and sales.

📊 Model Evaluation

The models were evaluated using:

MAE

Mean Absolute Error measures the average absolute difference between actual and predicted sales.

Lower values indicate smaller prediction errors.

RMSE

Root Mean Squared Error gives greater weight to larger prediction errors.

Lower values indicate better predictive accuracy.

R² Score

R² measures the proportion of variation in the target variable explained by the model on the evaluation data.

Model Performance
Model	MAE	RMSE	R²
Linear Regression	$69,068.00	$79,598.36	0.3147
Random Forest	$88,431.76	$100,283.78	-0.0878

On the chronological test set, Linear Regression produced lower MAE and RMSE values and a higher R² than Random Forest.

Based on these test-set results, Linear Regression was used for the future forecasting stage.

Note: These results are specific to the selected dataset, features, model configurations, and eight-month test period.

🔮 Future Sales Forecast

The Linear Regression model was used to generate a recursive six-month forecast.

Forecast period:

January 2015 – June 2015
Forecast Results
Month	Forecasted Sales
January 2015	$238,103.84
February 2015	$178,025.47
March 2015	$269,086.65
April 2015	$272,591.10
May 2015	$348,741.56
June 2015	$457,920.93
Forecast Summary

Average monthly forecast:

$294,078.26

Total forecast for six months:

$1,764,469.54

Highest forecast:

June 2015 — $457,920.93

Lowest forecast:

February 2015 — $178,025.47

The future forecasting process was recursive, meaning that predicted values were incorporated into the lag and rolling features used for subsequent forecast months.

💼 Business Insights

The analysis provides several potential business applications.

1. Inventory Planning

Forecasted sales can help businesses plan inventory levels and prepare for periods of higher expected demand.

2. Seasonal Planning

Historical sales show considerable variation across months. Seasonal patterns can therefore be considered when planning procurement and inventory.

3. Marketing Planning

Marketing campaigns can be aligned with periods of stronger historical sales activity.

4. Category Management

Technology contributed approximately 37.53% of total historical sales, making category-level analysis useful for product planning.

5. Operational Planning

Sales forecasts can support decisions related to staffing, logistics, procurement, and resource allocation.

6. Data-Driven Decision Making

Combining historical analysis with predictive modeling provides a quantitative approach to planning instead of relying entirely on historical intuition.

📊 Project Visualizations

The project generates the following visualizations:

Historical Monthly Sales

Annual Sales Performance

Monthly Seasonality

Sales by Category

Model Comparison

Historical Sales and Future Forecast

📁 Project Structure
sales_forecasting_project/
│
├── README.md
│
├── data/
│   └── monthly_forecasting_dataset.csv
│
├── models/
│   ├── linear_regression_model.pkl
│   └── random_forest_model.pkl
│
├── notebooks/
│   └── Sales_Forecasting_EncoderX_Batch02.ipynb
│
├── outputs/
│   │
│   ├── analysis/
│   │   ├── category_sales_analysis.csv
│   │   ├── historical_monthly_sales.csv
│   │   ├── model_comparison.csv
│   │   ├── monthly_seasonality.csv
│   │   ├── subcategory_sales_analysis.csv
│   │   └── yearly_sales_analysis.csv
│   │
│   ├── figures/
│   │   ├── 01_historical_monthly_sales.png
│   │   ├── 02_yearly_sales.png
│   │   ├── 03_monthly_seasonality.png
│   │   ├── 04_category_sales.png
│   │   ├── 05_model_comparison.png
│   │   └── 06_historical_future_forecast.png
│   │
│   └── forecasts/
│       └── future_sales_forecast.csv
│
└── src/
    └── [project source code]
🛠️ Technologies Used
Programming Language
Python
Libraries
Pandas
NumPy
Matplotlib
Scikit-learn
Joblib
Development Environment
Jupyter Notebook
Python
Git
GitHub
Machine Learning
Linear Regression
Random Forest Regression
Evaluation Metrics
MAE
RMSE
R²
Limitations

Although the project demonstrates a complete sales forecasting workflow, several limitations should be considered.

The forecasting dataset contains a relatively small number of monthly observations.
Only eight observations were available in the chronological test set.
External factors such as holidays, promotions, advertising expenditure, economic conditions, and competitor activity were not included.
The future forecast is based on historical sales patterns and engineered temporal features.
Recursive forecasting means that future predictions depend partly on previous predicted values.
Model performance may change when additional historical data and external forecasting variables become available.
🔮 Future Improvements

The project could be extended by:

Adding holiday information
Including promotional data
Incorporating marketing expenditure
Adding economic indicators
Testing additional forecasting models
Performing time-series cross-validation
Increasing the forecasting horizon
Hyperparameter tuning
Adding external demand-related features
Comparing machine learning models with dedicated time-series models such as ARIMA or SARIMA
Deploying the forecasting model through a Streamlit dashboard
📌 Key Takeaway

This project demonstrates an end-to-end machine learning workflow for sales forecasting, beginning with raw transactional data and progressing through preprocessing, exploratory analysis, feature engineering, model development, evaluation, forecasting, and business interpretation.

The analysis shows how historical sales patterns can be transformed into predictive features and used to support data-driven business planning.

👩‍💻 Author

Aiman Babar

BS Bioinformatics
University of Agriculture Faisalabad

🎓 Internship

EncoderX Remote Internship — Batch 02

Task: Sales Forecasting

This project was completed as part of the Data Science internship task.

📄 License

This project is intended for educational and portfolio purposes.

Please refer to the original dataset source for dataset-specific licensing and usage terms.

⭐ Acknowledgements

I would like to thank EncoderX for providing this learning opportunity and for creating an environment where I could apply data science and machine learning concepts to a practical business problem.
