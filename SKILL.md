---
name: prd-template
description: Generate a full PRD template (13 sections + appendices, "What this section covers / How to build it / Example / Pressure-test questions" under each) adapted to a specific case study, mirroring the course's reusable PRD structure. Use when the user gives a new case study and wants a PRD template built for it, or asks to turn a case study into a PRD, or references "the PRD structure" for a new case.
---

# PRD Template Generator

Turns a case-study brief (file or pasted description) into a full PRD template docx, by adapting the course's reusable 13-section shell to that specific case — the same judgment process used manually the first time this was done (vendor-management case → learning-tech-and-AI case).

This skill does NOT invent case facts. Every number, stat, or example either comes from the case source, or is explicitly marked `ILLUSTRATIVE` with a note to source it, or flagged as missing.

## Inputs

- **Case source** (required): a file path to a case-study document (.docx/.pdf/.txt/.md), OR pasted/verbal description of the case in the conversation. Both are valid — don't require a formal document.
- **Output path** (optional): defaults to the user's Downloads folder if not given.

## Assets

- `reference/meta-template.md` — the case-agnostic shell: generic front matter (title block shape, scoring-rubric shape, sprint-map shape, contents shape) plus all 13 sections' generic What/How/Example/Pressure-test structure and the underlying methodology (double-diamond, product-value template, value÷effort/ROI prioritisation, design iceberg, six UX components, AARRR + metrics stack). This file has NO case-specific content — treat it as the DNA every generated PRD is grown from.
- `scripts/generate_docx.py` — converts a structured markdown file (see DSL below) into the final styled `.docx`, reusing the fixed visual style established for this template family (blue bold section labels, red bold flag callouts, "Light Grid Accent 1" tables). Do not restyle per run — the consistency is intentional.

## Workflow

**1. Read the meta-template.** Load `reference/meta-template.md` in full before doing anything else.

**2. Read the case source.** If it's a file, extract its text (for .docx: copy to a .zip, expand, regex out `<w:t>` runs — see "Extracting docx text" below; for .pdf/.txt/.md, read directly). If it's pasted text, use it as-is.

**3. Diff the case against the meta-template.** For each of the 13 sections, and for the front matter, work out:
   - Is the underlying assumption still true? (e.g. is the problem actually given, or does the user have to find it? Is this B2B multi-stakeholder or B2C/individual? Is there a buyer distinct from the user?)
   - Does the case supply concrete numbers/facts to seed the "Example · this case" blocks, or none at all?
   - Does the case's deliverable list ask for anything the 13 sections have no slot for (e.g. real users, a growth loop, a live build, a specific artifact)? If so, a new numbered section may be warranted — don't force-fit.
   - Should any section be renamed because its title assumes something this case doesn't have (e.g. "The Given Problem" when the problem isn't given; "Stakeholder Mapping" when there's no multi-team enterprise workflow)?
   - Is there a scoring rubric / sprint length in the case? If not, the front-matter scaffolds get filled with placeholders and flagged as unconfirmed, not invented.

   Use the six-flag pattern from the learning-tech-and-AI case as the model for how deep this diff should go: problem-given vs. open, stakeholder shape, data availability, rubric availability, section-coverage gaps, timeline assumptions.

**4. Produce a review doc — markdown, one pass, not interactive.** Before writing the full PRD, output a short markdown summary (like the "Read First" section from the first run) listing every proposed rename, reweight, flag, and new/dropped section, each with a one-line reason. Present this to the user and wait for their confirmation or edits. Do not generate the docx yet.

   Include a **Recurring-pattern check** block in this same review doc: one line per known recurring mentor-feedback pattern (see list below), stating whether this case's draft is at risk and why, or "no risk flagged" if not applicable.
   - Interpretation presented as fact (claims not visibly separated from the evidence behind them)
   - Premature convergence (a conclusion reached without showing why alternatives were ruled out)
   - Unexplained scoring (a rubric or T-shirt-size scale applied without stating what it measures)
   - Unprioritized open questions/gaps (a list treated as equally important with no must-validate vs. nice-to-know split)
   - Solution described as a feature list (missing feature-level flow, edge cases, or failure states)
   - Problem statement over-justifying itself (defensive validity arguments crowding out who/what/why)

**5. Once confirmed, write the full structured markdown** for the entire PRD (front matter + all sections, in the DSL below), adapting every section's content to the case — same depth as the meta-template's originals, not abbreviated.

**6. Run `scripts/generate_docx.py`** on that markdown to produce the final `.docx`. Save to the output path (default: Downloads), named `PRD Template - <Case Title>.docx`.

**7. Propose (don't apply) meta-template evolution.** If this case needed a pattern that feels reusable beyond it (e.g. a second case in a row needing a growth-loop-style section), flag it to the user as a one-line suggestion: fold it into `reference/meta-template.md` as a standing optional section, or leave it case-specific. Only edit the meta-template file if the user says yes.

## Markdown DSL the script expects

Write the final structured markdown using these exact conventions — `generate_docx.py` parses them heuristically:

- `# Title` → Heading 1 (used for numbered sections and top-level headers)
- `## Subtitle` → Heading 2
- A line that is entirely `**LABEL TEXT**` (e.g. `**WHAT THIS SECTION COVERS**`) → styled blue bold label paragraph
- A line starting with `⚠ FLAG:` → styled red bold callout paragraph
- A line starting with `- ` → bullet list item
- A line that is entirely `*italic text*` → italic paragraph
- A markdown table (`| col | col |` rows, with a `|---|---|` separator row) → Word table, "Light Grid Accent 1" style, header row bolded
- A line containing only `\pagebreak` → page break
- Anything else → plain paragraph

## Extracting docx text (PowerShell, no admin/deps beyond what's already installed)

```powershell
$src = "<path to .docx>"
$zipPath = "$env:TEMP\case_extract.zip"
Copy-Item $src $zipPath -Force
$dst = "$env:TEMP\case_extract_ps"
if (Test-Path $dst) { Remove-Item -Recurse -Force $dst }
Expand-Archive -Path $zipPath -DestinationPath $dst
$xml = Get-Content -Raw "$dst\word\document.xml"
$texts = [regex]::Matches($xml, '<w:t[^>]*>([^<]*)</w:t>') | ForEach-Object { $_.Groups[1].Value }
$texts -join "`n" | Out-File -FilePath "$env:TEMP\case_text.txt" -Encoding utf8
```

Then read `$env:TEMP\case_text.txt` with the Read tool.

## Principles carried over from the first build

- **Evidence vs. interpretation stay visibly separate.** Any synthesized claim of the form "the evidence shows X" must be distinguishable from "we read this as meaning Y" — this applies everywhere findings get synthesized (secondary research so-whats, Key Insights, primary research findings, opportunity BECAUSE clauses), not just one section. This was the single most-repeated mentor critique across past cases (same note, same section type, two case studies in a row) — treat it as a standing check on every synthesis paragraph, not a one-section fix.
- Never invent case facts. Mark invented-shape examples `ILLUSTRATIVE — derive your own`.
- Discovery weight is not fixed — it depends on whether the problem is given (light discovery, vendor-management-style) or open (heavy discovery, learning-tech-and-AI-style). Diagnose this per case, don't assume.
- A rubric or sprint length the case doesn't supply gets a placeholder + flag, never a guessed number presented as fact.
- New sections are allowed when the case's deliverables have no home in the 13 — flag them as additions, don't silently renumber the original 13 out of existence.
