# Methodology

This project tests a macro-rates intuition under increasingly strict specifications.

## 1. Macro anchor

The anchor is constructed as

```text
theta_t = r*_t + trend_inflation_t
```

where trend inflation is a slow moving estimate based on CPI inflation and `r*_t` is a slow-moving neutral real-rate proxy. The key restriction is that the term premium is not inserted into the short-rate anchor. For long maturities, the term premium is derived as a model output.

## 2. Short-rate model

The core specification places the macro anchor as the moving central tendency of a Hull--White short-rate process estimated under the physical measure:

```text
dr_t = kappa (theta_t - r_t) dt + sigma dW_t
```

Estimation is based on the time-series relation between changes in the short rate and the gap to the anchor. The model is not calibrated to the current yield curve; therefore the comparison between observed yields and the model-implied pure-expectations curve is informative.

## 3. Model-implied term premium

For each tenor, the pure-expectations yield is derived from the affine short-rate model. The model term premium is

```text
TP_model(tau, t) = observed_yield(tau, t) - pure_expectations_yield(tau, t)
```

This is the central predictor in the paper.

## 4. Predictive tests

The core tests use expanding-window forecasting regressions and compare forecasts against an expanding historical mean benchmark. The reported diagnostics include:

- in-sample predictive slopes with Newey--West standard errors;
- realized out-of-sample R²;
- Clark--West tests for nested forecast comparison;
- common-window horse races against slope, Fama--Bliss-style predictors, raw anchor gaps, and anchor-free affine alternatives.

## 5. Specification audit

The project treats specification sensitivity as an object of study. The audit decomposes differences between strict US tests and panel-style tests into:

- tenor concentration: basket vs exact 10Y;
- target construction: exact Fama--Bliss-style excess returns vs duration-approximated returns;
- funding-rate series: T-bill vs interbank/money-market proxy;
- sample length and window effects.

## 6. Extensions

The extensions explore whether the same term-premium signal can be used for:

- tactical duration overlays;
- yield-curve relative value;
- sparse tenor selection under conditional rates risk.

These extensions are not the headline paper claim in the current version.
