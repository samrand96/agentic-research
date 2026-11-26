# 7. Good practice: the rules that keep AI-assisted work publishable

## The honesty rule

No claim without a measured number on a named dataset. No citation without an opened source.
Every tool, and every author, may answer "unsure".

## Four golden rules

**1. Every citation opened and verified, never from memory.**
AI models can produce references that look real and do not exist, or real papers that do not say what
is claimed. Open the source, find the passage, record where it is (`docs/literature/verified-references.md`),
then cite it. Run the `citation-check` skill before you share any draft.

**2. A frozen protocol before the results are seen.**
Write hypotheses, sample, measures, analysis and tests in `docs/protocol/protocol.md`. Mark it FROZEN,
commit it and tag it (`git tag protocol-v1`). Only then analyse outcome data. Any later change is a
dated "deviation", reported in the paper. Optional: pre-register the protocol (for example on OSF).

**3. Plans and status files.**
One plan with phases and work packages (`docs/plans/`). One status file per work package, updated at
the end of each session with what is done, what is next, blockers and numbers measured. One branch
and one pull request per work package, and you read the diff before you merge.

**4. No secrets in files.**
API keys and tokens live in environment variables only. `.mcp.json` refers to them as `${NAME}`.
`.gitignore` keeps `.env`, keys and raw data out of git. Never paste a key into a chat, a slide or an email.

## Data, ethics and disclosure

- Anonymise participant data before any AI reads it. Check that your ethics approval and consent
  forms allow the AI tools you use, and where the data is processed.
- Keep raw data in the storage your ethics approval names, not in git and not on GitHub.
- Respect the terms of use of platforms you collect data from (for example review sites).
- Check your target journal's policy on AI use and disclose as it requires.
- AI tools are not authors. You are responsible for every word and number.

## A short checklist before you submit

- [ ] `citation-check` report: zero `NOT FOUND`, zero `NOT SUPPORTED`, zero `CANNOT OPEN`
- [ ] Every number in the paper is in a report made by a script
- [ ] Protocol frozen and tagged before the results; deviations reported
- [ ] Novelty claim matches `docs/literature/novelty-check.md`
- [ ] `git status` is clean; no keys, no raw data, no personal details in the repository
- [ ] AI use disclosed as the journal requires
