# Release Notes

## v1.2.30
GH#818 Phase 1 (Tier 1) — fix intent-vs-output: the pipeline promised a written literature review but ran search/summarise/interpret/gaps/assess → polish (it polished the ANALYSIS). The `literature-review-draft` prompt was shipped but never wired in. Wire it on a dedicated local `literature-review-drafting` skill ("Literature Review Drafting"): …methodology → **literature-review-draft(draft)** → polish. Re-point its summaries ref to `{{steps.Source Summarization.output}}` (resolvable title). Polish binds `source` `from_step "Literature Review Drafting"`; coherent-lock all deps to current published (repin `polish-language` → 1.0.5 etc.). contents skills 1→2.

## v1.2.29
GH#749 Phase 1b — re-pin the summarise-source shared dep to v1.0.3 (position-safe prompt) and supply its source via `bindings: source_text` (from Literature Search). Restores the resolved source reference after the shared-prompt fix; no behavior change. Canonical scan clean.

## v1.2.28
GH#745 — declare per-step `output: {name, type}` on every execution step (sources/list, summaries/text, interpretation/text, citations/list, merged_sources/text, research_gaps/text, evidence_report/text, methodology_assessment/text, polished_review/text, consistency_verdict/decision). Lights up the #744 rich flow-map with named, typed outputs. Content-only; no bindings or logic changes.

## v1.2.27
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 22 inline shared-content files and declare 22 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.2.26
Wave 2: re-signed with canonical engine signing pipeline.

## v1.2.25
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.2.24
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.2.23
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.2.22
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
