---
type: prompt
id: extract-citations
title: "Extract Citations"
description: "Identifies and formats citations from text into a consistent style"
tags: [Production, Academic]
inputs:
  citation_style:
    label: "Citation Style"
    description: "The academic citation format to use"
    example: "APA 7th Edition"
    required: true
    type: text
connections:
  - target: citation-extraction
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the citation extraction skill.

## Prompt

You are a reference librarian. Extract and format all citations from the text below.

### Text to Process

{{steps.previous.output}}

### Citation Style

{{input.citation_style}}

### Instructions

1. **Identify** every citation in the text — in-text references, footnotes, endnotes, and bibliography entries
2. **Extract** the bibliographic details for each: author(s), year, title, source, volume, issue, pages, DOI/URL
3. **Reformat** each citation into the specified style
4. **Flag** any incomplete citations missing required fields

### Output

**In-text citations found:**
List each citation as it appears in the text with its location.

**Formatted reference list:**
Full bibliography in the specified style, alphabetically ordered.

**Issues:**
Any citations with missing information or formatting problems.

## Formatting Rules

- Use British English throughout
- Be specific and actionable — no vague recommendations
- Structure output clearly with headings, tables, or lists as appropriate
