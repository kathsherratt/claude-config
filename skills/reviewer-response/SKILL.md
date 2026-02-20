---
name: reviewer-response
description: >
  Process and respond to peer review comments on an academic
  manuscript. Use when receiving reviewer feedback, planning
  revisions, drafting response letters, or tracking revision
  progress. Structures the workflow from triage to final
  response letter.
disable-model-invocation: true
user-invocable: true
argument-hint: "[path-to-reviews]"
---

# Reviewer Response Workflow

## Step 1: Triage

Read the reviews file provided as `$ARGUMENTS` and parse each comment into a structured record.

For each comment, identify:
- **Reviewer**: Which reviewer (Reviewer 1, 2, etc.)
- **Comment text**: The full comment
- **Category**: Major methodological, Major analytical, Minor, Editorial
- **Manuscript section**: Which part of the paper it affects
- **Action**: Accept, Partly accept, or Reject (with justification)

Look for clusters of related comments across reviewers.
These indicate areas where the manuscript needs the most work.

## Step 2: Create tracking table

Generate a markdown tracking table:

```markdown
| Status | # | Reviewer | Comment (summary) | Response plan | Files affected |
|--------|---|----------|-------------------|---------------|----------------|
| [ ] | 1 | R1 | ... | ... | ... |
```

Group by:
- Analysis changes (code modifications needed)
- Writing changes (text revisions only)
- New supplementary material
- No action needed (clarification in response only)

Suggest creating GitHub issues for substantive comments that require code changes.

## Step 3: Draft responses

### Tone and approach
- Respectful, specific, evidence-based
- Address every comment, even trivial ones
- Never dismiss a comment; explain reasoning when disagreeing

### Response templates by action type

**Accept (change made):**
> We thank the reviewer for this suggestion.
> We have [specific action taken].
> The revised text now reads: "[quoted text]" (p. X, line Y).

**Partly accept:**
> We appreciate this observation.
> We have [what was done].
> However, we did not [what was not done] because [specific reasoning with evidence].

**Reject (with reasoning):**
> We thank the reviewer for raising this point.
> We respectfully disagree because [specific evidence or reasoning].
> [If applicable: We have added text to the manuscript clarifying this point.]

### For methodological challenges

When reviewers question the statistical approach:
- Provide the epidemiological or statistical reasoning, not just a citation
- If the concern has merit, run a sensitivity analysis and report it
- Reference established guidelines (STROBE, GATHER) where they support your approach
- Acknowledge limitations honestly rather than defending unconditionally

## Step 4: Coordinate changes

For each accepted comment:
1. Identify which files need editing (analysis scripts, manuscript, supplement)
2. Check for conflicts between reviewer suggestions
3. Make analysis changes first, then update manuscript text
4. Ensure inline statistics, figures, and tables reflect any reanalysis
5. Update the tracking table as each item is completed

## Step 5: Final response letter

Format the response letter:

```markdown
# Response to Reviewers

We thank the reviewers for their constructive feedback.
Below we address each comment point by point.
Changes to the manuscript are indicated in [bold/tracked changes].

## Reviewer 1

### Comment 1.1
> [Quoted reviewer comment]

[Response text]

### Comment 1.2
...

## Reviewer 2
...
```

Include page and line references to all manuscript changes.
