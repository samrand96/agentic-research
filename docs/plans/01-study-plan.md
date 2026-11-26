# Study plan — [working title]

> The plan splits the study into **phases**, and each phase into **work packages (WPs)**.
> A work package is a piece of work one person (or one AI session) can finish and hand over.
> Each WP has its own status file in `status/`, its own git branch, and its own pull request.
> Lines starting with `DECISION:` are for the author to decide. An AI stops there.

**Research question:** [copy from AGENTS.md]
**Target journal:** [name] · **Planned submission:** [month year]

---

## Phase 0 — Set-up

### WP0.1 Project folder and rules
- **Goal:** folder from the template, AGENTS.md filled in, git and a private GitHub repo.
- **Owns (may change):** `AGENTS.md`, `CLAUDE.md`, `.gitignore`, `.mcp.json`
- **Done when:** first commit pushed; `/mcp` shows paper-search and zotero connected.

## Phase 1 — Literature and novelty

### WP1.1 Search and screening
- **Goal:** a repeatable search with counts at every stage.
- **Owns:** `docs/literature/search-log.md`, `docs/literature/verified-references.md`
- **Skill:** `literature-review`
- **Done when:** every included paper is opened and in Zotero; counts logged.
- `DECISION:` inclusion and exclusion criteria.

### WP1.2 Novelty check
- **Goal:** honest answer to "is our idea new?"
- **Owns:** `docs/literature/novelty-check.md`
- **Skill:** `novelty-check`
- **Done when:** comparison table of the closest papers (all opened) and a verdict.
- `DECISION:` final framing of the contribution.

## Phase 2 — Protocol (the gate)

### WP2.1 Write and freeze the protocol
- **Goal:** hypotheses, sample, measures, analysis plan and tests written down **before** outcome data is analysed.
- **Owns:** `docs/protocol/protocol.md`
- **Done when:** the author marks it FROZEN; committed and tagged (`git tag protocol-v1`).
- `DECISION:` approve and freeze. Optional: pre-register it (e.g. on OSF).

## Phase 3 — Data and analysis

### WP3.1 Data collection and cleaning
- **Goal:** clean, anonymised data, made by scripts from the raw data.
- **Owns:** `analysis/01-clean.*`, `data/processed/` (not in git)
- **Done when:** a cleaning report in `docs/reports/` with counts (received, excluded and why, kept).

### WP3.2 Analysis as planned
- **Goal:** run the frozen analysis plan.
- **Owns:** `analysis/02-*.*`, `docs/reports/results.md`, `figures/`
- **Done when:** every result in the report comes from a script that runs from start to end.

## Phase 4 — Writing and submission

### WP4.1 Draft sections
- **Skill:** `write-section` (and `docx` for Word output)
- **Owns:** `paper/`

### WP4.2 Citation check and submission package
- **Skill:** `citation-check`
- **Owns:** `docs/reports/citation-check-*.md`, `paper/`
- **Done when:** zero `NOT FOUND` or `NOT SUPPORTED`; cover letter drafted; journal checklist done.
- `DECISION:` submit.
