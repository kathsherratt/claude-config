---
name: figure-table
description: >
  Create publication-quality figures and tables for academic
  manuscripts in R using ggplot2 and kableExtra. Apply when
  creating or refining visualisations of epidemiological data,
  model results, or summary statistics. Covers journal
  formatting, captions, and accessibility.
---

# Publication-Quality Figures and Tables

## Figure conventions

### Theme and layout

- Base theme: `theme_classic()` or `theme_bw()` with minimal gridlines
- Font size: 10-12pt for axis labels, 8-10pt for annotations
- Multi-panel figures: use `patchwork` with `plot_annotation(tag_levels = "A")`
- Panel labels: uppercase letters (A, B, C) in bold
- Aspect ratio: match the journal column width (single: ~85mm, double: ~170mm)

### Colour

- Use `scale_*_brewer()` with qualitative palettes for categorical data
- Ensure colour-blind safe: avoid red-green combinations; prefer `viridis` or `RColorBrewer` "Set2", "Dark2"
- Use distinct palettes between panels in multi-panel figures
- If >7 categories, consider shape or linetype instead of colour alone
- Grey for reference/baseline groups

### Axes and labels

- Label axes with full names and units (e.g., "Forecast horizon (weeks)")
- Avoid abbreviations unless defined in the caption
- Use `scale_x_date(date_labels = "%b %Y")` for time axes
- Start count/score axes at zero unless strong reason not to
- Log-scale axes: label with original values, not log values

### Specific plot types

**Coefficient/forest plots:**
- Point estimate with CI whiskers
- Reference line at null (0 for additive, 1 for multiplicative)
- Order by effect size or grouping variable
- Show both unadjusted (open symbol) and adjusted (filled symbol) if comparing

**Time series:**
- Observed data as points or thin line
- Predictions/smooths as thicker line with ribbon for CI
- Vertical lines for key events (variant emergence, policy changes)

**Score distributions:**
- Box plots or violin plots grouped by model characteristic
- Log-scale y-axis for skewed scores
- Show individual model points overlaid if few models

## Table conventions

### Formatting with kableExtra

```r
library(kableExtra)

df |>
  kbl(
    caption = "Table 1. Descriptive characteristics of included models.",
    digits = 2,
    col.names = c("Characteristic", "N", "Median (IQR)")
  ) |>
  kable_styling(full_width = FALSE) |>
  pack_rows("Model type", 1, 3) |>
  pack_rows("Geographic scope", 4, 5) |>
  footnote(general = "IQR = interquartile range.")
```

### Content conventions

- Table 1: Descriptive characteristics by exposure group
- Include: N (%), median (IQR) or mean (SD) as appropriate
- Group rows logically with `pack_rows()`
- All abbreviations explained in footnotes
- Numbers in brackets: explicitly label what they are (SD, 95% CI, IQR)

## Captions

Captions must be standalone. A reader should understand the figure or table without reading the main text.

Structure:
1. **What** is shown (the data or result)
2. **How** it was measured or computed
3. **How** to interpret (what do colours, panels, axes represent)
4. **Abbreviations** defined

Example:
> Figure 2. Adjusted partial effects of model method on forecast accuracy.
> Panel A shows effects on case forecasts; Panel B shows effects on death forecasts.
> Points indicate posterior mean partial effects from the GAMM; whiskers show 95% confidence intervals.
> The dashed line indicates no difference from the overall mean.
> WIS = weighted interval score; GAMM = generalised additive mixed model.

## Export for journal submission

```r
ggsave(
  here("output", "plots", "figure-1.tif"),
  plot = fig1,
  width = 170, height = 120, units = "mm",
  dpi = 300
)
```

- Format: TIFF or EPS for submission; PNG for drafts
- Minimum 300 DPI
- Dimensions in mm matching journal specifications
- Separate files for each figure
- Supplementary figures follow the same quality standards
