# Portfolio Risk Simulation (Market Risk)

This project analyses the market risk of a simple equity portfolio using
historical data and Monte Carlo simulation techniques.

The focus is on **risk measurement and downside risk**, rather than return
optimisation or trading strategies.

---

## Project Overview

A portfolio consisting of Apple (AAPL), Microsoft (MSFT), and Google (GOOG)
is constructed using fixed asset weights.

Using historical daily returns from 2023, the project:

- estimates portfolio volatility using the covariance matrix
- simulates future portfolio values over a one-year horizon (252 trading days)
- quantifies downside risk using Value at Risk (VaR) and Conditional Value at Risk (CVaR)

Monte Carlo simulation is used to generate a distribution of possible future
portfolio outcomes.

---

## Methodology

### Data
- Daily closing prices obtained via Yahoo Finance
- Assets: AAPL, MSFT, GOOG
- Period: January 2023 – December 2023

### Portfolio Construction
- Fixed portfolio weights (not optimised)
- Daily portfolio returns computed as weighted sums of asset returns

### Risk Estimation
- Portfolio variance calculated using the covariance matrix of returns
- Portfolio volatility derived as the square root of variance

### Monte Carlo Simulation
- Daily portfolio returns converted to log returns
- Log returns assumed to be normally distributed
- Simulated over 252 trading days and 10,000 scenarios
- Final portfolio values obtained via cumulative exponentiation

### Risk Metrics
- **Value at Risk (VaR)** at the 95% confidence level
- **Conditional Value at Risk (CVaR)** at the 95% confidence level

---

## Key Outputs

- Simulated portfolio value paths over one year
- Distribution of final portfolio values
- Estimated VaR and CVaR measures based on simulated outcomes

Example outputs can be found in the `plots/` directory.

---

## Limitations

This analysis makes several simplifying assumptions:

- returns are independent and identically distributed
- volatility and correlations remain constant over time
- returns follow a normal distribution
- extreme market events are not explicitly modelled
- transaction costs, taxes, and portfolio rebalancing are ignored

Results are illustrative and are not intended as forecasts or investment advice.

---

## Tools and Libraries

- Python
- pandas
- numpy
- matplotlib
- yfinance

---

## Notes

This project is intended as a demonstration of market risk concepts and
Monte Carlo simulation techniques commonly used in actuarial and financial
risk analysis.
