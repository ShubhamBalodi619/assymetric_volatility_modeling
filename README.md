# Cross-Asset Asymmetric Volatility Dynamics: A GJR-GARCH Framework

## 📊 Project Overview
This project investigates **Volatility Clustering** and the **Asymmetry of Shocks** (the "Leverage Effect") across three distinct asset classes: Broad Equities (**S&P 500**), Commodities (**WTI Crude Oil**), and Real Estate (**Prologis**). 

By implementing the **Glosten-Jagannathan-Runkle (GJR) - GARCH** framework, we quantify how these assets respond differently to market stress. This analysis is critical for modern financial functions, including Value-at-Risk (VaR) estimation, derivative pricing, and portfolio risk management.

## 🛠️ Technical Stack
* **Language:** Python 3.x
* **Modeling:** `arch` library (GJR-GARCH implementation)
* **Data Analysis:** `pandas`, `numpy`, `scipy`
* **Visualization:** `matplotlib`, `seaborn`
* **Econometrics:** `statsmodels` (ADF Test, Ljung-Box Test)

## 🧮 Methodology
The project followed a rigorous econometric pipeline to ensure model integrity:
1.  **Exploratory Data Analysis (EDA):** Visualization of log returns and distribution analysis to identify stylized facts of financial time series.
2.  **Stationarity Testing:** Augmented Dickey-Fuller (ADF) tests were used to ensure the series were mean-reverting.
3.  **ARCH Effect Verification:** Ljung-Box tests on squared residuals confirmed the presence of conditional heteroscedasticity.
4.  **Model Fitting:** Estimation of GJR-GARCH(1,1,1) parameters using a **Standardized Student’s t-distribution** to account for heavy tails ($\nu$).
5.  **Validation:** Post-estimation Ljung-Box tests to ensure residuals behave as white noise (no remaining autocorrelation).
6.  **Forecasting:** Generation of 10-day conditional volatility projections showing mean reversion paths.

## 📈 Quantitative Comparison: The "Volatility DNA"
Our research successfully mapped the unique risk signatures of each asset class:

| Parameter | **S&P 500 (Equity)** | **WTI Crude Oil (Commodity)** | **Prologis (Real Estate)** |
| :--- | :--- | :--- | :--- |
| **$\omega$ (Constant)** | 0.0261 | 0.1202 | 0.0388 |
| **$\alpha$ (ARCH - News Reactivity)** | 0.0044 | **0.0564** | 0.0375 |
| **$\gamma$ (Gamma - Asymmetry)** | **0.2755** | 0.0749 | 0.0631 |
| **$\beta$ (GARCH - Persistence)** | 0.8369 | 0.8822 | **0.9155** |
| **$\nu$ (Nu - Degrees of Freedom)** | **5.6716** | 6.3618 | 7.2256 |

### Key Strategic Takeaways:
* **The Fear Factor:** The **S&P 500** exhibits a massive leverage effect ($\gamma = 0.27$). Volatility is almost exclusively driven by downside panic. It also has the lowest $\nu$, indicating the highest exposure to "Black Swan" events.
* **The Immediate Responder:** **WTI Crude Oil** is the most reactive to daily news ($\alpha = 0.056$). It processes new information—both positive and negative—much faster than the other assets.
* **The Sticky Risk:** **Prologis** shows the highest persistence ($\beta = 0.91$). In the real estate sector, volatility is structural; once a shock occurs, it lingers far longer than in the equity or commodity markets.

