# Gold Price Forecasting in Vietnam using ARIMA

## Project Description

This project applies the ARIMA (Autoregressive Integrated Moving Average) model to forecast the buying and selling prices of gold in Vietnam, using daily time series data from August 2009 to January 2025. The objective is to capture underlying trends in gold prices and evaluate the model's forecasting accuracy, especially in the context of volatile market behavior.

A Linear Regression model is also implemented for comparison. Evaluation results show that ARIMA performs significantly better than linear regression for this dataset.

## Dataset

- Historical daily gold prices in Vietnam
- Data source: [Kaggle Dataset](https://www.kaggle.com/datasets/hoangnam729/gi-vng-ti-vit-nam-01082009-31122024)
- Key columns:
  - `Date`: Record date
  - `Buy Price`: Buying price (in 1,000 VND/tael)
  - `Sell Price`: Selling price (in 1,000 VND/tael)

## Workflow

1. **Data Preprocessing**
   - Convert the `Date` column to datetime format
   - Handle outliers using IQR filtering
   - Visualize trends and distributions

2. **Stationarity Testing**
   - Use ADF test to check for stationarity
   - Apply first-order differencing to achieve stationarity

3. **Model Configuration**
   - Use automated selection of ARIMA parameters `(p,d,q)` based on AIC
   - Model selected: ARIMA(0,1,0) for both buy and sell prices

4. **Model Training and Forecasting**
   - Fit ARIMA model on preprocessed data
   - Generate 10-day forecasts for both target variables

5. **Model Evaluation**
   - Metrics used:
     - `MAD` (Mean Absolute Deviation)
     - `SSE` (Sum of Squared Errors)
   - Visualize actual vs. predicted values

## Evaluation Results

| Target Variable | MAD   | SSE       |
|------------------|--------|------------|
| Buy Price        | 0.1298 | 471.86     |
| Sell Price       | 0.1282 | 445.32     |

- The ARIMA model achieves high accuracy with low forecast errors.
- The model effectively captures the trend and noise of the gold price time series without requiring seasonal components.

## Comparison with Linear Regression

| Model           | Target     | MAD   | SSE        |
|------------------|------------|--------|------------|
| Linear Regression| Buy Price  | 7.32  | 409,301.35 |
| Linear Regression| Sell Price | 7.50  | 432,874.63 |
| ARIMA            | Buy Price  | 0.1298| 471.86      |
| ARIMA            | Sell Price | 0.1282| 445.32      |

- ARIMA significantly outperforms Linear Regression in both MAD and SSE.
- Linear Regression fails to capture sudden price fluctuations, while ARIMA adjusts well to non-stationary behavior after differencing.

## Conclusion
- ARIMA is a more suitable model for forecasting gold prices in volatile markets.
- The model shows reliable short-term predictions with low error rates.
