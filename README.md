Toy Retail Sales Forecasting
Project Overview
This project focuses on analyzing historical sales data for a toy company to develop a reliable model for predicting future sales. The primary goal is to enable the company to optimize inventory management, enhance marketing strategies, and improve overall business planning. The analysis utilizes time series data, focusing on monthly sales figures, and explores several forecasting models to identify the most accurate approach.

Data
The analysis uses the sales_data_sample.csv dataset, which contains historical sales data with the following key variables:

Column Name

Description

ORDERNUMBER

Unique identifier for each order.

QUANTITYORDERED

Quantity of products ordered.

PRICEEACH

Price of each product.

ORDERLINENUMBER

Line number of the item in the order.

SALES

Total sales amount for the order line.

ORDERDATE

Date when the order was placed.

STATUS

Status of the order.

QTR_ID

Quarter of the year.

MONTH_ID

Month of the year.

YEAR_ID

Year of the order.

PRODUCTLINE

Category of the product.

MSRP

Manufacturer's Suggested Retail Price.

PRODUCTCODE

Unique product code.

CUSTOMERNAME

Name of the customer.

COUNTRY

Country of the customer.

DEALSIZE

Size of the deal.

The primary focus of the analysis is on the SALES variable, which represents the target for forecasting. The ORDERDATE is crucial for time series analysis.

Key Findings & Insights
Data Preprocessing and Feature Engineering
Column Removal: Irrelevant columns and those with excessive missing values (ADDRESSLINE2, STATE, TERRITORY, POSTALCODE, PHONE, ADDRESSLINE1, CONTACTFIRSTNAME, CONTACTLASTNAME) were removed.

Date Conversion: ORDERDATE was converted to a datetime object.

New Feature: A day_of_week column was created from ORDERDATE.

The data was aggregated to a monthly level for time series forecasting.

Exploratory Data Analysis (EDA) Highlights
Strong Seasonality: Sales peak significantly in late November/early December, indicating a strong influence of holiday shopping. October, January, February, and May also show higher sales.

Mid-Year Dip: June and July are consistently the weakest months for sales.

