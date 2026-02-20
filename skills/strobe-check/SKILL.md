---
name: strobe-check
description: >
  Review a manuscript against STROBE reporting guidelines for
  observational studies. Use when checking a draft manuscript
  for completeness, preparing for journal submission, or
  responding to reviewer comments about reporting quality.
  Adapted for infectious disease and forecast evaluation studies.
disable-model-invocation: true
user-invocable: true
argument-hint: "[path-to-manuscript]"
---

# STROBE Reporting Checklist Review

## Instructions

1. Read the manuscript file provided as `$ARGUMENTS`
2. Load `references/strobe-checklist.md` for the full adapted checklist
3. Work through each of the 22 STROBE items systematically
4. For each item, identify the relevant section of the manuscript and assess coverage

## Assessment process

For each STROBE item:

1. **Locate**: Find where in the manuscript this item is addressed
2. **Assess**: Rate as Present, Partial, or Missing
3. **Note**: For Partial or Missing items, provide specific guidance on what to add or improve
4. **Adapt**: Some items need reinterpretation for non-standard study types (see below)

## Adaptations for common study types

### Forecast evaluation studies

- **Participants** (Item 6): "Participants" are forecasting models/teams, not human subjects. Describe model selection criteria, inclusion/exclusion, and the forecasting platform.
- **Variables** (Item 7): Exposure = model characteristics (method, geographic scope). Outcome = forecast accuracy (scoring rule). Confounders = prediction difficulty factors (horizon, location, trend).
- **Data sources** (Item 8): The forecasting hub or platform, observation data sources, and any secondary data (variant classifications, population data).
- **Bias** (Item 9): Selection bias from model participation patterns. Information bias from varying submission completeness. Confounding by prediction difficulty.

### Secondary data analysis

- **Setting** (Item 5): Describe the original data collection, not just your analysis
- **Participants** (Item 6): Describe the original study population and your inclusion criteria for the secondary analysis
- **Data sources** (Item 8): Cite the original data source and any linking or transformation steps

## Output format

Present results as a markdown table:

```markdown
| Item | Topic | Status | Location | Notes |
|------|-------|--------|----------|-------|
| 1a | Title: study design | Present | Title | ... |
| 1b | Abstract: informative | Partial | Abstract | Missing: sample size |
```

After the table, provide:
1. **Summary**: Count of Present / Partial / Missing items
2. **Priority fixes**: The 3-5 most important gaps to address, ordered by impact on manuscript quality
3. **Not applicable**: Any items genuinely not applicable, with justification

## Common gaps to watch for

These items are most frequently missing or weak in infectious disease manuscripts:

- **Item 6** (Participants): Selection criteria for models/data often implicit
- **Item 7** (Variables): Exposure classification and confounder identification under-specified
- **Item 9** (Bias): Often omitted entirely or treated superficially
- **Item 12e** (Sensitivity analyses): Often missing or not pre-specified
- **Item 16a** (Main results): Unadjusted vs adjusted comparison absent
- **Item 19** (Limitations): Direction and magnitude of potential bias rarely discussed
