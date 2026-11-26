# AGENTS.md — house rules for every AI assistant in this project

> Every AI assistant that works in this folder reads this file first. Codex reads it directly;
> Claude Code reads it through CLAUDE.md. Other tools (Gemini, Cursor and more) read it too.
> Fill in the parts in [square brackets]. Delete the hints in italics when you are done.
> Keep it short: this file is read at the start of every session.

---

## 1. The project

- **Working title:** [Your paper's working title]
- **Research question:** [One sentence. Example shape: "How does X affect Y among Z in setting W?"]
- **Field:** [Your field and sub-field]
- **Method:** [e.g. survey + PLS-SEM / semi-structured interviews + thematic analysis / review of online reviews]
- **Target journal:** [Journal name]. Style: [APA 7th]. Word limit: [number]. Author guidelines: [link to the journal's own page]
- **Authors:** [Use initials or roles only, e.g. "Lead author (A.B.)". Do not put emails, phone numbers or addresses here.]

## 2. Where things are

Read these before doing any task:

1. `docs/plans/01-study-plan.md` — the plan: phases and work packages (WPs).
2. `docs/plans/status/` — one status file per work package. Read the one for the WP you are working on.
3. `docs/protocol/protocol.md` — the analysis protocol. Once it says **FROZEN**, it may not be changed.

| Folder | What goes there |
|---|---|
| `docs/literature/` | search log, verified reference list, novelty check |
| `docs/reports/` | results reports, each with the script that made it |
| `references/library.bib` | exported automatically from Zotero (Better BibTeX). Never edit by hand. |
| `data/raw/` | original data. **Never edited, never committed to git, never sent to an online service without anonymisation.** |
| `data/processed/` | cleaned data, made by scripts in `analysis/` |
| `analysis/` | scripts. Every number in the paper comes from a script here. |
| `figures/` | charts, made by scripts |
| `paper/` | the manuscript |

## 3. Honesty rules (never break these)

1. **No citation from memory.** Cite only sources that are in the Zotero library and that you have opened in this project. For each citation, record where the claim is in the source (page, section or paragraph) in `docs/literature/verified-references.md`.
2. **If a reference cannot be found or opened, say so.** Write `[CITATION NEEDED]` in the draft. Never invent an author, title, year, DOI, page number or quote.
3. **No number without a source.** Every number in the paper comes from a script in `analysis/` or from an opened, cited source.
4. **"Unsure" is an allowed answer.** If the evidence is weak, say so in plain words.
5. **Frozen protocol.** Do not look at outcome results before `docs/protocol/protocol.md` is marked FROZEN and committed. After that, any change to the analysis is reported as a deviation in the paper.
6. **Quotes are exact.** A quotation from a paper or an interview is copied, never paraphrased inside quotation marks, and its location is given.

## 4. Privacy and secrets

- API keys and tokens live only in environment variables. Never write them in any file, chat, commit message or slide.
- Never put anyone's email address, phone number or home address in a file in this project.
- Participant data (interviews, survey responses) is anonymised before any AI reads it. Names of people and small organisations are replaced with codes.
- Never send, post, submit or delete anything on the author's behalf. Draft it and ask.

## 5. How to work

- **The author is a researcher, not a programmer.** Explain every step in plain
  language, avoid technical jargon, and say what each command does before running it.
- [Language: the author may write to you in Chinese or English. Write the paper itself in English unless told otherwise.]

- Work on **one work package at a time**, on its own git branch (`wp/<number>-<short-name>`).
- At the end of each session, update that work package's status file: what is done, what is next, blockers, numbers measured.
- Commit before any large change, so it can be undone.
- Ask before installing software or downloading anything large.
- Stop at **decision points** marked `DECISION:` in the plan. Prepare the options; the author decides.

## 6. Writing voice

- [Clear, plain academic English. Short sentences. Active voice where possible.]
- [No buzzwords: avoid "delve", "tapestry", "pivotal", "landscape", "in today's fast-paced world".]
- [Spelling: British or American — pick one.]
- Define every abbreviation the first time it appears.

## 7. Skills in this project

Recipes for recurring tasks live in `.claude/skills/` (Claude Code) and `.agents/skills/` (Codex).
The two folders hold the same files. Use one with `/name` in Claude Code or `$name` in Codex:

- `literature-review` — search, screen and log the literature.
- `novelty-check` — find the closest existing work before claiming anything is new.
- `write-section` — draft one section of the paper from notes and verified sources.
- `citation-check` — open every reference and confirm it exists and says what we claim.