Weekday Dominance: Weekdays, particularly Friday, generate the highest sales, with weekend sales being substantially lower (approximately 20% of Friday's sales).

Yearly Trend: Sales increased from 2003 to 2004, but experienced a notable drop in 2005 (likely due to incomplete data for that year).

Top Product Lines: "Classic Cars" and "Vintage Cars" are the leading revenue generators. "Trains" and "Ships" are the lowest-performing product lines.

Concentrated Customer Base: A small number of key customers (e.g., Euro Shopping Channel, Mini Gifts Distributors Ltd.) contribute a large portion of total sales.

Geographic Hotspots: The USA is the dominant market, with Spain and France also being significant. Madrid stands out as the highest-selling city.

Efficient Order Fulfillment: The vast majority of orders are successfully "Shipped," indicating a robust order processing system.

Quantity Drives Sales: A positive correlation exists between the quantity of items ordered and the total sales value.

Deal Size: Most transactions are of "Medium" and "Small" size.

Methodology
1. Data Acquisition and Understanding
The sales_data_sample.csv dataset was loaded.

Initial inspection of data types, unique values, and missing values was performed.

2. Data Preprocessing and Feature Engineering
Irrelevant and sparse columns were dropped.

ORDERDATE was converted to datetime objects.

A day_of_week column was extracted.

Sales data was aggregated to a monthly level for time series analysis.

3. Data Analysis (EDA)
A custom function analyze_sales_data was used to provide insights into temporal trends, product performance, customer behavior, and order statuses.

Visualizations (histograms, box plots, scatter plots, line plots) were used to illustrate key patterns.

Augmented Dickey-Fuller (ADF) test was performed to check for stationarity of the monthly sales data.

Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots were examined to identify potential time series patterns (e.g., seasonality, autoregressive/moving average components).

4. Model Selection and Evaluation
The monthly sales data was split chronologically into training (up to end of 2004) and testing (2005) sets.

Three time series forecasting models were considered and evaluated:

Prophet: A model designed for time series with strong seasonality.

Holt-Winters Exponential Smoothing: A method that captures both trend and seasonality (additive and multiplicative).

SARIMA (Seasonal ARIMA): A generalization of ARIMA that models seasonal patterns.

Models were evaluated using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and Mean Absolute Percentage Error (MAPE).

Model Performance Summary (on Test Set)
Model Name

MAE

RMSE

MAPE (%)

Prophet

226,275.53

234,077.38

68.37

Holt-Winters Additive (Default)

59,503.77

65,920.84

17.01

Holt-Winters Multiplicative

62,596.26

70,642.74

17.06

Holt-Winters Additive (Tuned)

49,158.49

55,420.91

14.01

Non-Seasonal ARIMA

66,202.69

77,086.50

19.12

SARIMA (D=0)

58,615.42

66,154.57

15.90

5. Final Model and Future Forecast
Based on the evaluation metrics (lowest MAPE, MAE, RMSE), the tuned Holt-Winters Additive model was selected as the final forecasting model.

This model was retrained on the entire dataset to leverage all available data.

The model was used to forecast total monthly sales for the next three months (June, July, and August 2005).

Forecasted Sales (June - August 2005)
Date

Forecasted Sales

2005-06-01

$375,892

2005-07-01

$408,490

2005-08-01

$481,880

The forecast indicates a continued upward trend in sales for these three months.

Strategic Recommendations for the Toy Company
Based on the sales forecasting analysis, the following recommendations are provided:

Leverage Strong Seasonality: Capitalize on the strong year-end seasonality (Nov/Dec) by optimizing inventory, marketing, and logistics.

Capitalize on Weekday Sales: Consider targeted promotions for weekdays, especially Fridays, to further boost sales.

Address Mid-Year Dip: Explore strategies (e.g., targeted discounts, summer-themed products) to mitigate weaker sales in June and July.

Focus on Top Products: Prioritize "Classic Cars" and "Vintage Cars" product lines for continued investment and growth.

Re-evaluate Underperforming Lines: Conduct a thorough review of "Trains" and "Ships" product lines to determine if they should be revitalized or discontinued.

Nurture Key Customer Relationships: Strengthen ties with major clients like "Euro Shopping Channel" and "Mini Gifts Distributors Ltd."

Optimize Geographic Strategies: Continue investing in top-performing countries (USA, Spain, France) and cities (Madrid), while exploring growth potential in underperforming regions.

Monitor Forecast Accuracy: Continuously track actual sales against the forecast to refine future predictions and business strategies.

Consider Further Forecasting: Explore product-level forecasting and incorporate the impact of promotions into future models for better accuracy.

How to Run the Code
Prerequisites
Python 3.x

Jupyter Notebook (recommended for interactive exploration) or a Python IDE.

Dependencies
Install the necessary Python libraries using pip:

pip install pandas numpy matplotlib seaborn plotly statsmodels prophet pmdarima scikit-learn

Files
sales_data_sample.csv: The raw dataset containing toy retail sales information.

codes.py: The Python script (originally a Jupyter Notebook) containing all the code for data loading, preprocessing, EDA, model training, evaluation, and forecasting.

Documantation of case study (1).docx: A detailed report outlining the project's process, results, and recommendations.

Execution Steps
Place the data file: Ensure sales_data_sample.csv is in the same directory as codes.py.

Run the script:

If using a Jupyter Notebook, open codes.py (you might need to convert it to .ipynb if it's not already) and run all cells sequentially.

If running as a Python script from your terminal:

python codes.py

The script will:

Perform data loading and preprocessing.

Execute detailed EDA, printing insights and generating various plots.

Train and evaluate Prophet, Holt-Winters, and SARIMA models, printing their performance metrics.

Perform grid search for Holt-Winters parameters.

Generate and visualize the final Holt-Winters forecast for future months.
