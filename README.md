# Cross-Sectional Equity Alpha Research

A quantitative research project investigating cross-sectional equity signals and market-neutral portfolio construction.

The project develops a reproducible pipeline for:

* equity data preparation and validation
* cross-sectional factor construction
* forward-return labeling
* time-series out-of-sample validation
* linear and regularized regression baselines
* Information Coefficient (IC) analysis
* market-neutral portfolio construction
* portfolio performance evaluation

## Current Status

**Work in progress.**

The `main` branch contains the current **working baseline pipeline** developed during the initial learning and implementation phase.

Active research and further development are being carried out in the [`dev`](../../tree/dev) branch, including improvements to data handling, factor research, statistical validation, portfolio construction, and robustness analysis.

## `learn/`

The `learn/` directory contains the initial end-to-end implementation used to understand the workflow of a quantitative equity research pipeline.

The current pipeline follows:

```text
S&P 500 data
     ↓
Data cleaning & validation
     ↓
Factor construction
     ↓
Forward-return labeling
     ↓
Time-series cross-validation
     ↓
Linear / Ridge regression
     ↓
Out-of-sample predictions
     ↓
Market-neutral portfolio
     ↓
Performance evaluation
```

The baseline implementation currently uses three cross-sectional factors:

* Momentum
* Mean reversion
* Volatility

Models are evaluated using out-of-sample Spearman Information Coefficient, while the resulting portfolio is evaluated using metrics including Sharpe ratio, maximum drawdown, and cumulative return.

## Research Direction

The baseline pipeline is intentionally simple. The next stage of the project focuses on turning the pipeline into a research framework by systematically investigating factor hypotheses, model choices, robustness, and realistic trading constraints.

See the `dev` branch for ongoing development.