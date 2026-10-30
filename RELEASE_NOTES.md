# Release Notes

## v1.2.34
GH#1100 consumer wave batch 6 — declare the data flow these steps were resolving positionally. 6 binding(s) added.

`identify-research-gaps` (slot "Prior Analysis") binds Data Interpretation rather than its positional predecessor, which emits merged sources. The interpretation is the prior analysis.

## v1.2.33
GH#1044 — the last of the required-but-undocumented inputs, resolved by testing whether the existing table name is itself required by a prompt rather than by how similar the names look. documented research_topic. Rows generated from the requiring prompt's own declared description, example and required flag. No behaviour change; documentation only.

## v1.2.32
GH#1044 — document the inputs this workflow's prompts REQUIRE but its Inputs table never listed. A user supplying exactly what the table asked for was running with required parameters unsatisfied — a silent wrong run, not a documentation nicety. documented 4 input(s): field_specific_standards, known_limitations, literature_summary, research_topic. Every row is generated from the requiring prompt's own declared description, example and required flag — none invented. No behaviour change; documentation only.

## v1.2.31
GH#1011 — 1 step(s) that declared the non-existent `local.transform` now declare the LLM step type they were already dispatched as, and reference the shared prompt their skill never had: `dedup-and-merge` → `synthesis`.

These steps had no `prompt:` because `local.*` types need none, so the engine's LLM default had nothing to send: the author saw the model complaining about a prompt nobody wrote. **Output changes** — from a complaint to the thing the skill describes. Shared deps re-pinned to 1.0.4 with the published bundle checksum.

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
