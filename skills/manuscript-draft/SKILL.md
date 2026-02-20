---
name: manuscript-draft
description: >
  Draft or revise sections of an academic manuscript in
  epidemiology. Use when writing methods, results, or
  discussion sections, or when updating manuscript text to
  reflect analysis changes. Applies epidemiological writing
  conventions and proper statistical language.
disable-model-invocation: true
user-invocable: true
---

# Academic Manuscript Drafting

## Writing conventions

- One sentence per line in markdown
- Simple, direct prose without adjectives
- Active voice preferred ("We fitted..." not "A model was fitted...")
- Present tense for established facts; past tense for what was done in this study
- Define abbreviations on first use

## Statistical language precision

### Associations and effects

| Instead of | Write |
|-----------|-------|
| "X causes Y" | "X was associated with Y" (observational data) |
| "No effect" | "No clear evidence of a systematic difference" |
| "X significantly affected Y" | "X was associated with a [magnitude] [direction] in Y (95% CI: ...)" |
| "Proved" | "Found evidence consistent with" |
| "Failed to reach significance" | "The estimate was imprecise (95% CI: ... to ...)" |

### Reporting estimates

- Always report effect sizes with uncertainty or confidence intervals
- For multiplicative models: report on ratio scale (e.g., "1.3-fold higher, 95% CI: 1.1 to 1.6")
- For additive models: report absolute differences with units
- Present both unadjusted and adjusted estimates to show confounding direction
- State the adjustment set explicitly

### Uncertainty

- Distinguish statistical uncertainty (CI width) from systematic bias (confounding, measurement error)
- Overlapping CIs do not mean "no difference"; formally compare if needed
- Interpret CIs as compatibility intervals: values within the CI are compatible with the data

## Section-specific guidance

### Methods

Structure:
1. Study design and setting (one paragraph)
2. Data sources (one paragraph per source)
3. Variables: outcome definition, exposure classification, confounders (one paragraph each)
4. Statistical analysis: model specification, software (one to two paragraphs)
5. Sensitivity analyses (one paragraph)

Include enough detail for independent replication.
State software versions.
Reference the analysis code repository.

### Results

Structure:
1. Participation/sample (flow from eligible to included)
2. Descriptive characteristics (Table 1)
3. Main results: unadjusted, then adjusted (Table 2 or Figure)
4. Subgroup and sensitivity analyses

Lead with the finding, then the evidence:
- "Statistical models were associated with lower accuracy than mechanistic models (adjusted WIS ratio: 1.3, 95% CI: 1.1 to 1.6)."
- NOT: "The adjusted WIS ratio was 1.3 (95% CI: 1.1 to 1.6), indicating that statistical models had lower accuracy."

Reference figures and tables actively:
- "Table 1 shows..." not "as shown in Table 1"

### Discussion

Structure:
1. Key findings (one paragraph, no new numbers)
2. Comparison with existing literature (two to three paragraphs)
3. Strengths and limitations (one to two paragraphs)
4. Implications and future directions (one paragraph)

For limitations:
- Name the bias type (selection, information, confounding)
- State the expected direction (toward or away from null)
- Estimate likely magnitude if possible
- Do not just list limitations; explain what they mean for interpretation

### Epidemiological terminology

| Term | Use precisely |
|------|--------------|
| Confounding | Requires a specific causal structure; use "adjustment" when structure uncertain |
| Bias | Specify type and direction; not a synonym for "error" |
| Random effects | Describe what they represent substantively, not just statistically |
| Accuracy | General performance; distinguish from calibration and sharpness |
| Calibration | Reliability of probabilistic predictions specifically |
| Significance | Avoid; report estimates and CIs instead |

## Coordination with analysis

When updating manuscript text:
1. Check that any quoted numbers match current analysis output
2. If analysis has changed, identify all manuscript sections needing updates
3. Ensure figure/table references match current numbering
4. Update the research narrative document if the story has changed
