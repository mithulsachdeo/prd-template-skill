# PRD Meta-Template (case-agnostic)

This is the reusable shell behind every case-study PRD built with the `prd-template` skill. It carries no case-specific content — every `[bracketed]` placeholder and every "adapt this" note must be filled in fresh for each case. Do not copy any concrete numbers, company names, or examples from a previous case into a new one.

## How the source template explains itself (keep this framing, adapt the wording)

This document is a **format**, not a finished submission. Every section explains **what it must cover**, **how to build it well**, and the **pressure-test questions** you must answer before moving on.

Blocks, per section:
- **What this section covers** — the mandatory content.
- **How to build it** — the craft: how to make it hold up under scrutiny.
- **Example / Suggested format** — either a reusable format (safe to reuse the shape as-is) or an `ILLUSTRATIVE` block (shape only — the specifics are invented, do not copy them; derive your own from the case).
- **Pressure-test questions** — the self-check gate before moving to the next section. If you can't answer one with evidence, that's the question an examiner/mentor will ask.

## Front matter (adapt per case)

- **Title block**: [Case name] · Product Requirements Document · [Week/Case label] · one-line tagline naming what's being built and for whom.
- **What's different this time**: name whether the problem is GIVEN (discovery stays lean, everything downstream carries the weight) or OPEN (the team must find the problem, so discovery carries real weight) — diagnose per case, don't assume.
- **Golden rule**: name the lock point — after problem/persona/scope are locked, no major pivots; execution discipline takes over.
- **Ownership & pace**: who owns product decisions; how many days in the sprint; what ships by the end (PRD only? PRD + live demo? PRD + real users?).
- **Scoring table** (only if the case supplies a rubric — otherwise placeholder + flag, never invented):

  | Where the points are | Which sections carry it | Points |
  |---|---|---|
  | Discovery (research + insights) | Sections 1–6 | ? |
  | Opportunity — prioritisation | Section 7 | ? |
  | Product thinking — focused MVP | Sections 8–10 | ? |
  | Analytics — metrics & tracking | Section 12 | ? |
  | Solution design — workflow & UX | Sections 9, 11, 13 | ? |
  | Communication — clarity & story | Whole document + demo | ? |

