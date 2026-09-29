---
name: ux-check
description: Review a screen, flow or pattern library in fixed passes - accessibility against WCAG 2.1 level AA, then usability against ISO 9241-110 or Nielsen's heuristics, optionally a visual critique - and return one ranked list of findings, each with criterion, location, severity and fix. Use before a handoff or release, when a client or team asks "is this accessible and usable", when an accessibility statement or tender needs evidence, or when a design has to be judged against the brief it was built for.
---

# UX Check

Category: **Check**

|  |  |
|---|---|
| **Use when** | A screen or flow is about to be handed off or released · someone asks whether it is accessible and usable · an accessibility statement or a public tender needs evidence · a pattern library needs auditing at the source · a design has to be judged against its brief |
| **Skip when** | A single specialised criteria set is wanted, such as Amershi's human-AI guidelines, psychological principles or a KPI choice: a review skill built for that set (`ux-heuristic-review`, separate, not in this collection). Only craft and polish of a rendered screen: a visual critic (`design-critic`, separate). Nothing exists yet to check |
| **Needs** | Something concrete: a running build, screens with their states, or a library with tokens and components. Ideally the context brief (`ux-context`) |
| **Produces** | One report: scope, passes run, findings ranked by severity, observations marked as opinion, and findings that should become patterns |
| **Then** | Fixes go back to `ux-flow`, `ux-text` or the screen step. Recurring findings go to `ux-pattern` |

## Before you start

Look for the context brief: task, user group, success criterion. It usually comes from `ux-context`.

Found it: check against it and say in one line what you are checking against.
Not found: say so and offer to run `ux-context` first. Without it the usability pass can only ask "is this usable", not "is this usable for this task".
Told to go ahead anyway: do, but write the assumed task and user group at the top of the report. The accessibility pass does not depend on the brief and runs either way.

## Scope first

Name what is under review (one flow, one screen with all its states, one component set) and what is not. "The app" produces a list nobody acts on.

For a pattern library, check the source, not the screens. A finding in a shared component fixes every screen that uses it, and a missing state in the library (no focus style at all, no error variant) is a stronger finding than a wrong one, because it shows nobody could build it correctly even if they wanted to.

## The passes

Run them in this order, one at a time. Mixing criteria sets in one pass produces overlapping findings and an argument about which one counts.

### Pass 1: Accessibility, WCAG 2.1 level AA

The target is **WCAG 2.1 AA**: all level A and AA success criteria, 50 in total. It is the level the European standard EN 301 549 builds on, and so the level most public tenders and accessibility laws in Europe point to. The checklist with every A and AA criterion is in [references/wcag-21-aa.md](references/wcag-21-aa.md).

Get the levels right, because reviews and tools get them wrong:

- **2.5.5 Target Size (44 by 44 CSS pixels) is level AAA** in WCAG 2.1, not AA. It is not part of an AA audit. WCAG 2.2 added **2.5.8 Target Size (Minimum), 24 by 24 CSS pixels, at level AA**. Platform guidance (Material's 48 by 48 dp) is a design recommendation, not a WCAG criterion. Report each under its own name.
- **1.4.11 Non-text Contrast** (3:1 for controls, focus indicators, states and meaningful graphics) and **4.1.3 Status Messages** are AA and new in 2.1. Both are missed often.
- **3.1.5 Reading Level** is AAA. Plain language still matters; report it in the usability pass, not as a WCAG failure.

Run the pass in three steps:

1. **Automated check first**, with axe-core (browser extension, `npx @axe-core/cli <url>`, or Lighthouse). It is cheap and reliable for what it covers, which is roughly a third of the problems: missing names and labels, contrast values, broken structure, missing language.
2. **Keyboard only**, through the one task from the brief, start to finish. Tab order, visible focus everywhere, no traps, every action reachable, focus moved sensibly after dialogs, errors and page changes. This half hour finds more than anything else in the audit.
3. **Meaning**, which no tool checks: is colour ever the only carrier of information, do the error messages say what to do, do headings reflect the structure, are status changes announced, do labels match the visible text.

Measure contrast from token pairs, not from screenshots: text on surface, border on background, icon on button, for the combinations that actually occur. Name the tool and date with every measured value.

If the project targets **WCAG 2.2 AA**, add its new A and AA criteria as a separate block (listed in the reference) so the report shows which findings exist only under 2.2.

### Pass 2: Usability, one heuristic set

Pick one set per pass, by the question being asked. Both are summarised in [references/heuristics.md](references/heuristics.md).

| Question | Set |
|---|---|
| Does it hold up against the international standard, for a client or a tender | ISO 9241-110:2020, seven interaction principles |
| Is it usable at all, quick and widely understood | Nielsen's ten usability heuristics |

Walk the criteria one at a time against the real artifact. Not from memory, not from the description of the design. If the build runs, click it. Check each view in every state from the catalogue in `ux-flow`, not just the populated one.

Then check the result against the brief: can the user group do the task, at their routine's pace, and would the success criterion be met? A screen that passes every heuristic and fails the task has failed.

### Pass 3, optional: Visual critique

Only when craft matters for the decision and only after passes 1 and 2. Run it with a critic in a fresh context that sees only the screenshot, never the code or the builder's reasoning (a visual-critic skill such as `design-critic`, separate, not in this collection, does exactly this). Its findings go in a separate section; they are judgement against a direction, not violations of a standard.

## Findings

Each finding has five fields:

| Field | Rule |
|---|---|
| Criterion | WCAG number and level, or the named heuristic. No criterion, no finding |
| Location | View, state and element. "Applicant list, no-results state, the Clear filters link". A finding without a location cannot be fixed or verified |
| What happens | The failure in user terms, observed, not suspected |
| Severity | **Blocker**: the task cannot be completed, or cannot be completed without a mouse, a screen or sight. **Major**: significant effort, errors or lost trust. **Minor**: friction, no loss |
| Fix | One line, concrete enough to act on |

Rules that keep the report usable:

- **Rank by severity**, not by criterion number.
- **Cap the list.** The fifteen most severe findings in full, the rest counted by criterion. A report of eighty equal findings gets none of them fixed.
- **Group repeats.** The same failure on twelve screens is one finding with twelve locations, and a candidate for `ux-pattern`.
- **Separate opinion.** Anything that cannot be tied to a criterion goes into a short "Observations" section, marked as opinion.

## The report

1. Scope, target (WCAG 2.1 AA or 2.2 AA, which heuristic set), date, what was tested how (tool, keyboard, screen reader and browser)
2. Summary in three sentences: can the user group do the task, what blocks it, what the largest lever is
3. Findings, ranked
4. Findings that should become patterns, each with one line on the rule it would set
5. Observations, marked as opinion
6. Optional: visual critique

A finding fixed on one screen is a ticket. A finding turned into a rule is fixed for every screen built afterwards. Section 4 is often the most valuable part of the report.

## What this skill does not do

It does not certify legal conformance; a WCAG review supports an accessibility statement, it is not one. It does not replace testing with disabled users or assistive technology users. It does not redesign; it names the fix, and the design work goes back to the skills that own it.

## Where it sits

`ux-context` → `ux-flow` → screen → `ux-text` → `ux-pattern` → **`ux-check`**

## References

| File | Holds |
|---|---|
| [references/wcag-21-aa.md](references/wcag-21-aa.md) | All WCAG 2.1 level A and AA criteria as a checklist, the AAA criteria people mistake for AA, the WCAG 2.2 additions, links |
| [references/heuristics.md](references/heuristics.md) | ISO 9241-110:2020 and Nielsen's ten heuristics, one line each, with the question to ask |
