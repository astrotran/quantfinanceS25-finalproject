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

## ⚖️ **Mini Project 3: Option Sensitivities in the Black-Scholes Model**

**Objective:** Explore and visualize option sensitivities (Greeks) using the Black-Scholes model.

**Methods:**

- Implemented call and put pricing formulas
- Calculated and plotted:
  - **Delta**: sensitivity to changes in the underlying stock price
  - **Theta**: sensitivity to time decay
- Used a range of spot prices to examine behaviors

**Results:**

- **Call Delta** increases with spot price; **Put Delta** is negative and decreases
- **Theta** shows stronger decay near expiration and for at-the-money options

- The Greeks give important intuition for hedging and risk management. We observed classic textbook behavior in visual form.


## 📉 **Mini Project 4: Heston Model, Delta Hedging & ML**

**Objective:** Model non-constant volatility with the Heston model, simulate hedging, and use ML to predict hedge performance.

**Methods:**

1. **Simulated paths using the Heston Model**

   - Introduced stochastic volatility
   - Parameters:  
     - Initial spot price $S_0 = 100$, initial variance $v_0 = 0.04$ 
     - Mean reversion $\kappa = 2.0$, long-run variance $\theta = 0.04$  
     - Vol of vol $\sigma_v = 0.3$, correlation $\rho = -0.7$, $T = 1 \text{ year}$
   - Compared to Geometric Brownian Motion (GBM)

2. **Implemented Delta Hedging**

   - Hedged short call positions
   - Tracked P&L under different rebalance frequencies
   - Compared P&L under GBM vs Heston

3. **Hedging Error Analysis**

   - Computed hedging error over time and compared **standard deviations**:
     - Heston: ~6.42  
     - GBM: ~6.36  
   - Demonstrated that **stochastic volatility increases hedge error variance**.

4. **Machine Learning Classification**

   - Framed a classification task: Will a hedge produce high error?
   - Used features like final price, realized vol, moneyness
   - Trained models:
     - **Logistic Regression** (baseline)
     - **Random Forest**
     - **XGBoost**
    
5. **Volatility Smile Analysis**  
   - Generated a **volatility smile** by plotting implied volatilities of Heston-simulated call prices across strikes.  
   - Found the classic smile shape:
     - Higher IV for deep in-the-money and out-of-the-money options
     - Peak IV near at-the-money
   - This confirmed the Heston model’s ability to **capture market-observed IV behavior**, unlike Black-Scholes.

**Results:**

- **XGBoost** achieved:
  - 93.5% accuracy
  - 98% precision on identifying high-error cases
- Feature importance showed **final price** and **realized volatility** were the most predictive
- Added a **vega hedging strategy** using a second option, which improved performance in volatile scenarios by reducing exposure to volatility shifts in highly stochastic environments.

- The Heston model captures more realistic market dynamics but is harder to hedge.
- Machine learning can help identify hedge risk ahead of time and potentially optimize strategies.


## 🚀 Conclusion

This repo reflects a full progression through real-world financial modeling problems, from classicial portfolio theory to modern methods in machine learning for hedge evaluation. Future work may include the implementation of other ML models like transformers. We may also explore other volatility models like SABR or GARCH. 

Thanks for checking it out!

---


