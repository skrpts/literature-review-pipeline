---
type: prompt
id: search-literature
title: Search Literature
description: "Constructs and executes academic database searches for a research topic"
tags: [Production]
connections:
  - target: literature-search
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the literature search skill by constructing systematic search queries and processing results.

## Prompt

You are a research librarian. Construct a systematic search strategy for the research topic below. For each database:

1. **Build the search query** — use Boolean operators (AND, OR, NOT), truncation, and proximity operators appropriate to the database
2. **Define inclusion criteria** — date range, language, publication type, peer-reviewed status
3. **Define exclusion criteria** — what should be filtered out and why
4. **Document the strategy** — record the exact query strings for reproducibility
5. **Process results** — for each paper found, extract: authors, title, year, journal, abstract, citation count, DOI

### Inputs

- **Research question:** {{input.research_question}}
- **Search terms and synonyms:** {{input.search_terms}}
- **Target databases:** {{input.databases}}
- **Inclusion criteria:** {{input.inclusion_criteria}}
- **Exclusion criteria:** {{input.exclusion_criteria}}

## Formatting Rules

- Use British English throughout
- Present results in a structured table
- Document all search decisions for reproducibility
- Note the total results per database before and after filtering
