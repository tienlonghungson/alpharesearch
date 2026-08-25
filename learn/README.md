# Cross-Sectional Equity Alpha Research Platform

## Project Description

This project aims to build an **quantitative equity research pipeline** project. The objective is to simulate the a workflow of quantitative research.

Instead of predicting the absolute future price of a stock, the project focuses on **cross-sectional prediction**: given a universe of stocks on a trading day, rank them according to their expected future performance. These rankings are then converted into a market-neutral long-short portfolio and evaluated using metrics commonly used in quantitative finance.

The emphasis is not on maximizing predictive accuracy with complex models, but on developing a **rigorous, reproducible, and explainable research pipeline**.

The project should demonstrate:

* rigorous data engineering
* hypothesis-driven factor research
* statistically sound model validation
* realistic portfolio construction
* software engineering best practices
* every design decision must be explainable

---

# Fixed Design Decisions

## Universe

* US equities
* Fixed S&P 500 universe for the initial project

## Data Source

Phase 1:

* Yahoo Finance (`yfinance`)

Future upgrade (optional):

* CRSP / WRDS (point-in-time data)

## Prediction Target

Predict the **cross-sectional rank** of future returns instead of absolute returns.

Example:

For a given trading day,

* Stock A → top 5%
* Stock B → middle
* Stock C → bottom 5%

The model learns to distinguish relative winners from losers.

## Initial Factors

The first implementation will use a small number of classical factors, such as

* Momentum
* Mean Reversion
* Volatility

Additional factors can be introduced later after establishing a solid baseline.

## Initial Model

Progression:

* Linear Regression
* Ridge Regression
* Lasso Regression

Only after establishing the linear baseline should more complex models (Random Forest, Gradient Boosting, etc.) be investigated.

## Evaluation

The primary metrics are

* Information Coefficient (IC)
* Information Ratio (ICIR)
* Sharpe Ratio
* Maximum Drawdown

---

# Learning & Baseline

## Objective

Become familiar with quantitative research terminology, workflows, and software architecture by implementing a complete but minimal end-to-end factor model.

The goal is **understanding**.

---

## Learning Goals

Understand:

* what a stock universe is
* panel data (date × ticker)
* factor engineering
* cross-sectional prediction
* alpha
* long-short portfolios
* Information Coefficient
* Sharpe Ratio
* market neutrality
* backtesting workflow

---

## Milestones

### Milestone 1 — Data

* Download S&P 500 daily OHLCV data using `yfinance`
* Build a reproducible data pipeline
* Store cleaned data in an efficient format (e.g., Parquet)
* Document known limitations (e.g., survivorship bias)

### Milestone 2 — Factor Engineering

Implement several classical factors using vectorized Pandas operations:

* Momentum
* Mean Reversion
* Volatility

Learn how each factor is defined mathematically and why it may have predictive value.

### Milestone 3 — Labels

Construct the prediction target:

* forward returns
* cross-sectional percentile ranks

### Milestone 4 — Baseline Model

Train a simple linear model:

* Linear Regression
* Ridge Regression

Use proper time-series validation (e.g., `TimeSeriesSplit`) to avoid lookahead bias.

### Milestone 5 — Portfolio

Implement a simple market-neutral portfolio:

* Long top decile
* Short bottom decile
* Equal weights

### Milestone 6 — Evaluation

Evaluate the strategy using

* Information Coefficient
* Sharpe Ratio
* Cumulative returns
* Maximum Drawdown

---