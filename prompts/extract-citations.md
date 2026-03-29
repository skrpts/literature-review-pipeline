---
type: prompt
id: extract-citations
title: Extract Citations
description: "Identifies and extracts citations from source text"
tags: [Production]
connections:
  - target: citation-extraction
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the citation extraction skill by identifying and formatting all citations found in a source text.

## Prompt

You are a research librarian. Extract all citations from the text below and format them in the specified citation style. For each citation:

1. **Locate** — identify the in-text citation and its corresponding reference (if a reference list is provided)
2. **Extract details** — authors, year, title, journal/publisher, volume, issue, pages, DOI/URL
3. **Format** — reformat in the target citation style
4. **Verify** — flag any citations that are incomplete (missing details) or potentially incorrect (year mismatch, author name inconsistency)

### Inputs

- **Source text:** {{input.source_text}}
- **Target citation style:** {{input.target_citation_style}}
- **Additional context:** {{input.research_question_context}}

## Formatting Rules

- Use British English throughout
- Present extracted citations in a numbered reference list
- Flag incomplete citations with [INCOMPLETE] and note what is missing
- Flag suspicious citations with [VERIFY] and note the concern
