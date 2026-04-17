# 🛢️ Petrocurrency Statistical Arbitrage Engine

> A quantitative research project exploring the "Oil Money" hypothesis through cointegration analysis and mean-reversion trading strategies between Brent Crude and the Norwegian Krone (NOK).

---

## 📌 Overview
This engine implements a **Statistical Arbitrage** strategy based on the correlation between global commodity benchmarks and "Petrocurrencies." Specifically, it models the relationship between Brent Crude Oil prices and the NOK/USD exchange rate to identify alpha-generating dislocations.

Built for **Quantamental** research, the project bridges the gap between macro-economic theory and systematic execution.

---

## 🧠 Mathematical Framework

The core logic assumes that the currency $Y$ (e.g., NOK/USD) is a function of the commodity $X$ (Brent Crude):

$$Y_t = \beta X_t + \alpha + \epsilon_t$$

Where:
* **$\beta$**: The hedge ratio (sensitivity of the currency to oil).
* **$\alpha$**: The constant intercept (regime baseline).
* **$\epsilon_t$**: The residual (the "spread" or mispricing).

### **Signal Generation**
We calculate the **Z-Score** of the residuals to determine if the currency is overvalued or undervalued relative to its historical relationship with oil:

$$Z_t = \frac{\epsilon_t - \mu_{\epsilon}}{\sigma_{\epsilon}}$$

* **Short Signal:** $Z_t > +2.0$ (Currency is too strong relative to oil).
* **Long Signal:** $Z_t < -2.0$ (Currency is too weak relative to oil).

---

## 🛠️ Key Features
* **Cointegration Testing:** Utilizes the **Augmented Dickey-Fuller (ADF)** test to ensure the spread is stationary (mean-reverting).
* **Dynamic Hedging:** Calculates time-varying beta coefficients using rolling window regressions.
* **Risk Analytics:** Computes Sharpe Ratio, Max Drawdown, and cumulative returns for the strategy.
* **Automated Data Pipeline:** Fetches historical spot prices for Brent and FX pairs via Yahoo Finance/Pandas-Datareader.

---

## 📊 Performance Metrics
* **Statistical Significance:** High R-squared values ($>0.70$) during stable macro regimes.
* **Alpha Generation:** Consistent returns by exploiting short-term divergences during oil supply shocks.
* **Convergence:** Validated mean-reversion behavior within 10-15 trading days.

---

## 🚀 Quick Start
```bash
# Clone the repository
git clone [https://github.com/vedakshari1-collab/Oil-Money-project.git](https://github.com/vedakshari1-collab/Oil-Money-project.git)

# Install dependencies
pip install pandas numpy statsmodels matplotlib yfinance

# Run the research notebook
jupyter notebook Oil_Money_Analysis.ipynb
