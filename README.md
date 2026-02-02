# Survival-Based-Risk-Prediction-using-Partial-Moments
Project Overview

Traditional financial risk measures such as volatility and variance treat gains and losses in the same way. In reality, investors care much more about losses, especially large drawdowns.

This project models Bitcoin crash risk as a time-to-event problem. Instead of asking how volatile Bitcoin is, the project asks:

How long does Bitcoin survive before experiencing a major crash?

A crash is defined as a 20 percent peak-to-trough drawdown.
The project uses survival analysis combined with downside risk measures (Partial Moments) to predict crash risk more realistically.

Crash Definition

Asset: Bitcoin (BTC-USD)

Crash Event: 20 percent peak-to-trough drawdown

Time Unit: Days

Survival Time: Number of days until the first 20 percent drawdown

Censoring: Periods with no crash are treated as censored observations

Why Survival Analysis?

Most risk models output a single number, such as volatility.
Survival analysis answers a more useful question:

When is a crash likely to happen?

This approach:

Handles sudden crashes naturally

Uses time information efficiently

Works well with rare but extreme events

Partial Moments Explained
Lower Partial Moment (LPM)

Measures downside risk only

Focuses on losses below a threshold

Strongly linked to crash behavior

Upper Partial Moment (UPM)

Measures upside movements

Helps separate good volatility from bad volatility

Unlike variance, partial moments do not treat gains and losses equally.

Methodology

Download daily Bitcoin price data

Compute returns and drawdowns

Identify 20 percent crash events

Create survival labels (time and event)

Compute rolling LPM and UPM features

Fit a Cox Proportional Hazards model

Compare results with a variance-based model

Evaluate using concordance index and survival curves

Perform stress testing by increasing downside risk

Models Used
Primary Model

Cox Proportional Hazards Model

Covariates:

Lower Partial Moment (LPM)

Upper Partial Moment (UPM)

Baseline Model

Cox Proportional Hazards Model

Covariate:

Rolling variance of returns

Key Findings

Downside risk rises before major Bitcoin crashes

Lower Partial Moments are stronger predictors of crashes than variance

Variance-based models fail to distinguish good volatility from bad volatility

Survival models provide meaningful crash timing information

Evaluation Metrics

Concordance Index (risk ranking accuracy)

Survival probability curves for high-risk and low-risk periods

The partial moment model consistently outperforms the variance-based model.

Practical Applications

Crypto risk management

Hedge fund crash monitoring

Early warning systems for drawdowns

Portfolio stress testing

Academic research in financial risk modeling

Limitations

Model assumes proportional hazards

Single asset analysis

Fixed drawdown threshold

Does not include macro or on-chain variables

Possible Extensions

Dynamic or regime-switching survival models

Deep learning survival models (DeepSurv)

Multi-asset or portfolio-level analysis

Volatility-adjusted crash thresholds

Inclusion of macroeconomic or sentiment indicators

Technologies Used

Python

Google Colab

Pandas and NumPy

Matplotlib

Lifelines (Survival Analysis)

Yahoo Finance data
