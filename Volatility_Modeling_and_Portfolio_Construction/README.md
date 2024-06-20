# Volatility Modeling and Portfolio Construction Using BlackRock's Sector ETFs 

## Overview

This project focuses on modeling the volatility of BlackRock ETFs covering all 11 sectors within the S&P 500 from 2002 to 2024. The aim is to use GARCH(1,1) models and realized volatility to analyze and predict ETF volatility, and subsequently construct and compare various portfolios based on these volatility measures.

## Objectives

1. **Volatility Estimation**: Calculate volatility using both GARCH(1,1) models and realized volatility.
2. **Volatility Prediction Models**: Define and apply four models to predict ETFs volatility based on S&P 500 volatility.
3. **Portfolio Construction**: Construct portfolios based on different volatility measures and models, and compare their performance.

## Data Acquisition

We sourced the risk-free rate for each month, as well as daily and monthly data for BlackRock's 11 sector ETFs and its S&P 500 ETF (IVV) from the CRSP dataset, covering the period from 2002 to 2024. The data includes:
- **Daily and Monthly Prices**
- **Daily and Monthly Returns**
- **Risk-Free Rates per Month**

## Installation Instructions
To run the notebook, you need Python and the following libraries:
- pandas, numpy, wrds, arch, statsmodels, matplotlib, tabulate

## Methodology

### Volatility Calculation

1. **GARCH(1,1) Model**: Applied to monthly log returns to estimate the volatility of each ETF.
2. **Realized Volatility**: Calculated using daily log returns within each month.

### Volatility Prediction Models

1. **Model 1:**
![Model 1](https://latex.codecogs.com/svg.image?{\color{Red}\sigma^{ETF}_{t}=\alpha^{ETF}&plus;\beta^{ETF}\sigma^{SP500}_{t}&plus;\varepsilon^{ETF}_{t}})

2. **Model 2:**
![Model 2](https://latex.codecogs.com/svg.image?{\color{Red}\sigma^{ETF}_{t}=\phi^{ETF}_{0}&plus;\phi^{ETF}_{1}\sigma^{SP500}_{t}&plus;\phi^{ETF}_{2}\sigma^{SP500}_{t-1}&plus;\phi^{ETF}_{3}\sigma^{SP500}_{t-2}&plus;\varepsilon^{ETF}_{t}})

3. **Model 3:**
![Model 3](https://latex.codecogs.com/svg.image?{\color{Red}\sigma'^{ETF}_{t}=\gamma^{ETF}_{0}&plus;\gamma^{ETF}_{1}\hat{\sigma}^{ETF}_{t}&plus;\varepsilon^{ETF}_{t}})

where 

![Model 3-1](https://latex.codecogs.com/svg.image?{\color{Red}\sigma'^{ETF}_{t}=\gamma^{ETF}_{0}&plus;\gamma^{ETF}_{1}\hat{\sigma}^{ETF}_{t}&plus;\varepsilon^{ETF}_{t}})

4. **Model 4:**
![Model 4](https://latex.codecogs.com/svg.image?{\color{Red}\sigma'^{ETF}_{t}=\gamma^{ETF}_{0}&plus;\gamma^{ETF}_{1}\hat{\sigma}^{ETF}_{t-1}&plus;\gamma^{ETF}_{2}\hat{\sigma}^{ETF}_{t-2}&plus;\varepsilon^{ETF}_{t}})

where 

![Model 4-1](https://latex.codecogs.com/svg.image?{\color{Red}\hat{\sigma}^{ETF}_{t}=\hat{\phi}^{ETF}_{0}&plus;\hat{\phi}^{ETF}_{1}\sigma^{SP500}_{t}&plus;\hat{\phi}^{ETF}_{2}\sigma^{SP500}_{t-1}&plus;\hat{\phi}^{ETF}_{3}\sigma^{SP500}_{t-2}})

### Portfolio Construction

We constructed the following portfolios for each volatility prediction model:

1. **GARCH Portfolio**: Based on GARCH(1,1) model volatility.
2. **Realized Volatility Portfolio**: Based on realized volatility.

and compared their performance with the following portfolios:

1. **Value-Weighted Portfolio**: Based on the IVV ETF.
2. **Equal-Weighted Portfolio**: Equal investment in each sector ETF.
3. **Constant Volatility Portfolio**: Constructed based on a simple method of volatility estimation (standard deviation).

- Note: The weight of each ETF in the GARCH and realized volatility portfolios was determined by:
$$W^{ETF}_{t} = \frac{\bar{\mu_{0,t}}}{\hat{\sigma}^{ETF}_{t}}$$
where ${\bar{\mu_{0,t}}}$ is the average log return of the ETF from time 0 to t.

### Portfolio Evaluation Metrics

- **Return**: Average return of the portfolio.
- **Sharpe Ratio**: Risk-adjusted return of the portfolio.
- **Information Ratio**: Performance relative to the benchmark (S&P 500 index ETF or IVV).
- **CER (Certainty Equivalent Return)**: The guaranteed return an investor would accept instead of a risky portfolio.
- **Turnover**: Frequency of rebalancing the portfolio.

## Results

The performance of each portfolio was evaluated based on the above criteria:

| Portfolio                              | Annual Sharpe Ratio | Annual Information Ratio | Annual CER | Average Annual Turnover |
|----------------------------------------|---------------------|--------------------------|------------|-------------------------|
| Value-weighted Portfolio               | 0.3165              | -                        | 0.008      | -                       |
| Equal-weighted Portfolio               | 0.27                | -0.2016                  | -0.0003    | 2.9824                  |
| Constant Volatility Portfolio          | 0.2942              | -0.0639                  | 0.004      | 0.1365                  |
| GARCH Portfolio (Model 1)              | 0.294               | -0.0757                  | 0.0042     | 0.1341                  |
| Realized Volatility Portfolio (Model 1)| 0.2906              | -0.0866                  | 0.0037     | 0.1348                  |

### Conclusion

This project demonstrates the application of GARCH and realized volatility models to predict ETF volatility and construct optimized portfolios. By comparing different portfolio construction methods, the project provides insights into the relationship between ETF volatility and overall market volatility, represented by the IVV ETF. Although this analysis highlights the effectiveness of Model 1 relative to other models in predicting volatility and optimizing portfolio performance, none of the portfolios constructed using GARCH and realized volatility achieved better performance than the value-weighted portfolio (IVV).
