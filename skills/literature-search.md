---
type: skill
id: literature-search
title: Literature Search
description: "Searches academic databases and catalogues for papers matching a research topic"
tags: [Tested, Academic, Research]
connections:
  - target: llm-service
    type: runs_on
  - target: semantic-scholar
    type: requires
---

## Capability

Searches academic databases and catalogues for papers, articles, and books matching a research topic or question. Constructs search queries using Boolean operators, filters by date range, publication type, and citation count, and returns structured results.

## When to Use

- Starting a new literature review
- Expanding an existing review to cover additional databases
- Checking for recently published work on a topic
- Verifying completeness of a search strategy

## Inputs

Research question or topic, target databases, date range, inclusion/exclusion criteria, search terms and synonyms

## Outputs

Structured search results: bibliographic details, abstracts, citation counts, relevance scores, and full-text availability status. Also produces the search strategy documentation (databases searched, query strings used, results per database) for reproducibility.

## Limitations

- Relies on database APIs for access — paywalled full texts require institutional access
- Citation counts may lag behind actual citations by several months
- Cannot assess quality of papers — only retrieves and ranks by relevance and citations
