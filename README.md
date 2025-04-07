# Stock-Data

RDDT Time Series Analysis

## Table of Contents

1. [Introduction](#introduction)
2. [Data](#data)
3. [Process Outline](#process-outline)
   1. [Initial Observation/Clean](#clean-data)
   2. [Analyze Data](#analyze-data)
   3. [Preprocess Data for Model](#preprocess-data-for-model)
   4. [Model Analysis/Prediction](#model-prediction/analysis)
4. [Next Steps](#next-steps)
5. [References](#references)

## 1 - Introduction <a name="introduction"></a>

I made predictions on Reddit (RDDT) stock using time series analysis. I used root mean squared error (RMSE) as the metric for success. RMSE gives the avergae size of prediction errors (i.e higher number means predicitons were further away from actual prices) so I was looking for a model that gave the lowest RMSE.

## 2 - Data <a name="data"></a>

I used the last year (251 trading days) of Reddit's daily closing stock prices for my analysis. I pulled the data using the YFinance Python library.

## 3 - Process Outline <a name="process-outline"></a>


### 3i - Initial Observations/Clean <a name="clean-data"></a>

RDDT went public in March 2024, just a few weeks before my dataset begins. This meant that I was unable to go further back in time for more meaningful data as the remaining information wasn't even an additional month.

Since the data came in from YFinance and consisted of close prices per market day, there were no nulls or duplicates.

### 3ii - Analyze Data <a name="analyze-data"></a>

#### Price Movement

![RDDT as of 04-04-2024](Images/RDDTasof20250404.png)

Between April 2024 and February 2025, the stock moved from approximately $50 to $225 per share for an increase of 450%. From February 2025 through the last close on April 4th 2025, the stock moved from approximately $225 to $87 a share for a decrease of 61%.

Both of these moves on their own would be considered large by normal stock market standards. Seeing them together in such a short timeframe is even more unusual. I wondered during my modeling if this would create issues with predictions. I used the last 50 observations as my test set, which means my test set encompasses the 61% drop that started in February. I kept note of this in case it looked ot be creating issues later in the process.

Due to the large price swings, the rolling mean and variances varied throughout the year and needed to be handled in preprocessing.

Upon checking for seasonality, the magnitude of seasonal variation at the weekly, monthly and quarterly levels were insignificant enough that I did not make any edit to the data to accoutn for seasonality.

### 3iii - Preprocess Data for Model <a name="preprocess-data-for-model"></a>

The data needed to be stationary to run through an ARIMA model. I took the log of the closing prices to smooth out the moving average. I took the difference of the closing prices over their previous close to smooth out the variance moving average.

### 3iv - Model Analysis/Prediction <a name="model-prediction/analysis"></a>

## 4 - Next Steps <a name="next-steps"></a>



## References <a name="references"></a>

\\
