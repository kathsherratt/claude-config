# STROBE Checklist for Observational Studies

Adapted for infectious disease epidemiology and forecast evaluation.
Based on STROBE Statement (von Elm et al., 2007).

## Title and Abstract

| Item | Requirement | Adaptation notes |
|------|------------|-----------------|
| 1a | Indicate the study's design in title or abstract | For forecast evaluation: state it is an observational analysis of forecast performance |
| 1b | Provide an informative, balanced abstract including: background, methods, results, conclusions | Include: number of models/forecasts, study period, primary outcome measure, key finding with effect size |

## Introduction

| Item | Requirement | Adaptation notes |
|------|------------|-----------------|
| 2 | Explain scientific background and rationale | State why evaluating forecast accuracy matters for the specific disease/context |
| 3 | State specific objectives, including any pre-specified hypotheses | Distinguish prediction vs association vs causal inference aims |

## Methods

| Item | Requirement | Adaptation notes |
|------|------------|-----------------|
| 4 | Present key elements of study design early | State: retrospective analysis of prospectively collected forecasts (or similar) |
| 5 | Describe setting, locations, dates (including recruitment, exposure, follow-up, data collection) | Describe: forecasting platform/hub, participating countries, study period, forecast submission windows |
| 6a | Give eligibility criteria, sources and methods of selection | For forecast eval: model inclusion criteria (minimum submissions, target types, quantile levels). For secondary analysis: original study population and your subset criteria |
| 6b | For matched studies, matching criteria and number of exposed/unexposed | Rarely applicable; note if models are matched by submission date or target |
| 7 | Define all outcomes, exposures, predictors, confounders, effect modifiers. Give diagnostic criteria where applicable | Outcome: scoring rule (WIS, CRPS) with definition. Exposure: model characteristic (method type, geographic scope). Confounders: prediction difficulty factors. Give classification criteria for each |
| 8 | For each variable, give data sources and details of assessment. For >1 group, describe comparability | Cite data sources (forecast hub, surveillance systems). Describe how model classifications were assigned (self-report, expert assessment, algorithm) |
| 9 | Describe any efforts to address potential sources of bias | Address: selection bias (model participation), information bias (classification uncertainty), confounding (by prediction difficulty). State direction of expected bias |
| 10 | Explain how the study size was arrived at | Report total forecasts, models, locations, time points. If a power calculation was done, report it |
| 11 | Explain how quantitative variables were handled. If applicable, describe which groupings were chosen and why | State how continuous variables were categorised or smoothed. Justify any grouping thresholds |
| 12a | Describe all statistical methods for each objective | Specify model family, link function, error distribution, estimation method. Name software packages with versions |
| 12b | Describe methods for examining subgroups and interactions | State any planned stratifications (by variant phase, country, horizon) |
| 12c | Explain how missing data were addressed | Report missing forecast submissions and how handled (complete case, imputation, or acknowledged limitation) |
| 12d | If applicable, explain how loss to follow-up was addressed | For forecast eval: how model dropout during study period was handled |
| 12e | Describe any sensitivity analyses | List pre-specified sensitivity analyses and their rationale |

## Results

| Item | Requirement | Adaptation notes |
|------|------------|-----------------|
| 13a | Report numbers at each stage (consider flow diagram) | Flow diagram: total models considered, excluded (with reasons), included. Total forecasts by model |
| 13b | Give reasons for non-participation at each stage | Why models were excluded (insufficient submissions, wrong format, late entry) |
| 13c | Consider use of a flow diagram | Recommended especially when exclusion criteria are multi-step |
| 14a | Give characteristics of participants and information on exposures and confounders | Table 1: model characteristics (method, geographic scope, team), number of submissions, countries covered |
| 14b | Indicate number of participants with missing data for each variable | Report completeness of model classification and forecast submissions |
| 15 | Report numbers of outcome events or summary measures | Report distribution of scores (median, IQR) overall and by group |
| 16a | Give unadjusted estimates and, if applicable, confounder-adjusted estimates with precision (e.g. 95% CI). State which confounders were adjusted for and why | Present BOTH unadjusted and adjusted estimates side by side. Name each adjustment variable and its role (confounder vs precision variable) |
| 16b | Report category boundaries when continuous variables were categorised | State thresholds and justify. Report number of observations per category |
| 16c | If relevant, consider translating relative measures into absolute risk | For scores: report both relative differences (ratios) and absolute differences in score units |

## Discussion

| Item | Requirement | Adaptation notes |
|------|------------|-----------------|
| 17 | Summarise key results with reference to objectives | State main finding with effect size and CI |
| 18 | Discuss limitations, sources and direction of bias, imprecision. Discuss direction and magnitude of any potential bias | For each bias type (selection, information, confounding): state the direction of expected bias and likely magnitude. Do not just list limitations |
| 19 | Give a cautious overall interpretation considering objectives, limitations, multiplicity of analyses, similar studies | Distinguish what the study shows from what it cannot show. Do not overclaim causality from observational data |
| 20 | Discuss generalisability (external validity) | To what diseases, forecasting contexts, or time periods do results generalise? |

## Other Information

| Item | Requirement | Adaptation notes |
|------|------------|-----------------|
| 21 | State the source of funding and the role of funders | Standard |
| 22 | State where the study protocol, registration, or full data can be accessed | Link to code repository, data repository, pre-registration if applicable |
