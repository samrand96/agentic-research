---
name: citation-check
description: Check every citation and reference in a draft — that each source exists, the metadata (authors, year, title, journal, DOI) is right, and the source really says what the text claims. Use before sharing a draft, before submission, after any AI-assisted writing, or when asked to verify, audit or fact-check references.
---

# Citation check

Goal: a report that lists every citation in the draft with a verdict, so that no invented, wrong or
misquoted reference reaches a reviewer.

## Steps

1. **List every citation** in the draft (in-text cite keys or author-year citations) and every entry in
   the reference list. Flag citations with no reference entry, and reference entries never cited.
2. **Check that each source exists.** For each reference:
   - If it has a DOI, resolve it through Crossref (the `paper-search` MCP has a Crossref DOI lookup) and
     compare authors, year, title, journal, volume and pages.
   - If it has no DOI, search by exact title in OpenAlex and Semantic Scholar, then Google Scholar.
   - Check it is in the Zotero library (`zotero` MCP).
3. **Check that the source says it.** For each sentence that cites the source, open the source
   (full text, or at least the abstract page) and find the passage. Record the page or section.
   Quotations must match word for word.
4. **Check the reference style** against the journal (e.g. APA 7th) — but only after steps 2 and 3.
5. **Write the report** to `docs/reports/citation-check-<date>.md` with one row per citation:

   | Citation | Exists? | Metadata correct? | Claim supported? | Where in source | Action |
   |---|---|---|---|---|---|

   Verdicts: `OK`, `FIX METADATA`, `NOT SUPPORTED`, `CANNOT OPEN`, `NOT FOUND`.
6. **Summarise at the top**: number of citations checked, and counts per verdict.

## Rules

- `NOT FOUND` means it must be removed or replaced by the author. Never "fix" a citation by inventing
  plausible details.
- `CANNOT OPEN` is not a pass. The author must open it, or the claim must go.
- Do not change the draft yourself unless asked; the report is the output.

## Done when

Every citation has a verdict, and the summary says how many need action.
