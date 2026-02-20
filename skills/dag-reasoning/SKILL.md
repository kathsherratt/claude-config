---
name: dag-reasoning
description: >
  Reason about causal structure using directed acyclic graphs
  for epidemiological studies. Use when identifying confounders,
  mediators, or colliders; when deciding which variables to
  adjust for; or when a reviewer questions the adjustment
  strategy.
---

# DAG-Based Causal Reasoning

## Variable classification rules

Before adjusting for any variable, classify its role:

| Role | Definition | Adjust? | Consequence of error |
|------|-----------|---------|---------------------|
| **Confounder** | Common cause of exposure and outcome | Yes | Omitting causes bias |
| **Mediator** | On causal pathway from exposure to outcome | No (unless decomposing) | Adjusting blocks the effect of interest |
| **Collider** | Common effect of exposure and outcome | No | Adjusting opens spurious path |
| **Instrument** | Affects exposure only, not outcome directly | No (use for IV methods) | Adjusting reduces precision |
| **Precision variable** | Predicts outcome, unrelated to exposure | Optional | Improves precision if included |

## The backdoor criterion

To estimate the causal effect of X on Y:
1. List all paths from X to Y
2. Identify which paths are causal (follow arrow direction) and which are non-causal (backdoor paths)
3. Find a set of variables that blocks all backdoor paths without opening new non-causal paths
4. This set is a valid adjustment set

A path is blocked if it passes through:
- A variable you condition on (if that variable is not a collider on the path)
- A collider you do NOT condition on

## Drawing DAGs

Use ASCII art for simple DAGs:

```
  Confounder
   /      \
  v        v
Exposure --> Outcome
```

```
Exposure --> Mediator --> Outcome
```

```
Exposure --> Collider <-- Outcome
(DO NOT condition on Collider)
```

Guidelines:
- Include all variables in the analysis plus important omitted ones
- Every missing arrow is an assumption (no direct effect)
- Time flows left to right where possible
- Mark adjusted variables with brackets: [Variable]

## Common pitfalls

### Table 2 fallacy
Interpreting coefficients of adjustment variables as if they are causal effects of those variables.
Each variable in a model has a different confounding structure; the adjustment set valid for the primary exposure is not valid for other variables.

### Overadjustment
Conditioning on a descendant of the outcome, which can induce bias.
Example: adjusting for a variable caused by the outcome.

### M-bias
Conditioning on a variable that is a common effect of two unobserved causes (one of the exposure, one of the outcome).
This opens a path that was previously blocked.

### Adjusting for a proxy
Using a proxy for a confounder may not fully block the backdoor path.
Residual confounding remains proportional to how poor the proxy is.

### Time-varying confounding
When a confounder is itself affected by prior exposure values.
Standard regression cannot handle this; requires marginal structural models or g-estimation.

### Hierarchical/nested structures
When units are nested (e.g., models within method classes, patients within hospitals):
- Effects can operate at different levels
- Adjusting for group-level variables when the exposure varies at the group level can absorb signal
- Consider whether random effects are appropriate vs fixed effects
- A variable that is constant within clusters cannot confound within-cluster comparisons

## Applying DAGs to forecast evaluation

Example for a study of method effects on forecast accuracy:

```
                Trend
                 |
                 v
Method -----> Accuracy <----- Horizon
  ^              ^               |
  |              |               |
  +-- Location --+               |
  |              |               |
  +---- Time ----+---------------+
```

- **Method -> Accuracy**: The effect of interest
- **Location, Time, Trend, Horizon -> Accuracy**: Prediction difficulty confounders (adjust)
- **Location, Time -> Method**: If some methods are used in specific locations/periods (adjust)
- **Model**: Nested within Method; random effect absorbs model-specific skill

Key question: Is "number of forecasts submitted" a confounder, mediator, or collider?
- If more experienced teams (exposure -> submissions) also forecast better (submissions -> outcome): mediator. Do not adjust.
- If better accuracy leads to continued participation: collider on a specific path. Adjusting may bias.
