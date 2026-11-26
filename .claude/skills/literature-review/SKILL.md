---
name: literature-review
description: Search, screen and log the scholarly literature for this project with verified citations only. Use when asked to find papers, do a literature search or review, map prior work, build a reading list, or update the search log.
---

# Literature review with verified citations

Goal: a literature search that another researcher could repeat, and a reading list in which every
paper exists, was opened, and is in Zotero.

## Before you start

1. Read `AGENTS.md` (question, scope, honesty rules) and the status file of the current work package.
2. Read `docs/literature/search-log.md` so you do not repeat earlier searches.
3. If the author has not given inclusion and exclusion criteria, propose them and **stop for approval**.

## Steps

1. **Plan the search.** Write the search strings (synonyms, Boolean operators), the databases, and the
   date range in `docs/literature/search-log.md` *before* running them. Good general sources are OpenAlex,
   Semantic Scholar, Crossref, CORE and SSRN; add PubMed or Europe PMC for health topics, and Google Scholar only as a cross-check.
2. **Run the searches** with the `paper-search` MCP tools. For each query, log: date, database, exact
   string, filters, number of hits.
3. **De-duplicate** by DOI first, then by title and year. Log how many duplicates were removed.
4. **Screen titles and abstracts** against the criteria. For every excluded paper, give a one-line reason.
   Log the counts at each stage (identified → after duplicates → screened → full text assessed → included),
   so a PRISMA-style flow can be drawn.
5. **Open every included paper.** Read the abstract page or full text through its DOI or an open-access
   copy (Unpaywall, CORE, arXiv, SSRN). If you cannot open it, mark it `NOT OPENED` and do not use it
   for any claim.
6. **Add included papers to Zotero** (through the `zotero` MCP server, or list DOIs for the author to add).
   Use the Better BibTeX cite key in all notes.
7. **Extract** for each included paper, in `docs/literature/verified-references.md`: cite key, DOI,
   setting (country, sector), method, sample, main finding, and the exact location (page/section)
   of anything you may cite later.
8. **Synthesise** in `docs/reports/literature-map.md`: themes, agreements, contradictions, gaps.
   Every sentence that states a finding ends with a cite key that is in the verified list.

## Never

- Never cite a paper from memory or from a search snippet alone.
- Never invent a DOI, page number or quote. Use `[CITATION NEEDED]` instead.
- Never use the Sci-Hub download option.
- Never save publisher PDFs into a folder that is committed to git (`references/pdfs/` is ignored).

## Done when

- The search log has every query with its counts.
- Every included paper is opened, in Zotero, and in the verified list with a location for each claim.
- The status file of the work package is updated with the counts.
