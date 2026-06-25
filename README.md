# Business Forecasting: Monthly Toys Sales

## Project Overview

The toy industry is highly susceptible to demand volatility and strong seasonal trends (e.g., holiday spikes). This volatility makes accurate sales forecasting a major challenge, often leading to overstocking (increasing storage costs) or stockouts (missing revenue opportunities).

The objective of this project is to develop a robust, end-to-end Time Series Forecasting pipeline to accurately predict monthly toy sales. These predictions are designed to:

* Optimize inventory and reduce warehousing costs.
* Improve supply chain efficiency to prevent stockouts during peak demand.
* Guide long-term strategic business planning.

## Data Description

The dataset consists of historical monthly toy sales spanning 19 years.

* **Time Period:** January 2006 to December 2024
* **Total Observations:** 228 Months
* **Key Statistics:**
* Mean monthly sales: ~158.65k units
* Minimum sales: 114.6k units
* Maximum sales: 217.8k units
* Standard Deviation: 21.79k units (indicating high volatility and wide swings between low-demand and peak-season months).



## Methodology

1. **Exploratory Data Analysis (EDA):** Analyzed the data for long-term trends and seasonal variations using boxplots and yearly overlay charts.
2. **Time Series Decomposition:** Applied a multiplicative decomposition model to isolate the trend, seasonal, and residual components.
3. **Stationarity Testing & Transformation:** Conducted Augmented Dickey-Fuller (ADF) tests. Applied 1st-order differencing and deseasonalization techniques to transform the non-stationary raw data into a stationary format suitable for modeling.
4. **Parameter Selection:** Utilized Autocorrelation (ACF) and Partial Autocorrelation (PACF) plots to determine optimal lags.
5. **Model Training & Evaluation:** Split the data into a training set (2006–2023) and a holdout test set (2024).

## Models Implemented

The following models were built and compared against the 2024 test data:

* **ARIMA** (AutoRegressive Integrated Moving Average) - applied to deseasonalized data.
* **SARIMA** (Seasonal ARIMA) - explicitly modeled to handle the 12-month seasonality.
* **Holt-Winters Exponential Smoothing** (Multiplicative Model).

## Results & Final Model Selection

The models were evaluated based on Root Mean Squared Error (RMSE) and Mean Absolute Percentage Error (MAPE).

| Model | RMSE | MAPE |
| --- | --- | --- |
| **SARIMA (1,1,1)(1,1,1,12)** | **8.173** | **4.64%** |
| ARIMA | 8.426 | 4.66% |
| Holt-Winters | 10.257 | 5.12% |

**Conclusion:** The **SARIMA** model was selected as the final production model. It successfully captured both the underlying trend and the complex monthly seasonality, achieving the lowest error rates (MAPE of 4.64%) on unseen test data.

## Repository Structure

* `Business_Forecasting_Toys_Sales_Forecasting.ipynb`: The core Jupyter Notebook containing all Python code for EDA, statistical testing, model building, and evaluation.
* `Toys Sales.xlsx`: The raw dataset containing the `Date` and `Toys Sales` columns.

## 🚀 How to Run

1. Clone this repository.
2. Ensure you have the following Python libraries installed: `pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels`, `scikit-learn`.
3. Open `Business_Forecasting_Toys_Sales_Forecasting.ipynb` in Jupyter Notebook or your preferred IDE and run the cells sequentially.
