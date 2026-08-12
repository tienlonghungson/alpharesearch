# This Is Learn Folder - A Scratch Space
This folder is not part of the project. It is just a scratch folder storing everything I learnt to build the project, including my notes, my discussion with Gemini and ChatGPT, how I set the goal, and plan to of the project. Below is the summary of the project.

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

# Two-Phase Development Plan

The project will be developed in two distinct phases.

---

# Phase 0 — Learning & Baseline

## Objective

Become familiar with quantitative research terminology, workflows, and software architecture by implementing a complete but minimal end-to-end factor model.

The goal is **understanding**, not novelty.

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

## Deliverables

Repository with a clean software engineering structure:

```text
equity-alpha/

learn/
    notebooks for exploration

src/
    data/
    factors/
    labels/
    models/
    portfolio/
    evaluation/

tests/

report/
```

The notebooks in `learn/` are for experimentation and learning only. The actual implementation belongs in `src/`.

---

# Phase 1 — Research Project

## Objective

Transform the baseline implementation into an institutional-quality quantitative research project suitable for internship applications.

The focus shifts from learning to conducting original, defensible research.

---

## Milestone 1 — Data Engineering

* Improve data validation
* Improve reproducibility
* Clearly document assumptions and limitations
* Prepare for future migration to point-in-time datasets

---

## Milestone 2 — Factor Research

Expand the factor library.

For every new factor:

1. State the hypothesis.
2. Explain the financial intuition.
3. Implement the factor.
4. Test its predictive power.

Perform:

* factor pretests
* Information Coefficient analysis
* correlation analysis
* factor screening

---

## Milestone 3 — Modeling

Compare multiple approaches:

* Ridge
* Lasso
* Elastic Net
* Tree-based models (only if justified)

Perform:

* feature importance analysis
* ablation studies
* sensitivity analysis

---

## Milestone 4 — Portfolio Construction

Progressively improve the allocator:

* equal-weight market-neutral
* convex optimization (`cvxpy`)
* sector neutrality
* turnover constraints
* transaction costs
* risk constraints

---

## Milestone 5 — Robustness

Stress-test the strategy.

Examples:

* different lookback windows
* different rebalance frequencies
* different transaction costs
* bootstrap confidence intervals
* statistical significance tests

---

## Milestone 6 — Methodological Contribution (Optional)

Possible directions include:

* graph-based stock clustering
* dynamic similarity graphs
* approximation algorithms for NP-hard portfolio optimization under cardinality or integer constraints
* novel factor construction inspired by graph or clustering methods

The contribution should solve a genuine problem rather than introducing complexity for its own sake.

---

# Final Deliverables

The completed project should include:

1. **A reproducible GitHub repository**

   * Modular Python package
   * Tests
   * Documentation
   * Reproducible pipeline

2. **An academic-style technical report (8–15 pages)**

   * Abstract
   * Background
   * Data
   * Methodology
   * Experimental Results
   * Robustness Analysis
   * Limitations
   * Future Work

3. **An interview slide deck (10–15 slides)**

   * Problem statement
   * Research workflow
   * Methodology
   * Results
   * Lessons learned
   * Discussion and future improvements
