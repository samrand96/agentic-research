---
name: write-section
description: Draft or revise one section of the paper (introduction, literature review, method, results, discussion, conclusion or abstract) from the author's notes, the verified reference list and the results reports. Use when asked to write, draft, rewrite or shorten a section of the manuscript.
---

# Write one paper section

Goal: one section, in the target journal's style and the author's voice, in which every claim is
backed by a verified source or a result from a script.

## Inputs to read first

- `AGENTS.md`: target journal, style, word limit, writing voice.
- The journal's author guidelines (open the link in AGENTS.md; check the required section headings).
- `docs/literature/verified-references.md`: the only sources you may cite.
- `docs/reports/`: the only numbers you may report.
- `docs/protocol/protocol.md`: for the method section, describe what the protocol says, and mark any deviation.
- The author's notes or outline for this section, if any.

## Steps

1. **Outline first.** Write a bullet outline with one point per paragraph and the sources or results each
   paragraph will use. Show it to the author if the section is new.
2. **Draft** paragraph by paragraph. One idea per paragraph; topic sentence first.
3. **Cite as you write**, using Better BibTeX cite keys, e.g. `[@smith2021]`, or in the
   journal's style if the author asked for a Word file. Only cite keys that appear in the verified list.
   If a claim needs a source you do not have, write `[CITATION NEEDED]`.
4. **Numbers**: copy them from the reports, with the same rounding. Never compute a number in your head.
5. **Section-specific checks**
   - Introduction: problem, gap (from the novelty check), question, contribution, structure.
   - Method: enough detail to repeat the study; ethics approval and consent; data anonymisation.
   - Results: report what was pre-registered in the protocol first; label exploratory analyses as exploratory.
   - Discussion: compare with named prior studies; limitations stated plainly; no claims beyond the data.
6. **Save** to `paper/` (Markdown, or Word with the `docx` skill if the author asked for Word).
7. **Hand over** a short list: claims marked `[CITATION NEEDED]`, numbers to double-check, and
   word count against the limit.

## Never

- Never add a reference that is not in the verified list.
- Never report a number that is not in a report produced by a script.
- Never present the AI's wording as a quotation from a source.
