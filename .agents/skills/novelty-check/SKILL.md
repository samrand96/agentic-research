---
name: novelty-check
description: Check whether a research idea, contribution or claim is actually new by finding and reading the closest existing work. Use before claiming novelty, before writing the contribution or introduction, when asked "has this been done?", or when a reviewer questions originality.
---

# Novelty check

Goal: an honest answer to "is this new?", based on the closest papers, all of them opened and read.
The answer may be "no" or "only partly". That is a useful result.

## Steps

1. **State the claim** in one sentence, and split it into its parts:
   setting (e.g. a country, sector or population), construct or phenomenon, method, data, and outcome.
   Write it at the top of `docs/literature/novelty-check.md`.
2. **Search for each part and for combinations** with the `paper-search` MCP tools (OpenAlex,
   Semantic Scholar, Crossref, CORE, SSRN; Google Scholar as a cross-check). Also search for the
   claim in other words, and in neighbouring fields.
3. **Follow citations** of the two or three closest papers: who they cite, and who cites them.
4. **Pick the closest 10 papers** (or fewer if fewer exist). Open each one. If you cannot open one, say so.
5. **Compare** in a table in `docs/literature/novelty-check.md`:

   | Cite key | Setting | Method | Data | Finding | Same as our idea? | What differs |
   |---|---|---|---|---|---|---|

6. **Write the verdict** in plain words, one of:
   - *New*: no opened paper does this; say exactly which combination is new.
   - *Partly new*: name the papers that overlap, and what we add.
   - *Not new*: name the papers that already did it, and suggest how the idea could change.
7. **Draft a one-paragraph contribution statement** that names the closest papers and is no stronger
   than the evidence. Avoid "first ever" unless the search really supports it; prefer
   "to our knowledge, no study has …" with the search scope stated.

## Never

- Never declare something new because a quick search found nothing.
- Never rely on your own memory of the literature. Every comparison row is based on an opened paper.

## Done when

The novelty file has the claim, the search record, the comparison table with opened papers only,
a verdict, and a draft contribution statement for the author to approve.
