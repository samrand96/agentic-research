# 5. Skills: recipes for research writing

A **skill** is a folder with one text file, `SKILL.md`: a name, a description of when to use it, and the
steps. The assistant loads a skill only when the task fits the description, or when you call it by name.
**The same SKILL.md works in Claude Code and Codex.**

| | Claude Code | Codex |
|---|---|---|
| Project skills folder | `.claude/skills/<name>/SKILL.md` | `.agents/skills/<name>/SKILL.md` |
| Your skills for all projects | `~/.claude/skills/` | `~/.agents/skills/` |
| Use a skill | `/skill-name` | `$skill-name` (or `/skills` to list them) |

Docs: https://code.claude.com/docs/en/skills · https://learn.chatgpt.com/docs/build-skills

## The four research skills in this toolkit

They are already in `.claude/skills/` (Claude) and `.agents/skills/` (Codex), so they work in every copy of this template. If you edit one, copy it to the other folder.

| Skill | What it does |
|---|---|
| `literature-review` | Plans and logs the search, screens papers, opens every included paper, files them in Zotero |
| `novelty-check` | Finds and reads the closest existing work, then gives an honest "new / partly new / not new" |
| `write-section` | Drafts one paper section from your notes, verified sources and results reports |
| `citation-check` | Opens every reference: does it exist, is the metadata right, does it say what we claim? |

Try: *"Use the literature-review skill to plan a search on my research question in AGENTS.md."*

## Where skills live

| Location | Works in | Shared through git? |
|---|---|---|
| `.claude/skills/<name>/SKILL.md` inside a project | that project | Yes |
| `~/.claude/skills/<name>/SKILL.md` in your home folder | all your projects | No |
| `.agents/skills/<name>/SKILL.md` inside a project (Codex) | that project | Yes |
| `~/.agents/skills/<name>/SKILL.md` in your home folder (Codex) | all your projects | No |

To use the four skills in **all** your projects, copy the four folders into `~/.claude/skills/` (Claude) and/or
`~/.agents/skills/` (Codex). On Windows, `~` means `C:\Users\<you>`.

## Skills from others

**Anthropic's skills, for Claude** (Word, PowerPoint, PDF, Excel, skill-creator and more):
https://github.com/anthropics/skills. Inside Claude Code:

```
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

Many of these skills are Apache 2.0; check each skill's own licence file. The repository describes
itself as for demonstration and education. Plugins: https://code.claude.com/docs/en/discover-plugins

**Community research skills** (example): https://github.com/Imbad0202/academic-research-skills,
which includes `academic-paper`, `academic-paper-reviewer` (a tough "Reviewer 2"), `academic-pipeline` and
`deep-research`. Licence: CC BY-NC 4.0 (non-commercial). Install inside Claude Code:

```
/plugin marketplace add Imbad0202/academic-research-skills
/plugin install academic-research-skills
```

Before installing any skill or plugin from someone else: read its SKILL.md files and licence.
A skill is instructions your assistant will follow.

**Charts:** a data-visualisation skill (`dataviz`) is available in some Claude app setups. Without it,
ask Claude for a plotting script (for example Python with matplotlib) and keep the script in `analysis/`.

## Make your own

1. Create `.claude/skills/interview-coding/SKILL.md` with:

   ```
   ---
   name: interview-coding
   description: Code interview transcripts with our codebook. Use when asked to code or re-code transcripts.
   ---
   1. Read docs/codebook.md first.
   2. Code each transcript; cite line numbers.
   3. Save to analysis/coding/<id>.md.
   4. Never invent quotes; flag unclear lines.
   ```

2. Copy the same folder to `.agents/skills/interview-coding/` for Codex.
3. Use it: `/interview-coding` in Claude, `$interview-coding` in Codex, or just describe the task.
4. Easiest: ask *"use skill-creator to make a skill for coding my interviews"*. Codex has skill-creator built in;
   for Claude it is in Anthropic's repository above.

Good skills are short, have a precise description (it decides when the skill is used), say what
"done" looks like, and list what must never happen.
