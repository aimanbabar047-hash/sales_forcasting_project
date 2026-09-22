A machine learning project developed during the \*\*EncoderX Internship\*\* to analyze historical sales data, identify sales patterns, compare machine learning models, and forecast future monthly sales.



\---



\## 📌 Project Overview



Sales forecasting helps businesses estimate future demand based on historical sales patterns. Accurate forecasts can support better inventory planning, resource allocation, marketing decisions, and operational planning.



In this project, historical sales data was cleaned and analyzed to understand yearly, monthly, and category-level sales patterns. Time-series features such as lag values and rolling averages were then created and used to train machine learning models.



Two models were evaluated:



\- Linear Regression

\- Random Forest Regressor



The models were evaluated using a chronological train-test split to preserve the temporal nature of the data. Based on the test set used in this project, \*\*Linear Regression achieved lower prediction errors than Random Forest\*\* and was therefore used for the future forecasting stage.



\---



\## 🎯 Objectives



The main objectives of this project were:



\- Clean and preprocess the historical sales dataset.

\- Correctly parse and validate date information.

\- Analyze historical sales trends.

\- Study yearly and monthly sales patterns.

\- Analyze sales performance across product categories and sub-categories.

\- Create time-based forecasting features.

\- Train multiple machine learning models.

\- Compare model performance using MAE, RMSE, and R².

\- Forecast sales for the next six months.

\- Generate business-oriented insights from the analysis.



\---



\## 📊 Dataset



The dataset contains \*\*51,290 sales records\*\* with information related to:



\- Orders

\- Customers

\- Products

\- Categories

\- Locations

\- Sales

\- Quantity

\- Discount

\- Profit

\- Shipping Cost

\- Order Priority

\- Shipping Information



\### Dataset Dimensions



| Property | Value |

|---|---:|

| Original Records | 51,290 |

| Original Features | 24 |

| Final Records | 51,290 |

| Final Features | 24 |

| Duplicate Rows | 0 |

| Date Range | 2011–2014 |



\---



\## 🧹 Data Preprocessing



Several preprocessing steps were performed before modeling.



\### 1. Date Conversion



The dataset contained date values in an ambiguous format.



Both possible interpretations were tested:



\- MM/DD/YYYY

\- DD/MM/YYYY



A date sanity check was performed using the relationship between Order Date and Ship Date.



The \*\*DD/MM/YYYY\*\* interpretation produced valid shipping dates and realistic shipping durations.



After correction:



\- Invalid Order Dates: \*\*0\*\*

\- Invalid Ship Dates: \*\*0\*\*

\- Invalid Shipping Durations: \*\*0\*\*



\### 2. Missing Values



The Postal Code column contained:



\*\*41,296 missing values (80.51%)\*\*



Since the column had a very high proportion of missing values and was not required for the forecasting task, it was removed.



\### 3. Duplicate Records



No duplicate rows were found:



\*\*Duplicate rows = 0\*\*



\### 4. Shipping Days Feature



A new feature was created:



