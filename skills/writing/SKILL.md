---
name: writing
description: >
  Use when writing any prose.
disable-model-invocation: true
user-invocable: true
---

# All prose writing

## Writing style

Primary importance:
- Use simple, direct prose
- DO NOT use adverbs
- Use very few adjectives

Secondary importance:
- Prefer active voice ("We fitted..." not "A model was fitted...")
- Present tense for established facts; past tense for what was done
- Define abbreviations on first use
- Use consistent terminology (see below)
- Explain necessary technical terms

As general context, note:

- In general interaction, ask questions rather than making assumptions; suggest a longer interview format where there is substantial ambiguity in the task.
- Perspective and tone should be warm, curious, direct.

## Language precision

### Terminology

| Term | Use precisely |
|------|--------------|
| Confounding | Requires a specific causal structure; use "adjustment" when structure uncertain |
| Bias | Specify type and direction; not a synonym for "error" |
| Random effects | Describe what they represent substantively, not just statistically |
| Accuracy | General performance; distinguish from calibration and sharpness |
| Calibration | Reliability of probabilistic predictions specifically |
| Significance | Avoid; report estimates and CIs instead |

### Associations and effects

| Instead of | Write |
|-----------|-------|
| "X causes Y" | "X was associated with Y" (observational data) |
| "No effect" | "No clear evidence of a systematic difference" |
| "X significantly affected Y" | "X was associated with a [magnitude] [direction] in Y (95% CI: ...)" |
| "Proved" | "Found evidence consistent with" |
| "Failed to reach significance" | "The estimate was imprecise (95% CI: ... to ...)" |

## Format-specific guidance

### Academic manuscripts

Invoke`SKILL.md` in `skills/manuscript-draft/`.

## Formatting
- In Markdown, use one sentence per line
- Max 80 chars per line (except Markdown, Quarto, and .qmd where one sentence per line takes priority)
- No trailing whitespace
- No spurious blank lines

