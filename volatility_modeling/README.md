# Volatility Modeling and Portfolio Construction of BlackRock ETFs

## Introduction

This project focuses on modeling the volatility of BlackRock ETFs that cover all 11 sectors within the S&P 500 from 2002 to 2024. The aim is to use GARCH(1,1) models and realized volatility to analyze and predict ETF volatility, and subsequently construct and compare various portfolios based on these volatility measures.

## Objectives

1. **Volatility Estimation**: Calculate volatility using GARCH(1,1) models and realized volatility.
2. **Volatility Prediction Models**: Define and apply four models to predict ETF volatility based on S&P 500 volatility.
3. **Portfolio Construction**: Construct portfolios based on different volatility measures and compare their performance.

## Data Acquisition

We sourced daily and monthly data for BlackRock ETFs and the S&P 500 ETF (IVV) from 2002 to 2024. The data includes:
- **Daily and Monthly Prices**
- **Returns**

## Methodology

### Volatility Calculation

1. **GARCH(1,1) Model**: Applied to monthly log returns to estimate the volatility of each ETF.
2. **Realized Volatility**: Calculated using daily log returns within each month.

### Volatility Prediction Models

1. **Model 1**:
![Model 1](https://latex.codecogs.com/png.latex?\sigma^{ETF}_{t}=\alpha^{ETF}+\beta^{ETF}\sigma^{S\&P500}_{t}+\varepsilon^{ETF}_{t})

2. **Model 2**:
![Model 2](https://latex.codecogs.com/png.latex?\sigma^{ETF}_{t}=\phi^{ETF}_{0}+\phi^{ETF}_{1}\sigma^{S\&P500}_{t}+\phi^{ETF}_{2}\sigma^{S\&P500}_{t-1}+\phi^{ETF}_{3}\sigma^{S\&P500}_{t-2}+\varepsilon^{ETF}_{t})

3. **Model 3**:
![Model 3](https://latex.codecogs.com/png.latex?\sigma'^{ETF}_{t}=\gamma^{ETF}_{0}+\gamma^{ETF}_{1}\hat{\sigma}^{ETF}_{t}+\varepsilon^{ETF}_{t})

where

![Equation](https://latex.codecogs.com/png.latex?\hat{\sigma}^{ETF}_{t}=\hat{\phi}^{ETF}_{0}+\hat{\phi}^{ETF}_{1}\sigma^{S\&P500}_{t}+\hat{\phi}^{ETF}_{2}\sigma^{S\&P500}_{t-1}+\hat{\phi}^{ETF}_{3}\sigma^{S\&P500}_{t-2})

4. **Model 4**:
![Model 4](https://latex.codecogs.com/png.latex?\sigma'^{ETF}_{t}=\gamma^{ETF}_{0}+\gamma^{ETF}_{1}\hat{\sigma}^{ETF}_{t-1}+\gamma^{ETF}_{2}\hat{\sigma}^{ETF}_{t-2}+\varepsilon^{ETF}_{t})

where

![Equation](https://latex.codecogs.com/png.latex?\hat{\sigma}^{ETF}_{t}=\hat{\phi}^{ETF}_{0}+\hat{\phi}^{ETF}_{1}\sigma^{S\&P500}_{t}+\hat{\phi}^{ETF}_{2}\sigma^{S\&P500}_{t-1}+\hat{\phi}^{ETF}_{3}\sigma^{S\&P500}_{t-2})

### Portfolio Construction

We constructed and compared the following portfolios:

1. **Value-Weighted Portfolio**: Based on the IVV ETF.
2. **Equal-Weighted Portfolio**: Equal investment in each ETF.
3. **Constant Volatility Portfolio**: Constructed using a simple method (standard deviation ) to calculate volatility.
4. **GARCH Portfolio**: Based on GARCH model volatility.
5. **Realized Volatility Portfolio**: Based on realized volatility.

### Portfolio Comparison Metrics

- **Return**: Average return of the portfolio.
- **Sharpe Ratio**: Risk-adjusted return of the portfolio.
- **Information Ratio**: Performance relative to a benchmark.
- **CER (Certainty Equivalent Return)**: The guaranteed return an investor would accept instead of a risky portfolio.
- **Turnover**: Frequency of rebalancing the portfolio.

## Results and Analysis

The performance of each portfolio was evaluated based on the above criteria.

### Conclusion

This project demonstrates the application of GARCH and realized volatility models to predict ETF volatility and construct optimized portfolios. By comparing different portfolio construction methods, the project provides insights into the relationship between ETF volatility and the overall market volatility, represented by the IVV ETF. The analysis highlights the effectiveness of various models in predicting volatility and optimizing portfolio performance.
