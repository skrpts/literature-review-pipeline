---
type: workflow
id: literature-review-pipeline
title: Literature Review Pipeline
description: "Search, summarise, synthesise, and write a literature review"
tags: [Production, Academic, Research]
connections:
  - target: literature-search
    type: uses
  - target: source-summarisation
    type: uses
  - target: data-interpretation
    type: uses
  - target: citation-extraction
    type: uses
  - target: methodology-assessment
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
  - target: llm-service
    type: runs_on
  - target: semantic-scholar
    type: runs_on
  - target: apa-7th-edition
    type: references
  - target: literature-search-log
    type: references
  - target: prisma-flow-diagram-template
    type: references
  - target: evidence-claim-check
    type: uses
  - target: dedup-and-merge
    type: uses
  - target: gap-analysis
    type: uses
metadata:
  estimated_duration: "30-60 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "literature-search"
  - "source-summarisation"
  - "data-interpretation"
  - "citation-extraction"
  - "methodology-assessment"
  - "evidence-claim-check"
  - "dedup-and-merge"
  - "gap-analysis"
  - "consistency-check"
  - "language-polish"
execution:
  - skill: "literature-search"
    prompt: "search-literature"
    step_type: "synthesis"
  - skill: "source-summarisation"
    step_type: "synthesis"
    prompt: "summarise-source"
  - skill: "data-interpretation"
    prompt: "interpret-data"
    step_type: "synthesis"
  - skill: "citation-extraction"
    prompt: "extract-citations"
    step_type: "synthesis"
    context:
      citation_style: "Harvard"
  - skill: "dedup-and-merge"
    step_type: "synthesis"
  - skill: "gap-analysis"
    prompt: "identify-research-gaps"
    step_type: "synthesis"
  - parallel:
    - skill: "evidence-claim-check"
      prompt: "check-evidence-claims"
      step_type: "review"
  - skill: "methodology-assessment"
    prompt: "assess-methodology"
    step_type: "review"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
  - parallel:
    - skill: "consistency-check"
      prompt: "check-consistency"
      step_type: "review"
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

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.research_question}}` | Yes | The research question guiding the review | "What is the impact of remote work on team productivity?" |
| `{{input.search_terms}}` | Yes | Key search terms and phrases | "remote work, telecommuting, team productivity, distributed teams" |
| `{{input.databases}}` | No | Target databases to search (defaults to Semantic Scholar) | "Semantic Scholar, PubMed" |
| `{{input.inclusion_criteria}}` | No | Criteria for including papers in the review | "Published 2019-2024, peer-reviewed, English language" |
| `{{input.exclusion_criteria}}` | No | Criteria for excluding papers | "Opinion pieces, conference abstracts only, non-empirical studies" |

## Outputs

| Name | Description |
|------|-------------|
| Literature review draft | A complete review organised by theme with proper citations |
| Search strategy documentation | Record of all queries, databases, and screening decisions |
| Paper summaries | Structured summaries of each included paper |
| Synthesis report | Thematic analysis identifying consensus, contradictions, and gaps |

## Setup

Before running this workflow:

1. **Semantic Scholar API access** — the literature search stage queries the Semantic Scholar API. No API key is required for basic access, but rate limits apply. For higher throughput, obtain a free API key from [Semantic Scholar](https://www.semanticscholar.org/product/api).
2. **Define your research question** — have a clear, focused research question and initial search terms ready before starting.

No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Works with any model — no specific provider requirements
- Longer context windows are beneficial when synthesising many paper summaries in Stage 4 and 5
- Estimated duration is 30-60 minutes depending on the breadth of the search

## Example Input

To test this workflow immediately after import:

```
Research question: "How does pair programming affect code quality and developer satisfaction?"
Search terms: "pair programming, code quality, developer satisfaction, collaborative coding, XP practices"
Inclusion criteria: "Peer-reviewed, published 2015-2024, empirical studies"
Exclusion criteria: "Grey literature, studies with fewer than 10 participants"
```
