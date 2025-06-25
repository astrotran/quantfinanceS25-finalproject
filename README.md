# A Machine-Learning Based Exploration into Quantitative Finance and Portfolio Theory

Erdos Quant Finance - Summer 2025

**Overview:**

In the age of machine learning methods in the computational sciences, methods such as pattern recognition, predictive modeling, and the handling of large datasets have become extremely relevant in quantitative finance. In this collection of mini projects, we use various methodologies in statistics, time series analysis, and machine learning to analyze stock data as well as explore common models in financial theory. This README serves to walk through each mini-project, highlighting key methods, results, and insights.

## 📈**Mini Project 1: Profitable Investment Portfolios**

**Objective:** Create two investment portfolios (high-risk and low-risk) using real stock data.

**Methods**:

- Used yfinance Python library to gather historical data for selected tickers
- Selected five stocks per portfolio. High risk stcks included TSLA, NVDA, META, AMZN, GOOG. Low-risk stocks included HD, MCD, PG, KO, JNJ.
- We weighted each portfolio equally and compute daily and cumulative returns.

**Results**: 

- The high-risk portfolio showed stronger growth over time but higher volatility.
- The low-risk portfolio was more stable with modest returns.
- Sharpe Ratios: High Risk ~0.91, Low-Risk ~0.69

- Higher risk led to higher average returns but with more volaitlity; serving as an example of the tradeoff between risk and return.


## 📊**Mini Project 2: Normality Testing of Log Returns**


**Objective:** test whether log returns of stocks are normally distributed.

**Methods:** 
- Used the Shapiro-Wilk, Anderson-Darling, and Jarque-Bera normality tests
- Applied tests on both globally and on rolling 60-day windows
- Removed outliers to test impact on normality

**Results:**
- Full-series tests often rejected normality.
- Removing outliers had a limited effect on the normality tests.
- Rolling windows showed that some periods passed the normality tests (e.g., ~70% of 60-day windows for NVDA)

- Log returns are not always normal, they can show normal-like behavior over shorter, stable periods.
