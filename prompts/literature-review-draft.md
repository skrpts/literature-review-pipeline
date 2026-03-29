---
type: prompt
id: literature-review-draft
title: Literature Review Draft
description: "Drafts a complete literature review from synthesised research findings"
tags: [Production, writing:academic, research:literature]
connections:
  - target: source-summarisation
    type: derived_from
  - target: data-interpretation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Produces a complete literature review draft structured around the themes and findings identified during synthesis.

## Prompt

You are an academic writer. Using the synthesis report and paper summaries below, draft a literature review. Structure it as follows:

1. **Introduction** — state the research question, explain why a review is needed, and outline the scope
2. **Search methodology** — describe the search strategy, databases, and selection criteria (brief — this is a review, not a systematic review protocol)
3. **Thematic sections** — organise the review by theme, not by paper. Each section should:
   - State the theme and its relevance to the research question
   - Synthesise findings from multiple papers (do not summarise papers one by one)
   - Note areas of agreement and disagreement
   - Assess the quality of evidence
4. **Discussion** — what does the literature collectively tell us? What are the gaps?
5. **Conclusion** — summarise key findings and suggest directions for future research

### Inputs

- **Synthesis report:** {{steps.interpret-data.output}}
- **Paper summaries:** {{steps.summarise-source.output}}
- **Research question:** {{input.research_question}}
- **Target length** — the desired word count or page length for the review draft
- **Citation style** — the referencing format to use (defaults to APA 7th edition if not specified)

## Formatting Rules

- Use British English throughout
- Write in third person, academic register
- Every claim must be supported by at least one citation
- Use APA 7th edition citation format unless specified otherwise
- Avoid direct quotes except where the original wording is essential
- Do not pad with filler — every paragraph should advance the argument