```text

Shipping Days = Ship Date - Order Date



The resulting shipping duration ranged from:



Minimum: 0 days

Maximum: 7 days

Average: approximately 3.97 days

📈 Exploratory Data Analysis



Several analyses were performed to understand the sales data.



Overall Sales

Metric	Value

Total Sales	12,642,501.91

Average Sales per Record	246.49

Median Sales	85.05

Minimum Sales	0.44

Maximum Sales	22,638.48

📅 Yearly Sales Analysis



Sales increased across the four available years.



Year	Sales	YoY Growth

2011	2,259,450.90	—

2012	2,677,438.69	18.50%

2013	3,405,746.45	27.20%

2014	4,299,865.87	26.25%



The dataset shows an overall upward sales trend from 2011 to 2014.



📆 Monthly Seasonality



Historical monthly sales were analyzed across all available years.



Month	Total Sales

January	168,783.42

February	135,934.84

March	192,625.24

April	174,640.30

May	226,003.08

June	317,429.19

July	187,345.46

August	323,458.29

September	359,345.03

October	292,046.10

November	387,819.34

December	395,195.19



The historical highest monthly sales value occurred in November 2014, with sales of approximately 555,279.03.



🏷️ Category Analysis



Sales were also analyzed across the three major product categories.



Category	Sales	Share

Technology	4,744,557.50	37.53%

Furniture	4,110,874.19	32.52%

Office Supplies	3,787,070.23	29.96%



Technology generated the largest share of sales in the analyzed dataset.



📦 Top Sub-Categories



The highest-selling sub-categories included:



Sub-Category	Sales

Phones	1,706,824.14

Copiers	1,509,436.27

Chairs	1,501,681.76

Bookcases	1,466,572.24

Storage	1,127,085.86

Appliances	1,011,064.30

Machines	779,060.07

Tables	757,041.92

Accessories	749,237.02

Binders	461,911.51

🤖 Machine Learning Forecasting

Monthly Forecasting Dataset



For forecasting, daily/transaction-level sales were aggregated into monthly sales.



Time-series features were created to capture historical patterns.



Features

Year

Month

Quarter

Lag\_1

Lag\_2

Lag\_3

Lag\_6

Lag\_12

Rolling\_Mean\_3

Rolling\_Mean\_6

Rolling\_Mean\_12

Lag Features



Lag features represent previous sales values.



For example:



Lag\_1  → Previous month's sales

Lag\_2  → Sales from two months earlier

Lag\_12 → Sales from the same month in the previous year

Rolling Mean Features



Rolling averages were used to capture recent historical trends.



Examples:



Rolling\_Mean\_3

Rolling\_Mean\_6

Rolling\_Mean\_12

🧪 Train-Test Split



Because sales forecasting is a time-dependent problem, a chronological split was used instead of random train-test splitting.



The forecasting dataset contained 36 monthly observations after feature engineering.



Dataset	Period	Observations

Training	Jan 2012 – Apr 2014	28

Testing	May 2014 – Dec 2014	8



This approach prevents future observations from being used to train the model before they occur.



📊 Model Evaluation



Two machine learning models were trained and evaluated.



Models

Linear Regression

Random Forest Regressor

Evaluation Metrics



The following metrics were used:



MAE (Mean Absolute Error)

RMSE (Root Mean Squared Error)

R² Score

Model Comparison

Model	MAE	RMSE	R²

Linear Regression	69,068.00	79,598.36	0.3147

Random Forest	88,431.76	100,283.78	-0.0878



On the selected eight-month test period, Linear Regression produced lower MAE and RMSE and a higher R² score than Random Forest.



Therefore, Linear Regression was selected for the future forecasting stage of this project.



🌲 Random Forest Feature Importance



The Random Forest model provided feature importance information.



The most influential features included:



Feature	Importance

Lag\_12	0.8122

Month	0.0529

Lag\_6	0.0347

Rolling\_Mean\_12	0.0338

Rolling\_Mean\_3	0.0163



The high importance of Lag\_12 indicates that sales from the same month in the previous year were particularly informative for this dataset.



🔮 Future Sales Forecast



The selected Linear Regression model was used to forecast sales for:



January 2015 – June 2015



Month	Forecasted Sales

January 2015	238,103.84

February 2015	178,025.47

March 2015	269,086.65

April 2015	272,591.10

May 2015	348,741.56

June 2015	457,920.93

Forecast Summary

Total forecasted sales: 1,764,469.54

Average monthly forecast: 294,078.26

Highest forecast: June 2015 – 457,920.93

Lowest forecast: February 2015 – 178,025.47



The forecast indicates variation across the six-month period, with higher predicted sales toward May and June.



💡 Business Insights



Based on the historical analysis and forecasting results, several practical insights can be considered.



1\. Inventory Planning



Forecasted demand can help businesses plan inventory levels and reduce the risk of both overstocking and stock shortages.



2\. Seasonal Planning



Historical monthly patterns can support preparation for months with relatively higher expected sales.



3\. Marketing Planning



Marketing campaigns and promotional activities can be aligned with expected demand periods.



4\. Category Management



Category-level sales analysis can help businesses monitor high-contribution product categories and sub-categories.



5\. Operational Planning



Forecasts can support planning for procurement, warehouse operations, staffing, and logistics.



6\. Data-Driven Decision Making



Machine learning forecasts can be used as one input alongside business knowledge, market conditions, promotions, and other operational information.



📁 Project Structure

sales\_forecasting\_project/

│

├── data/

│   └── monthly\_forecasting\_dataset.csv

│

├── models/

│   ├── linear\_regression\_model.pkl

│   └── random\_forest\_model.pkl

│

├── notebooks/

│   └── Sales\_Forecasting\_EncoderX\_Batch02.ipynb

│

├── outputs/

│   ├── analysis/

│   │   ├── historical\_monthly\_sales.csv

│   │   ├── yearly\_sales\_analysis.csv

│   │   ├── monthly\_seasonality.csv

│   │   ├── category\_sales\_analysis.csv

│   │   ├── subcategory\_sales\_analysis.csv

│   │   └── model\_comparison.csv

│   │

│   ├── figures/

│   │   ├── 01\_historical\_monthly\_sales.png

│   │   ├── 02\_yearly\_sales.png

│   │   ├── 03\_monthly\_seasonality.png

│   │   ├── 04\_category\_sales.png

│   │   ├── 05\_model\_comparison.png

│   │   └── 06\_historical\_future\_forecast.png

│   │

│   └── forecasts/

│       └── future\_sales\_forecast.csv

│

├── src/

│

├── .gitignore

├── requirements.txt

└── README.md

🛠️ Technologies Used

Python

Pandas

NumPy

Matplotlib

Scikit-learn

Joblib

Jupyter Notebook

⚙️ Installation



Clone the repository:



git clone https://github.com/YOUR-USERNAME/sales-forecasting-machine-learning.git



Navigate to the project directory:



cd sales-forecasting-machine-learning



Install the required dependencies:



pip install -r requirements.txt

▶️ How to Run



Start Jupyter Notebook:



jupyter notebook



Open:



notebooks/Sales\_Forecasting\_EncoderX\_Batch02.ipynb



Run the notebook cells sequentially to reproduce the analysis and forecasting workflow.



📌 Generated Outputs



The project generates:



Analysis Files

Historical monthly sales

Yearly sales analysis

Monthly seasonality analysis

Category sales analysis

Sub-category sales analysis

Model comparison

Visualization Files

Historical sales trend

Yearly sales comparison

Monthly seasonality

Category sales distribution

Model performance comparison

Historical vs future forecast

Forecast

outputs/forecasts/future\_sales\_forecast.csv

⚠️ Limitations



This project has several limitations:



The forecasting dataset contains only 36 monthly observations after feature engineering.

Only a small number of machine learning models were evaluated.

External factors such as holidays, promotions, economic conditions, competitor activity, and market trends were not included.

The future forecast is based on historical sales patterns and engineered time-series features.

Model performance may change when evaluated on a different time period or a larger dataset.

🚀 Future Improvements



Future versions of this project could include:



More historical data.

Additional external variables.

Holiday and promotional features.

Advanced time-series models.

Hyperparameter tuning.

Cross-validation designed specifically for time-series data.

Automated forecasting pipelines.

Interactive dashboards using Streamlit or Power BI.

Deployment of the forecasting model as a web application or API.

🎓 Internship Project



This project was completed as part of the EncoderX Internship.



The project provided practical experience in:



Data preprocessing

Exploratory data analysis

Feature engineering

Time-series forecasting

Machine learning

Model evaluation

Data visualization

Business-oriented interpretation

👩‍💻 Author



Aiman Babar



BS Bioinformatics Student

University of Agriculture Faisalabad



⭐ Project Summary



This project demonstrates an end-to-end machine learning workflow for sales forecasting:



Raw Sales Data

&#x20;     ↓

Data Cleaning

&#x20;     ↓

Date Validation

&#x20;     ↓

Exploratory Data Analysis

&#x20;     ↓

Monthly Aggregation

&#x20;     ↓

Time-Series Feature Engineering

&#x20;     ↓

Chronological Train/Test Split

&#x20;     ↓

Machine Learning Models

&#x20;     ↓

Model Evaluation

&#x20;     ↓

Model Selection

&#x20;     ↓

Future Sales Forecast

&#x20;     ↓

Business Insights



The project combines data analysis and machine learning to transform historical sales data into practical forecasting insights.





