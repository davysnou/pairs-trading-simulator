# pairs-trading-simulator

# Pairs Trading & Spread Simulator

[![Live Demo](https://shields.io)](https://github.io)
[![License: MIT](https://shields.io)](LICENSE)

An interactive, browser-based quantitative finance simulator illustrating the difference between **short-term return correlation** and **long-run statistical cointegration**, complete with a mean-reversion backtesting engine.

🔗 **Live Web App:** [https://github.io](https://github.io)

---

## Key Features

### 1. Learner Mode (Intuition Builder)
* **Regime Comparison:** Toggle between *Cointegrated* (mean-reverting equilibrium) and *Concurrent Move* (correlated returns with permanent price drift).
* **Stochastic Controls:** Adjust **Path Volatility** and **Divergence Drift** in real time or reseed random shocks.
* **Summary Diagnostics:** Tracks Pearson correlation, maximum spread deviation, and average spread.

### 2. Practical Mode (Strategy Backtester)
* **Real-World Ticker Presets:** Calibrated dynamics for *Gold vs. Silver*, *WTI vs. Brent Crude*, *Visa vs. Mastercard*, *Bitcoin vs. Ethereum*, and *AAPL vs. MSFT*.
* **Z-Score Signals & Risk Controls:** Plots rolling **±2σ entry bands** (`▲` Long / `▼` Short) alongside optional **±3.5σ stop-loss protection** (`✕`).
* **Stationarity Diagnostics:** Compares **Rolling Correlation** against a rolling **Augmented Dickey-Fuller (ADF) p-value** (`p < 0.05` signals stationarity).
* **Execution Realism & Reporting:** Models per-leg transaction costs/slippage (`bps`), tracks cumulative net equity and drawdown, accepts custom **historical CSV uploads**, and exports complete **trade logs to CSV**.

---

## Methodology Overview

1. **Rolling Spread Z-Score:**
   $$Z_t = \frac{S_t - \mu_{S, w}}{\sigma_{S, w}}$$
   where $S_t = P_{B,t} - P_{A,t}$ is the raw spread over a rolling window $w$.
2. **Stationarity Verification:** Uses an Augmented Dickey-Fuller (ADF) regression ($\Delta S_t = \gamma S_{t-1} + \varepsilon_t$) to distinguish true mean reversion from random-walk divergence.

---

## Feedback & Contributions
Have an idea for a new preset, risk metric, or chart? Open an issue in the **[Issues](../../issues)** tab or submit a pull request.
