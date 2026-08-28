# prd-template

A Claude Code skill that turns a case study into a full PRD template — the same
13-section "What this section covers / How to build it / Example / Pressure-test
questions" structure used across this course, adapted to whatever the new case
actually needs.

It was built by generalizing the process used to turn a vendor-management case
study's PRD template into one for a "Learning Tech & AI" case study: read the
shared shell, diagnose where the new case differs (problem given vs. open,
B2B vs. individual, what data exists, whether all deliverables have a home in
the 13 sections), flag every mismatch instead of silently guessing, then
generate the adapted document.

## Install

Drop this folder at `~/.claude/skills/prd-template/` (already done if you're
reading this from there). Claude Code picks up any folder under
`~/.claude/skills/` automatically — no restart needed.

## Use it on a new case study

```
/prd-template <path to a case-study file>
```

or, if there's no formal document yet:

```
/prd-template <paste a description of the new case study in the prompt>
```

Both work. A file (.docx/.pdf/.txt/.md) is preferred when one exists because
the skill grounds every example and flag in what the case actually says — but
a pasted paragraph is enough to start.

### What happens, step by step

1. **It reads `reference/meta-template.md`** — the case-agnostic shell (13
   section skeletons + front matter + the underlying methodology: double
   diamond, value÷effort prioritisation, the design iceberg, six UX
   components, the AARRR/metrics stack). This file has no case-specific
   content in it — it's the DNA every PRD is grown from.

2. **It reads your case study** and diffs it against that shell. It's
   checking things like:
   - Is the problem actually given, or do you have to find it? (This changes
     how much weight §1–6 discovery carries — a lot, if the problem is open.)
   - Is this a multi-team B2B workflow, or an individual/B2C journey? (§2
     gets reframed accordingly — approval chain vs. influence map.)
   - Does the case supply real numbers/facts, or none at all? (If none, every
     example gets marked `ILLUSTRATIVE` with a note to source it yourself —
     nothing gets invented and presented as fact.)
   - Do the case's deliverables ask for something none of the 13 sections
     cover (e.g. real users, a growth loop, a specific live artifact)? If so,
     it'll propose a new numbered section rather than force-fitting.
   - Is there a scoring rubric or sprint length in the case? If not, those
     get a placeholder and a flag, not a guess.

3. **It hands you a short markdown review doc** — every proposed rename,
   reweight, flag, and new/dropped section, one page, one pass. You read it
   and edit or confirm. Nothing gets built yet at this point.

4. **Once you confirm, it writes the full PRD** as structured markdown, then
   runs `scripts/generate_docx.py` to turn it into a `.docx` with the same
   visual language every time — blue bold section labels, red bold flag
   callouts, gridded tables — saved to your Downloads folder by default.

5. **It may suggest evolving the meta-template.** If your new case needed a
   pattern that feels reusable beyond it (e.g. a second case in a row needing
   a growth-loop section), it'll flag that as a one-line suggestion to fold
   into `reference/meta-template.md` — never auto-applied, always your call.

### Example

> `/prd-template C:\Users\you\Downloads\Case Study 5.docx`

→ Claude reads the case, reports back something like: *"This one's B2B like
the vendor case (not open like the AI-learning one) — discovery can stay
lean. No rubric or sprint length given, flagging both. Deliverables fit
cleanly in the 13 sections, no new section needed."* → you confirm → it
generates `PRD Template - <Case Title>.docx` in Downloads.

## Files

- `SKILL.md` — the skill's own instructions (what Claude follows when you
  invoke `/prd-template`)
- `reference/meta-template.md` — the case-agnostic shell
- `scripts/generate_docx.py` — markdown → `.docx` converter; see the DSL
  documented at the top of the file and in `SKILL.md` if you want to hand-edit
  the generated markdown before the docx step

## Editing the meta-template yourself

It's a plain markdown file — safe to hand-edit directly if you want to adjust
the base methodology or add a section that should be standard going forward,
rather than waiting for the skill to propose it after a third case needs it.
