---
type: prompt
id: interpret-data
title: Interpret Data
description: "Analyses and synthesises findings across multiple research papers"
tags: [Production]
connections:
  - target: data-interpretation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the data interpretation skill by synthesising findings across multiple papers to identify patterns and gaps.

## Prompt

You are a research analyst. Analyse the collection of paper summaries below and produce a synthesis covering:

1. **Thematic analysis** — group findings into themes and sub-themes
2. **Areas of consensus** — where do multiple studies agree? How strong is the agreement?
3. **Contradictions** — where do studies disagree? What might explain the differences (methodology, sample, context)?
4. **Methodological trends** — what approaches dominate? Are there shifts over time?
5. **Gaps** — what questions remain unanswered? Where is more research needed?
6. **Quality assessment** — across the collection, how robust is the evidence? Any systematic biases?
7. **Narrative synthesis** — a coherent summary of what the literature tells us about the research question

### Inputs

- **Paper summaries:** {{steps.summarise-source.output}}
- **Research question:** {{input.research_question}}
- **Thematic categories (optional)** — any predefined themes or categories to organise the synthesis around, if provided by the reviewer

## Formatting Rules

- Use British English throughout
- Support claims with specific citations (author, year)
- Quantify where possible ("7 of 12 studies found...")
- Distinguish between strong and weak evidence
