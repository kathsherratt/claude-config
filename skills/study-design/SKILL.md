---
name: study-design
description: >
  Design an epidemiological study using observational data.
  Use when planning a new analysis, defining research questions,
  identifying exposures, outcomes, and confounders, or
  structuring a study protocol. Covers cohort, cross-sectional,
  and ecological designs common in infectious disease
  epidemiology.
disable-model-invocation: true
user-invocable: true
---

# Epidemiological Study Design

Work through each section with the user, asking clarifying questions at each step.

## 1. Research question

Frame the question using the PECO structure:

- **P**opulation: Who or what is being studied?
- **E**xposure: What factor, intervention, or characteristic is of interest?
- **C**omparison: What is the reference group?
- **O**utcome: What is being measured?

Clarify the study aim:
- **Descriptive**: Characterise patterns (no hypothesis)
- **Exploratory**: Identify associations (hypothesis-generating)
- **Confirmatory**: Test a pre-specified hypothesis

Distinguish:
- **Prediction**: Best forecast of outcome (variable selection by predictive accuracy)
- **Association**: Relationship after adjustment (variable selection by confounding structure)
- **Causal inference**: Effect of intervention (requires DAG, consider `/dag-reasoning`)

Draft a one-sentence research question.

## 2. Study design classification

Classify using standard epidemiological designs:

| Design | Unit | Temporal | When to use |
|--------|------|----------|-------------|
| Cohort (prospective) | Individual | Follow-up | Incidence, risk factors |
| Cohort (retrospective) | Individual | Historical | Existing records |
| Cross-sectional | Individual | Snapshot | Prevalence, surveys |
| Case-control | Individual | Lookback | Rare outcomes |
| Ecological | Group/area | Variable | Population-level patterns |

For forecast evaluation: frame as "retrospective observational study of forecast performance" where the unit of observation is individual forecasts or forecast-target pairs.

See `references/study-designs.md` for detailed guidance on each design.

State inherent limitations of the chosen design.

## 3. Variable roles

List all variables and classify each:

- **Outcome** (Y): What is measured. Define precisely, including scale and scoring rule if applicable
- **Exposure** (X): The factor of interest. Define categories and classification criteria
- **Confounders** (C): Common causes of X and Y. Must satisfy: (1) associated with exposure, (2) associated with outcome, (3) NOT on the causal pathway
- **Effect modifiers** (M): Variables that change the X-Y relationship
- **Mediators**: On the causal pathway; do NOT adjust unless decomposing direct/indirect effects
- **Precision variables**: Predictive of outcome but not of exposure; improve precision without affecting bias

For each confounder, justify inclusion with a brief causal argument.
Consider using `/dag-reasoning` to formalise the causal structure.

## 4. Data requirements

Define:
- **Unit of analysis**: What each row in the dataset represents
- **Inclusion criteria**: Who/what is in the study (with explicit justification)
- **Exclusion criteria**: Who/what is excluded (with explicit justification)
- **Data sources**: Where each variable comes from
- **Sample size**: How many units are available; any power considerations

Consider:
- Selection bias from inclusion/exclusion criteria
- Measurement error in exposure classification
- Missing data: expected patterns and handling strategy
- Temporal alignment of exposure, confounders, and outcome

## 5. Analysis plan skeleton

Pre-specify:
- **Primary analysis**: Model family, link function, adjustment set
- **Unadjusted analysis**: Same model without confounders (for comparison)
- **Subgroup analyses**: Any planned stratifications
- **Sensitivity analyses**: Alternative specifications to probe assumptions
- **Multiple comparisons**: How handled if applicable

## 6. Output

Generate a structured study protocol in markdown covering sections 1-5.
Flag decisions that will need explicit justification in the manuscript Methods section.
