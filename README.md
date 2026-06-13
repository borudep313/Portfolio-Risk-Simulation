# Portfolio Risk Simulation and Portfolio Analysis

This project analyses portfolio risk, diversification, market exposure, and simulated future performance using historical equity return data and Monte Carlo simulation techniques.

The project compares a concentrated technology portfolio against a more diversified portfolio and explores how diversification affects risk, return, correlation structure, systematic risk, and downside risk.

---

## Project Overview

Two equally weighted portfolios are constructed:
- Technology Porfolio: AAPL, MSFT, GOOG, NVDA, AMD, INTC, AMZN, TSLA, ADBE, CSCO.
- Diversified Portfolio: AAPL, MSFT, GOOG, NVDA, JPM, XOM, WMT, JNJ, GLD, SPY.

Using daily return data from 2015-2023, the project investigates:
-  portfolio expected return and volatility
-  covariance and correlation structures
-  diversification effects
-  feasible portfolio risk-return combinations
-  beta and CAPM analysis
-  rolling market exposure (rolling beta)
-  Monte Carlo simulation of future portfolio values
-  downside risk measures using VaR and CVaR

---

## Methodology

### Data Collection
- Daily closing prices obtained using Yahoo Finance
- Period: January 2015 – December 2023
- Returns calculated using daily percentage (relative) change.

### Portfolio Statistics
The following statistics are calculated for each portfolio:
- Expected return:

$$E(R_p) = w^T\mu$$


- Portfolio variance:


$$\sigma^2_p = w^T\Sigma w$$
- Portfolio volatility:


$$\sigma_p = \sqrt{w^T\Sigma w}$$


where:
- w is the weight vector
- µ is the vector of mean returns
- Σ is the covariance matrix of returns

### Correlation Analysis
Correlation matrices are constructed and visualised to examine relationships between portfolio assets and to explain differences in diversification effectiveness.

### Diversification Experiment
Portfolio volatility is evaluated as the number of assets increases.

This illustrates:
- reduction of unsystematic risk through diversification
- diminishing marginal benefits of additional assets
- persistence of systematic market risk

### Feasible Portfolio Simulation
5000 random portfolio weight combinations are generated for each portfolio's asset universe, thus creating 5000 portfolios of random weights from each list of assets.

For each portfolio, expected return and volatility are calculated.

The resulting feasible portfolio sets illustrate the risk-return trade-off available within each asset univers.

### Beta and CAPM Analysis
Asset betas are estimated relative to SPY:


$$\beta_i = \frac{Cov(R_i,R_m)}{Var(R_m)}$$


CAPM expected returns are then calculated:


$$E(R_i) = R_f + \beta_i(E(R_m)-R_f)$$


Historical returns are compared with CAPM estimates to investigate alpha and deviations from market-risk based predictions.
Rolling one-year beta estimates are also calculated for both portfolios, allowing examination of how market exposure changes over time and the effect of diversification on beta variability and stability of systematic risk.

### Monte Carlo Simulation
Future portfolio values are simulated over a one-year horizon (252 trading days), for both portfolios.

The simulation uses:
- Historical mean returns
- Historical covariance matrices
- Multivariate normal return generation
- Cholesky decomposition to preserve correlation structure
Simulated asset returns are generated accorting to:


$$X=\mu+ZL$$


where:
- Z contains independent standard normal draws
- L is the Cholesky factor of the covariance matrix
- µ is the vector of historical average returns
Portfolio wealth is accumulated using compounded daily returns:


$$W_t = \prod_{i=1}^{t}(1+r_i)$$


10000 simulations are performed for each portfolio.
  
### Risk and Return Metrics
Monte Carlo outcomes are analysed using:
- Mean final wealth
- Variance and standard deviation
- Minimum and maximum outcomes
- 95% Value at Risk (VaR)
- 95% Conditional Value at Risk (CVaR)
- Probability of loss
These measures provide insight into both expected performance and downside risk.

---

## Key Findings
- The technology portfolio produced higher historical returns but substantially higher volatility.
- Diversification reduced portfolio volatility through lower correlations between assets.
- Technology stocks generally exhibited higher market beta values.
- Portfolio beta varied over time rather than remaining constant.
- Monte Carlo simulations showed higher expected wealth for the technology portfolio but also greater downside risk.
- Risk and return exhibited a clear trade-off across all analyses.

---

## Limitations

This project makes several simplifying assumptions:
- historical return distributions remain representative of the future
- means, variances and covariances remain constant
- returns follow a multivariate normal distribution
- extreme market events are not explicitly modelled
- transaction costs, taxes, and rebalancing are ignored
- survivorship and look-ahead bias exist in asset selection

Results are intended for educational purposes and should not be interpreted as investment advice.

---

## Tools and Libraries

- Python
- pandas
- numpy
- matplotlib
- seaborn
- yfinance

---

## Project Purpose
This project was developed as a practical exploration of portfolio theory, diversification, market risk, CAPM, and Monte Carlo simulation techniques commonly used in actuarial science, quantitative finance, and risk management.
