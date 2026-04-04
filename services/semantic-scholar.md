---
type: service
id: semantic-scholar
title: Semantic Scholar
description: "Academic paper search and citation graph API for literature discovery and retrieval"
tags: [Production, Tested, Academic, Research]
connections: []
metadata:
  serviceType: api
  auth_type: api_key_optional
---

## Semantic Scholar

External academic search API provided by the Allen Institute for AI. Used by the literature search stage to discover, retrieve, and filter scholarly papers programmatically.

### Capabilities

- **Paper search** — full-text and keyword search across 200M+ academic papers
- **Citation graph** — retrieve papers that cite or are cited by a given paper
- **Author lookup** — find all papers by a specific author
- **Bulk retrieval** — fetch metadata for a batch of paper IDs (DOI, ArXiv ID, Corpus ID)
- **Field filtering** — request only the fields you need (title, abstract, authors, year, citation count, etc.)

### Authentication

No API key is required for basic access. Rate limits apply:

- **Unauthenticated:** 100 requests per 5 minutes
- **Authenticated:** 1 request per second (sustained). Request a free API key at [semanticscholar.org/product/api](https://www.semanticscholar.org/product/api)

### Configuration

- **Base URL:** `https://api.semanticscholar.org/graph/v1`
- **Auth header:** `x-api-key: {your_key}` (optional)
- **Response format:** JSON
- **Pagination:** Offset-based (`offset` and `limit` parameters, max 100 per page)

### Usage in This Workflow

The literature search skill queries the paper search endpoint with the user's search terms and filters results by year, venue, and citation count. Results feed into the screening and quality assessment stages.