- **Sprint map** (only if the case supplies a day count/deadline — otherwise assume from today's date and flag the assumption):

  | Sprint day | What you do | PRD section it feeds |
  |---|---|---|
  | Day 1 — Understand | Read case, hypotheses, quick or deep research depending on whether the problem is given | §1–6 |
  | Day 2 — Converge | Lock problem, persona, scope, journey | §7–8 |
  | Day 3 — Ideate | Multiple directions, trade-offs, user flow | §9 |
  | Day 4 — Detail | Features, edge cases, IA, MVP scope | §10 |
  | Day 5 — Design | High-fidelity UX | §11 |
  | Day 6 — Analytics | Events, funnels, North Star, tracking plan | §12 |
  | Day 7+ — Build | Frontend, backend, integrate, deploy [, launch/acquire real users if the case requires it] | §13 [+14] |
  | Final days — Document | PRD, deck, demo | Whole PRD + presentation |

- **Contents**: numbered list of all sections used for this case (13 base sections + any added, e.g. a launch/growth section if the case demands real users; + appendices if the case defines any).

---

## 1. [The Given Problem / The Problem Space] — Case Summary

Rename based on whether the problem is actually given. Set the stage: state the problem precisely (in your own words if given; chosen and defended if open), and frame the [workflow/journey/system] you're about to dissect and build for.

**WHAT THIS SECTION COVERS**
- A 4–6 sentence summary of the case in plain language — the market/context, the shift driving it, and why this specific problem area is the battleground.
- The problem, restated (if given) or framed as a choice you're making (if open).
- The exact question you must answer — not "what is the problem" but "what should the FIRST version solve, and how will you know it worked once it's live/real?"
- What is explicitly out of scope.

**HOW TO BUILD IT**
- If the problem is given: state it crisply, move fast to the workflow and the build. If open: spend real discovery time before writing this section — don't summarize a hunch as case-given fact.
- Write the real question as a question, on its own line.
- Name the tension the case flags (e.g. abundant existing options yet the core outcome still isn't reached).

**EXAMPLE · THIS CASE** — `ILLUSTRATIVE — derive your own, do NOT copy shape from a prior case.` If the case supplies market stats or figures, cite them with a source; if not, flag that no data was supplied and defer sizing to §4.

**PRESSURE-TEST QUESTIONS**
- Can you state, in one sentence, what the FIRST version solves — without listing features?
- Have you separated the market opportunity (big) from the specific bottleneck you will fix (narrow)?
- Do you name what you will deliberately NOT build?

---

## 2. [Stakeholder Mapping / User & Influence Mapping]

Rename based on whether this is a multi-team B2B workflow (stakeholder mapping, approval chain) or an individual/B2C journey (user & influence mapping, no approval chain). List everyone who touches or influences the outcome, because the friction usually lives in the handoffs or the missing nudge, not inside any one party.

**WHAT THIS SECTION COVERS**
- Every party in the journey: [adapt — business teams/approvers for B2B; learner/manager/peers/community for B2C].
- For each: what they care about, what they fear, what they do today, how much power/influence they hold.
- Who is the primary USER, who is the BUYER, and who merely influences — decide explicitly, don't assume a B2B split or a B2C default out of habit.

**HOW TO BUILD IT**
- Use a table: Party | Cares most about | Where they help/block | Influence (H/M/L) | User/Buyer/Influencer.
- Separate buyer from primary user if they differ — state plainly if they're the same (self-serve).
- Flag the party or influence every existing solution ignores — that's a candidate wedge.

**SUGGESTED FORMAT** — reusable table shape, fill content from the case (see front-matter table pattern above).

**PRESSURE-TEST QUESTIONS**
- Who is the primary user, who is the buyer, and who are the influencers/approvers? Name each.
- Which gap does every existing approach fail to close — with evidence, not a guess?
- Have you listed anyone only because a prior case's table had that role, with no equivalent here? Cut or justify.

---

## 3. [The Onboarding Workflow / The Current Journey] — How It Works Today

The heart of discovery. Map the end-to-end journey and mark exactly where value/time/trust is lost.

**WHAT THIS SECTION COVERS**
- The complete journey as stages, from trigger to (rarely reached) ideal outcome.
- Layered on top: how work/information moves, and where time or motivation is spent/lost.
- The bottlenecks — where the journey waits, loops back, or drops off. This is what the MVP targets.

**HOW TO BUILD IT**
- Draw the journey as stages with an estimated cost (days, % drop-off, etc.) per stage.
- For each stage, mark the friction.
- Prefer a diagram or stepped table over prose.
- Separate symptoms from root causes.

**SUGGESTED FORMAT** — Stage | What happens/friction | Owner (if applicable) | Cost (days/%/etc., `?` if unknown — fill from primary research, don't invent).

**PRESSURE-TEST QUESTIONS**
- Can you point to the ONE stage that costs the most? That's your MVP target.
- Are your findings symptoms or root causes?
- Have you mapped what people actually do, or only the official/idealized process?

---

## 4. Secondary Research

What you can learn without leaving your desk — sized, sourced, interpreted. Keep it lean: it frames the [workflow/journey], it does not replace primary research or re-litigate the problem. Don't overdo TAM.

**WHAT THIS SECTION COVERS**
- Market size/growth and the trends driving investment or urgency in this space.
- What's already known about why the current approach persists despite existing options.
- Benchmarks you can borrow for later sizing.

**HOW TO BUILD IT**
- Every fact gets a citation and a "so what." If a number changes no decision, delete it.
- Group by theme, not by source.
- Keep it to ~1 page.

**EXAMPLE · THIS CASE** — `ILLUSTRATIVE structure only.` If the case supplies seed facts, cite and extend them; if not, flag it explicitly and source your own — never carry numbers over from a different case.

**PRESSURE-TEST QUESTIONS**
- For every statistic: does it actually say what you claim?
- Does your research explain WHY the problem persists, or just restate that it exists?
- Is this section earning its page, or padding?

---

## 5. Existing Tools/Solutions — and the [Job/Seam] They Miss

Show what each category of existing solution does, the specific players crowding or leaving open ground, and the one job none of them finishes. This section closes with a Key Insights subsection — required, not optional.

**WHAT THIS SECTION COVERS**
- The categories of tool/solution that already touch this space.
- What each does well, and where it stops.
- **Competitor Analysis (required subsection)**: named competitors/products, organised by job-to-be-done or mechanism (not just a feature list), showing where the market is crowded and where it's genuinely open.
- **Key Insights (required closing subsection)**: the synthesis of §4 + §5 into a small number of dated, evidence-tagged insights — see below.
- The unfinished job that survives all of them.

**HOW TO BUILD IT**
- Organise by job-to-be-done, not by brand.
- For Competitor Analysis: compare underlying mechanism, not surface features — "every player follows a staff-led, top-down model" is a stronger finding than a feature checklist.
- For each category, name the unfinished job in one line — it points at the MVP wedge.
- Resist rating by features; rate by whether the outcome actually gets closer end-to-end.
- For Key Insights: write each insight as evidence, then interpretation — first state what the research shows, then, on a visibly separate clause or line, state what the team believes it means. Don't let the interpretation get written as if it were the finding itself. This is the single most-repeated mentor critique across past cases — hold this section to it more than any other.

**EXAMPLE · THIS CASE** — `ILLUSTRATIVE — derive your own.`

**PRESSURE-TEST QUESTIONS**
- If so many solutions exist, why does the problem persist? Answer honestly — it's the crux of the case.
- Which job is every current solution failing to finish end-to-end?
- Are existing tools failing, or solving a different job than the one you care about?
- For Competitor Analysis: did you compare mechanism, or just list feature tables?
- For Key Insights: for each insight, can you point to which sentence is the evidence and which is the interpretation? If a reader can't tell them apart, rewrite it.

---

## 6. Primary Research — Right-Sized for [a Given / an Open] Problem

Diagnose this explicitly per case: if the problem is GIVEN, research is lighter and aimed at locating the bottleneck and validating the MVP (6–10 conversations is a reasonable target). If the problem is OPEN, research must be heavier and aimed at finding the real problem/segment before validating anything (12–20+ conversations across multiple candidate segments, in two passes: broad-then-narrow).

**HOW MUCH PRIMARY RESEARCH DOES THIS CASE NEED?**
- State which mode applies (given vs. open) and why.
- A workable target, sized to that mode.
- The interviewing discipline: ask about the LAST specific instance (not "usually"); keep talk-share ~20%; open why/what/how questions; never lead; distrust stated enthusiasm ("I'd use this") — ask what they've actually done.

**WHAT THIS SECTION COVERS**
- Who you spoke to, how many, how you reached them.
- What you asked, aimed at the mode you diagnosed above.
- What you heard/saw, with a SAW/THINK/ASSUME split, and what would change your MVP.
- **Research Gaps & Prioritized Open Questions (required closing subsection)**: what's still unvalidated after primary research, split into "must validate before moving ahead" vs. "good to explore later" — not a flat list.

**HOW TO BUILD IT**
- Table it: Segment/Function (n=) | Method | What we heard/saw | Saw/Think/Assume.
- Anchor every interview on a specific real instance.
- Ask a consistent closing question across interviews; the overlap in answers is your MVP signal.
- Decide in advance what finding would kill your favourite idea — then look for it.
- For Research Gaps: list every open question or unvalidated assumption, then explicitly rank them — name the single one that creates the highest risk to the product if wrong, and say why it outranks the others. A gap list with no ranking gets the same critique twice in past cases; don't repeat it a third time.

**SUGGESTED FORMAT** — table shape above, fill from the case. Research Gaps as two labeled groups (Must validate / Good to explore later), not one flat bullet list.

**PRESSURE-TEST QUESTIONS**
- Is your research aimed at the right thing for this case's mode (locating vs. finding)?
- Did every interview answer the same closing question, and do the answers converge?
- Does your confidence match your sample size? Label ASSUME honestly.
- Can you name the ONE open question that, if it broke the wrong way, would break the product's core hypothesis? Is it visibly flagged as higher-priority than the others?

---

## 7. Opportunity & Prioritisation

Turn findings into candidate opportunities, then pick ONE using a value-vs-effort lens. This is the commit point — after this, no major pivots.

**WHAT THIS SECTION COVERS**
- Candidate opportunities, each as For whom / Through what / Because why it exists today.
- Prioritisation on impact vs. effort, reasoning shown.
- The single opportunity carried forward, and why it beats the others.

**HOW TO BUILD IT**
- Write each opportunity as one line: "FOR [who + need] THROUGH [wedge] BECAUSE [why the gap persists today]."
- Before scoring anything, state in one sentence what Value and Effort each measure for this case (e.g. "Value = strength/frequency of the pain signal in research; Effort = build complexity within the sprint window") — a scale applied without this gets flagged in review even if every row has reasoning.
- Use value/effort with T-shirt sizing (S/M/L). Break ties toward smaller effort given the sprint window.
- The BECAUSE clause is the test — if you can't explain why the gap persists despite existing options, you haven't found the real opportunity.

**EXAMPLE** — `ILLUSTRATIVE — derive your own` value-vs-effort table (Candidate | Value | Effort | Carry forward?).

**PRESSURE-TEST QUESTIONS**
- Have you stated what Value and Effort each measure, before the table — not just per-row reasoning after the fact?
- Can you fill BECAUSE with evidence, or is it a guess dressed as a reason?
- Did you prioritise on value ÷ effort and break ties toward the smaller build?
- Who exactly is it FOR? A broad category is not a user — name the segment and the person.

---

## 8. Product Strategy — User, Buyer, Problem Statement

The lock point. Commit to user, buyer, persona, problem statement, and scope. No major pivots after this.

**WHAT THIS SECTION COVERS**
- Primary user and buyer, named separately — or explicitly stated as the same (self-serve), decided from evidence, not habit.
- One or two personas, written for a real person.
- The final problem statement: stakeholder + bottleneck + root cause + why it matters.
- The locked scope: what's frozen from here.

**HOW TO BUILD IT**
- Name user and buyer on their own lines.
- Persona: role, a moment where the problem bites, what "success" looks like to them, one outcome they want.
- Problem-statement template: "For [specific stakeholder], [the bottleneck] because [root cause], which matters because [consequence]."
- State the freeze explicitly: "Locked on [day] — problem, persona, scope."

**EXAMPLE** — `ILLUSTRATIVE shape only, no case-given anchor exists here unless the case supplied one; derive your own.`

**PRESSURE-TEST QUESTIONS**
- Have you named the primary user AND the buyer as different roles, or explicitly stated they're the same?
- Does the confidence in your problem statement match the size of your evidence?
- Is the scope locked and written down?
- Does the problem statement stick to who has the problem, what it is, and why it matters — with any defense of its own validity ("why nobody solved this," "why it's really a health/business problem") moved to §7 or §4–§6 instead of crowding the statement itself? Past cases have hit both failure modes — missing justification entirely, and overloading the problem statement with it — so check for either.

---

## 9. Solution Ideation & Direction

Don't jump to the first idea. Put multiple solution directions on the table, weigh trade-offs, pick one, then draw the end-to-end flow.

**WHAT THIS SECTION COVERS**
- At least two or three genuinely distinct solution directions.
- A trade-off evaluation leading to a clear choice.
- The chosen approach in one paragraph, with why it beats the alternatives for this user in this timeframe.
- The end-to-end user flow, today-vs-tomorrow.

**HOW TO BUILD IT**
- Force divergence first — different shapes, not variants of one idea.
- Evaluate on the same axes: user value, build effort, risk. Reuse the value÷effort discipline from §7.
- Commit to one and say why the others lost — name the specific failure mode of each rejected direction, not just "weaker." Model precedent: the Whetstone/AI-work-feedback case rejected "curriculum-first" and "prompt-library" directions by naming exactly what each still failed to fix even in its strongest form, before naming why the chosen direction closed that gap.
- Draw the flow as an ordered list or boxes-and-arrows. Every §10 feature must trace back to a step here.

**EXAMPLE** — `ILLUSTRATIVE — derive your own` directions/trade-off table and today-vs-tomorrow flow table.

**PRESSURE-TEST QUESTIONS**
- Did you genuinely diverge, or dress one idea in three costumes?
- Can you say — in one sentence each — why the rejected directions lost?
- Does every step of your flow map to a real user action and reach the outcome the persona actually wants?

---

## 10. Product Detailing & MVP Scope

Detail the chosen flow: every feature, edge cases, information architecture, and — critically — what makes the MVP versus what waits.

**WHAT THIS SECTION COVERS**
- Full feature list mapped to the §9 flow.
- Product-value classification: must-haves, performance benefits, delighters.
- **Feature-level flow & failure states (required, every feature in the catalogue)**: for each feature, not just the must-haves — Trigger → Steps → Success state → Failure/edge states → trust/safety note. A feature list without this reads as a capability inventory, not a spec — this was the single most-repeated critique in past cases (three separate comments on one solution section).
- Information architecture.
- The MVP cut: V1 (this sprint), V1.1/V1.2 (deferred), with explicit non-goals.

**HOW TO BUILD IT**
- List features as user-facing capabilities, not screens. Tie each to a §9 flow step.
- Sort with the product-value template. MVP = must-haves + one shippable delighter.
- Prioritise on value÷effort and versioning — V1 is the thinnest slice that delivers the core outcome.
- For each feature, write the block: **Trigger** (what starts it) → **Steps** (the user-visible sequence) → **Success state** (what "worked" looks like) → **Failure/edge states** ("When X, the product does Y" — cover at minimum: no data/empty state, invalid input, and a timing/concurrency edge if relevant) → **Trust/safety note** (privacy, moderation, or fairness implication, if any). Don't stop at "edge cases exist" — name them and state the product's behavior for each.
- Sketch the IA as a tree or screen map.

**EXAMPLE** — `ILLUSTRATIVE — derive your own` feature/MVP-cut table, plus one fully-worked Trigger→Steps→Success→Failure block to show the expected depth.

**PRESSURE-TEST QUESTIONS**
- Does every feature trace to a §9 flow step and a real user need?
- Is your V1 truly the thinnest slice — or did comfort features sneak in?
- For EVERY feature — not just the top three — can you state its trigger, its success state, and at least one named failure/edge state with the product's exact behavior?
- Can you name three things you are deliberately NOT building, and why?
- If a stranger read only this section, could they tell how the product behaves when something goes wrong — or only when everything goes right?

---

## 11. UX & Product Design

Design the EXPERIENCE, not just screens. Work the design iceberg in order and pressure-test against the six components of great UX.

**WHAT THIS SECTION COVERS**
- High-fidelity screens for the core V1 flow, designed for the named persona.
- The design worked through the iceberg in order: conceptual → information → interaction → visual.
- A self-assessment against the six UX components, with evidence for each.
- Reusable components/design-system pieces that keep the build consistent.

**HOW TO BUILD IT**
- Work the iceberg top-down; visual comes LAST — jumping to visual first is the classic mistake.
- Design for the persona by name.
- Build reusable components in the design tool that match what will actually be built.
- Score yourself honestly on each component below; each weak score is a fix, not an excuse.

**SUGGESTED FORMAT** — six-component self-check table:

| Component | How to judge it | Your evidence |
|---|---|---|
| Usability | % who complete the core task with no help | ___% |
| Efficiency | % who finish within the target time | ___% |
| Perceived effort | How cluttered/heavy it feels | low/med/high |
| Credibility | Social proof, trust cues, no broken states | ___ |
| Delight | One moment of unexpected value | ___ |
| Simplicity | Clicks/taps to reach the outcome | ___ |

**PRESSURE-TEST QUESTIONS**
- Did you work conceptual → information → interaction → visual in order, or start with colours?
- Can you point to a screen and say what your named persona sees, thinks, does?
- For each UX component, do you have evidence — or an opinion?
- Do your design components match what you'll actually build?

---

## 12. Analytics & Event Tracking

Analytics isn't a slide — it's wired into the product. Define the metrics stack, then design the actual events/properties/funnels, and say how tracking gets implemented before you build.

**WHAT THIS SECTION COVERS**
- The metrics stack: one North Star (value) metric, leading (predictive) metrics, lagging (confirming) metrics.
- The activation metric and the funnel that leads to it — use the FULL AARRR loop (acquisition → activation → retention → referral) if the case requires real user acquisition/growth; a B2B-internal case may reasonably de-emphasise acquisition/referral — diagnose which applies.
- An event-tracking sheet: events, properties, funnel step.
- How analytics is actually implemented — where events fire, where data lands.

**HOW TO BUILD IT**
- Pick ONE North Star that captures delivered value.
- Split leading (predict) vs. lagging (confirm) metrics — always a ratio with a denominator, never a raw count.
- Name the activation metric — the aha moment.
- Design events with FEW event names and RICH properties.
- Apply the "So What" / removal test — cut vanity metrics. Model precedent: the Whetstone/AI-work-feedback case's North Star ("Artifact Improvement Reach") paired a so-what test ("does this have a direct, defensible consequence for the product's actual thesis") with a removal test ("if you removed the ability for work to get better, does this number go to zero") — hold every North Star candidate to both, not just one.

**EXAMPLE** — `ILLUSTRATIVE — derive your own` metrics-stack table and event-tracking sheet.

**PRESSURE-TEST QUESTIONS**
- Is your North Star a single value metric — or a dashboard pretending to be one?
- For each metric, apply "So What" — would a different reading change a decision?
- Are your events few-with-rich-properties, or a new event name for every click?
- Can you point to WHERE each event fires and WHERE the data lands?

---

## 13. Build & Deployment

The week's payload: a real, working product. Document what you built, how, what you cut to ship, and the live evidence.

**WHAT THIS SECTION COVERS**
- The technical approach — frontend, backend (if built), data store, APIs — kept as simple as the demo/pilot allows.
- What shipped in V1 versus what was deferred, and the honest reason for each cut.
- How §12 events are integrated into the running product — not just planned.
- The live deployment: URL/link, plus screenshots.
- How you tested — core flow end-to-end, known bugs/limitations.

**HOW TO BUILD IT**
- State the stack in one line each. Choose boring, shippable tools.
- Be explicit about scope-at-ship: "Built: X. Faked/stubbed: Y. Cut: Z."
- Wire the §12 events for real; confirm they land somewhere readable.
- Put the live link at the top of this section with 2–4 screenshots.
- Describe testing plainly; list known limitations.

**EXAMPLE** — `ILLUSTRATIVE — derive your own` shipped-vs-deferred table.

**PRESSURE-TEST QUESTIONS**
- Is there a working link a reviewer can click right now — or only screens that look done?
- Can you say precisely what is real, stubbed, and cut?
- Do your analytics events actually fire in the deployed product, or only in the plan?
- Does the core flow survive a stranger using it unaided?

---

## [Optional additional section(s) — only if the case's deliverables have no home in §1–13]

Example precedent: a case requiring real user acquisition, a growth loop, and insight-driven iteration got a new "Launch, Growth Loop & Iteration" section, because §13 in this shell stops at "deployed and tested," not "acquired real users and iterated on their behaviour." Don't force unrelated deliverables into §13 just to avoid adding a section — flag the addition clearly instead, and note it's an addition to the base 13, not a renumbering of them.

**WHAT THIS SECTION COVERS** — adapt: acquisition strategy/channel, growth loop mechanic, full funnel results (real numbers from §12 events), insights from real behaviour vs. what was assumed, and the concrete change(s) made because of those insights.

**HOW TO BUILD IT** — state channels honestly (repeatable vs. one-time favour); report real numbers, not projections; contrast assumed vs. observed behaviour; name at least one concrete product change made mid-pilot.

**PRESSURE-TEST QUESTIONS** — adapt: did you reach users through a repeatable channel or a one-off favour; can you cite a real number, not a guess; what's the ONE thing real behaviour taught you that research didn't, and what did you change because of it.

---

## Appendices

Carry forward only if the case or mentor supplies content for them. In the original source template, "Appendix A — Ship-Ready Pressure-Test" and "Appendix B — The PM Prompt" were listed in the contents but had no body content — don't invent content for empty appendices; leave them as placeholders and say so.
