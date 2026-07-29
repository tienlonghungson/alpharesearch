# Requirements
1. **Research requirements**
   * What hypotheses or questions should the platform answer?
   
   The platform should be able to perform experiments to answer the following questions: How well do these factors explain returns on my chosen universe? How stable are the estimated factor exposures over time? Does adding a new factor improve predictive performance? Which factor model produces better out-of-sample rankings? How sensitive are results to estimation choices (window length, rebalance frequency, regression method)?
   
2. **Software requirements**
   * What actions should a researcher be able to perform to answer those questions?

   The researcher should be able to configure, execute, and compare multiple quantitative experiments while changing one or more components (factor model, estimator, portfolio construction, evaluation metric, etc.), with the framework ensuring that all other conditions remain consistent.
   
# Design
The Modular Factor Research Platform: Component Summary
- Experiment (The Orchestrator): The master record. A reproducible specification that defines exactly which data, model, estimator, strategy, and backtest configurations are being used for a single run.
- Dataset (The Raw Reality): Provides clean, point-in-time aligned historical market data. It does no math; it only serves prices and volumes.
- Factor Model (The Hypothesis): Defines the structural equation (e.g., Fama-French 3-Factor: $R = \beta_1 \times Size + \beta_2 \times Value$). It decides what we are looking at.
- Estimator (The Math Solver): The algorithm (OLS, Ridge Regression) that takes the Factor Model's equation and finds the optimal parameters. It decides how we solve the math.
- Portfolio Strategy (The Allocator): Takes the Estimator's predictions and outputs Target Portfolio Weights. (This is where you will eventually inject your TCS approximation algorithms to handle NP-hard constraints).
- Backtest (The Reality Simulator): Steps through time day-by-day. It takes the Target Weights, applies transaction costs and slippage, and tracks cash. It is strictly forbidden from looking ahead in time.
- Result (The Ledger): A passive data class that holds the final equity curve, Sharpe ratios, and diagnostic logs for the researcher to review.
