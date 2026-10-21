---
name: ux-text
description: Write or fix the functional text of an interface - labels, buttons, hints, error messages, empty states, confirmations - and hand it over as a replacement table developers can work down, with IDs, variables, a binding glossary and the behaviour changes the text depends on. Use when a screen has placeholder or developer-written text, when error messages say what went wrong but not what to do, when empty states say "No data", when the same thing has three names, or when a flow needs final text before build.
---

# UX Text

Category: **Flow**

|  |  |
|---|---|
| **Use when** | A screen still has placeholder or developer text · error messages say "invalid input" · empty states are blank or say "No data" · the same thing has three names across screens · a flow is ready and its text is not · a German interface reads like a translation |
| **Skip when** | The text is clear and the brand wants a distinct personality or marketing voice: a voice skill (separate, not in this collection). The problem is the order or number of steps, not their wording: `ux-flow` |
| **Needs** | The screens or the flow, with the states each view can be in, and who uses it how often |
| **Produces** | A text handover: assumptions, voice in three lines, binding glossary, replacement table per element and state, behaviour the text depends on, message patterns |
| **Then** | `ux-build-plan` when someone else builds it, otherwise build directly |

## Before you start

Look for the states each view can be in: empty, loading, error, success, partial, no permission, conflict. They usually come from `ux-flow`.

Found them: write text for every state, not just the happy one, and say in one line what you are building on.
Not found: derive them from the screen and its behaviour, and list the ones you assumed in the assumptions table, so the missing ones are visible.

Text written for the happy path only is the most common reason empty states and errors ship with "No data" and "An error occurred".

## Set the voice from the routine, not from a persona

Three lines at the top of the handover, and every string below has to keep them:

| Routine | Voice |
|---|---|
| Daily, expert | Short. Labels one to three words, messages one sentence. Domain terms the users already use stay, abbreviations they know stay (with a long form for screen readers). No explaining what they know |
| Occasional | Short, but say what the screen is for and what comes next, because the user forgot since last time |
| Rare, broad audience | Plain language, one thought per sentence, no jargon; explain terms where they appear |

Decide the address form (du, Sie, or impersonal) once and write it into the glossary. Personality, wit and marketing tone are not this skill's job.

## Rules that carry the quality

**Name things the way users name them.** Use the words from the brief, support requests and the people who do the work, not the data model. One term per concept across the product, written into the glossary. Do not rename what users already call something: a role, a team, a document type keeps its name unless the users themselves use another.

**Buttons name the action.** Verb plus object: "Send invitation", "Move to shortlist". Not "OK", "Submit", "Yes". A button inside a dialog repeats the dialog's verb.

**Labels stay visible.** A placeholder is not a label. Hints go under the label and say what format or what example, not what the field is.

**Front-load.** The word that decides whether to read on comes first. "Interview on 12 March cancelled", not "We would like to inform you that...".

**Say it once.** No heading that repeats the button, no hint that repeats the label, no "Saved successfully" after "Save".

**Errors say what to do.** At the field: "Enter a start date", "Enter a date after today", not "Invalid date". Keep what the user entered. Validate when the user is done, not per keystroke. Accept every unambiguous format instead of reporting it. No blame, no "Oops", no exclamation marks. For a form with several fields, add an error summary at the top that links to each field (GOV.UK [error summary](https://design-system.service.gov.uk/components/error-summary/)); a single inline control needs none.

**System errors say it is not the user's fault**, whether their work is safe, and the one thing to do now. One or two sentences for experts.

**Empty states answer three questions:** what normally appears here, why it is empty now, the one thing to do. "No data" answers none. For no results, name the active filters and offer to clear them.

**Confirmations name the object and the consequence.** Ask only before what cannot be undone; for the rest, confirm after with undo. If a question stays, the buttons repeat the verb ("Delete application" / "Keep application"), and the safe answer is the default.

GOV.UK's [writing for user interfaces](https://www.gov.uk/service-manual/design/writing-for-user-interfaces) and Material's [content design](https://m3.material.io/foundations/content-design/overview) agree on almost all of this. Where they differ, the more specific and more tested one wins, which for forms and errors is usually GOV.UK.

## German interfaces

- **Du or Sie, once, everywhere**, or impersonal where it reads naturally. Mixed address reads as two products.
- **Verbs, not nouns.** "Wenn Sie den Antrag stellen", not "Bei der Antragstellung".
- **Buttons in the infinitive**: "Einladung senden", not "Senden Sie die Einladung", not "Absenden".
- **Errors as instructions**: "Geben Sie ein Startdatum ein", not "Ungültige Eingabe".
- **Gender-fair without breaking the line**: where a new term is needed, prefer neutral forms (Bewerbende, Team) over gender characters in buttons and column headers. Existing role names the users use stay.
- **Plan for length**: German runs about a third longer than English. A label that only fits as an abbreviation needs a different layout.
- **Short sentences**, active voice, under about fifteen words. Plain language is standardised as ISO 24495-1.
- **No "Bitte" by reflex.**

## The handover

Developers replace texts by working down a table. Write it so they never have to interpret prose.

**1. Assumptions.** Table: assumption, why it matters, what changes if it is wrong. Includes the states you assumed.

**2. Voice.** Three lines from the routine table, plus the address form.

**3. Glossary (binding).** Use / do not use / note. Every term in the strings below follows it, including your own messages.

**4. Replacement table.** One row per element and state:

| ID | Element and state | Today | New | Why |
|---|---|---|---|---|
| T01 | Search field, label | (placeholder "Suchen...") | Suche | Placeholder disappears on input |

- Stable IDs (T for existing texts, N for new states the screen does not have yet).
- Final strings only, with variables in braces (`{nr}`, `{name}`), never example values. Define each variable once.
- One string per row. Alternatives only for at most three critical texts, in a separate short section, with a recommended one.
- The "Why" is one line. A change you cannot defend is a preference.

**5. Behaviour the text depends on.** Table: ID, problem today, what is needed, which text IDs depend on it. Text cannot fix a dialog in the wrong place or a field that clears itself; say so here, once, and keep it out of the replacement table.

**6. Message patterns.** The sentence shapes every message follows ("{name} auf die Shortlist gesetzt." / "{name} wurde nicht auf die Shortlist gesetzt. Versuchen Sie es noch einmal."), the button verb pattern, and two or three don'ts.

Leave out how the handover was produced: no skill names, no process steps, no explanation of rules that did not apply.

## What this skill does not do

It does not give the product a brand voice or personality. It does not restructure the flow when the real problem is a step that asks two things at once; that goes to `ux-flow`, and the behaviour table names it. It does not translate; it writes for one language at a time.

## Where it sits

`ux-flow` → **`ux-text`** → `ux-build-plan` → build → `ux-validate`
