---
name: epi-analysis
description: >
  Epidemiological analysis conventions for R.
  Apply when writing or reviewing statistical analysis code
  involving: regression models for count or rate data, forecast
  evaluation, scoring rules, GAMs/GAMMs, or time-series of
  infectious disease data.
  Covers model specification, diagnostics, and interpretation.
---

# Epidemiological Analysis in R

## Data processing

- Count data: check for zeros before log transforms; document any constant added (e.g. `wis + 1e-7`)
- Dates: use `lubridate`; align weekly aggregation with ISO epiweeks
- Factors: set reference levels explicitly with epidemiological justification
- Trend classification: define thresholds for stable/increasing/decreasing explicitly
- Population denominators: rates per 100,000; document data source
- Missing data: document patterns and handling; distinguish MCAR/MAR/MNAR

## Model selection

Choose model family based on the outcome distribution:

| Outcome | First choice | Check | Alternative |
|---------|-------------|-------|-------------|
| Counts | Poisson GLM | Overdispersion (`dispersiontest()`) | Negative binomial, quasi-Poisson |
| Rates | Poisson with offset | Overdispersion | Negative binomial with offset |
| Continuous positive | Gamma GLM or log-transformed Gaussian | Residual normality | Tweedie |
| Scores (WIS, CRPS) | Log-transformed Gaussian | Residual patterns | Gamma GLM |

### GAMs and GAMMs (`mgcv`)

- Use smooth terms (`s()`) for non-linear relationships; parametric terms for categorical variables
- `bs = "re"` for random intercepts; `bs = "fs"` for factor-smooth interactions
- `bs = "tp"` (default thin plate) for spatial/temporal smooths
- Use `bam()` with `discrete = TRUE` for large datasets; `fREML` for fast estimation
- Always check basis dimension: `mgcv::k.check()`
- Link functions: log link for multiplicative effects on positive outcomes; identity when additive

### Adjusted vs unadjusted

- Always fit both unadjusted (single predictor) and adjusted (full) models
- Compare estimates to demonstrate direction and magnitude of confounding
- Do not interpret coefficients of adjustment variables as causal effects (Table 2 fallacy)

## Model diagnostics

Run and report these diagnostics:

1. `gratia::appraise()` for GAM diagnostic plots
2. `mgcv::k.check()` for basis dimension adequacy
3. Residual vs fitted, QQ plot, scale-location plot
4. For random effects: `gammit::extract_ranef()` to inspect estimated effects and CIs
5. Check for influential observations if sample size permits

Report what diagnostics show, including imperfections.
Do not hide diagnostic issues.

## Forecast evaluation

- Use proper scoring rules: WIS (weighted interval score), CRPS, log score
- State which scoring rule and why
- `scoringutils` pipeline: `as_forecast_quantile()` then `score()`
- Log-transformed evaluation: transform BOTH forecasts and observations before scoring
- Pairwise comparisons vs pooled scoring: justify choice
- Report calibration (PIT histograms) and sharpness separately from overall score

## Interpreting and reporting results

- Random effects: report as partial effects with 95% CI
- Compare adjusted vs unadjusted to show what confounding adjustment achieves
- Acknowledge residual variation explicitly
- Never claim "no effect" from non-significance; use "no clear evidence of systematic difference"
- Report effect sizes with confidence intervals, not just p-values
- For multiplicative models (log link): back-transform to ratio scale for interpretation

## Code conventions

- Use tidyverse with native pipe (`|>`)
- Document functions with a purpose comment at top
- Separate data processing, model fitting, and output extraction into distinct scripts
- Analysis scripts should be source-able from Quarto/Rmd
- Use `here()` for all file paths
- Write CSV for intermediate data, RDS for R objects
