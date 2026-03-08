---
type: workflow
id: literature-review-pipeline
title: Literature Review Pipeline
description: "Search, summarise, synthesise, and write a literature review"
tags: [Production]
connections:
  - target: literature-search
    type: uses
  - target: source-summarisation
    type: uses
  - target: data-interpretation
    type: uses
  - target: search-literature
    type: uses
  - target: summarise-source
    type: uses
  - target: interpret-data
    type: uses
  - target: literature-review-draft
    type: uses
  - target: anthropic-claude
    type: runs_on
  - target: openai-gpt4
    type: runs_on
  - target: semantic-scholar
    type: runs_on
metadata:
  estimated_duration: "30-60 minutes"
  trigger: manual
---

## Overview

This workflow conducts a complete literature review from initial search through to a written review draft. It follows academic best practices for systematic searching, screening, summarisation, and synthesis.

## Pipeline Stages

### Stage 1: Literature Search

**Input:** Research question, search terms, target databases, inclusion/exclusion criteria

Invoke the **literature-search** skill via the **search-literature** prompt to construct and execute systematic searches across academic databases. Document all queries in the literature search log.

**Output:** Search results with bibliographic details, search strategy documentation.

### Stage 2: Screening and Selection

**Input:** Search results from Stage 1, inclusion/exclusion criteria

Manual stage with AI assistance. Screen titles and abstracts against inclusion criteria, then screen full texts of remaining candidates. Document decisions in the search log and update the PRISMA flow diagram.

**Output:** Final set of included papers.

### Stage 3: Summarisation

**Input:** Included papers from Stage 2, research question

Invoke the **source-summarisation** skill via the **summarise-source** prompt for each included paper. Produce structured summaries covering methodology, findings, limitations, and relevance.

**Output:** Structured summaries for all included papers.

### Stage 4: Synthesis

**Input:** Paper summaries from Stage 3, research question

Invoke the **data-interpretation** skill via the **interpret-data** prompt to synthesise findings across papers. Identify themes, consensus, contradictions, and gaps.

**Output:** Synthesis report with thematic analysis.

### Stage 5: Literature Review Draft

**Input:** Synthesis report from Stage 4, paper summaries from Stage 3

Invoke the **literature-review-draft** prompt to produce a complete review organised by theme with proper citations.

**Output:** Literature review draft ready for revision.

## Error Handling

- If searches return too few results (under 10), broaden search terms or add databases
- If searches return too many results (over 500), add filters or narrow the research question
- If papers are inaccessible (paywalled), note them as excluded with reason and suggest alternatives
- If synthesis reveals insufficient evidence for a theme, flag it as a gap rather than speculating
