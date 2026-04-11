---
type: prompt
id: search-literature
title: Search Literature
description: "Constructs and executes academic database searches for a research topic"
tags: [Production, Academic, Research]
inputs:
  research_question:
    label: "Research Question"
    description: "The specific research question to address"
    example: "How does sleep duration affect cognitive performance in university students?"
    required: true
    type: text
  search_terms:
    label: "Search Terms"
    description: "Terms to use in the search"
    example: "sleep AND (cognitive OR academic) AND (student OR university)"
    required: true
    type: text
  databases:
    label: "Databases"
    description: "Databases to search"
    example: "PubMed, Scopus, Web of Science"
    required: true
    type: text
  inclusion_criteria:
    label: "Inclusion Criteria"
    description: "Criteria for including studies"
    example: "Published after 2015, English language, peer-reviewed"
    required: true
    type: text
  exclusion_criteria:
    label: "Exclusion Criteria"
    description: "Criteria for excluding studies"
    example: "Animal studies, conference abstracts only, non-English"
    required: true
    type: text
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
