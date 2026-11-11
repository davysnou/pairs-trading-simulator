---
layout: default
title: Quantitative Methodology & Model Notes
---

# Quantitative Methodology & Statistical Arbitrage Notes

[← Launch Interactive Simulator](./)

---

## 1. Return Correlation vs. Cointegration
A common pitfall in statistical arbitrage is treating high short-term return correlation ($\rho$) as evidence of a tradable spread:

* **Return Correlation:** Measures linear co-movement of first differences ($\Delta P_{A,t}, \Delta P_{B,t}$). Two assets can maintain $\rho > 0.85$ while drifting infinitely far apart in price levels.
* **Cointegration ($I(0)$ Spread):** Exists when a linear combination $S_t = P_{B,t} - \beta P_{A,t}$ is stationary with constant mean and finite variance over time.

---

## 2. Ornstein-Uhlenbeck Mean Reversion & Half-Life
In **Practical Mode**, cointegrated spreads follow a discrete-time Ornstein-Uhlenbeck (OU) process:

$$\Delta S_t = \theta (\mu - S_{t-1})\Delta t + \sigma \varepsilon_t$$

* **Mean-Reversion Speed ($\theta$):** Controlled by the *Cointegration Strength* slider.
* **Half-Life of Mean Reversion:** Indicates the expected number of bars for a shock to decay halfway back to equilibrium:

$$t_{1/2} = \frac{\ln(2)}{\theta}$$

---

## 3. Signal Generation & Risk Management
* **Rolling Z-Score Normalization:**
  $$Z_t = \frac{S_t - \bar{S}_w}{s_{S,w}}$$
* **Entry Triggers:** Long spread when $Z_t \le -2.0$, short spread when $Z_t \ge +2.0$.
* **Mean-Reversion Exit:** Close position when $Z_t$ crosses $0.0$.
* **Tail-Risk Stop-Loss:** Hard liquidation at $|Z_t| \ge 3.5$ to protect against structural regime breaks.
* **Execution Friction:** Deducts round-trip slippage and commissions in basis points (`bps/leg`) across both legs.

---

## 4. Roadmap & Feedback
* Custom rolling Z-score entry/exit thresholds
* Institutional risk-adjusted metrics (**Sharpe, Sortino, and Information Ratios**)
* Rolling hedge ratio ($\beta$) estimation via OLS / Kalman Filter

Have suggestions? [Open an Issue on GitHub](https://github.com).
