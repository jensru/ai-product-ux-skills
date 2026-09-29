---
name: ux-text
description: Write or fix the functional text of an interface - labels, buttons, hints, error messages with an error summary, empty states, confirmations - so it says what happens and what to do, in the product's language (with rules for German interfaces). Use when a screen has placeholder or developer-written text, when error messages say what went wrong but not what to do, when empty states are blank or say "No data", or when labels and buttons use different words for the same thing.
---

# UX Text

Category: **Flow**

|  |  |
|---|---|
| **Use when** | A screen still has placeholder or developer text · error messages say "invalid input" · empty states are blank or say "No data" · the same thing has three names across screens · a German interface reads like a translation |
| **Skip when** | The text is clear and the problem is voice, tone or personality: a voice skill such as `microcopy` (separate, not in this collection). The problem is the order or number of steps, not their wording: `ux-flow` |
| **Needs** | The flow with its states (`ux-flow`), or the screens with every state visible |
| **Produces** | Text per element and state, a short glossary of the terms used, and for each changed text one line of reasoning |
| **Then** | `ux-pattern` if a text rule keeps coming up, `ux-check` |

## Before you start

Look for the states each view can be in: empty, loading, error, success, partial, no permission. They usually come from `ux-flow`.

Found them: write text for every state, not just the happy one, and say in one line what you are building on.
Not found: say which states are missing and offer to run `ux-flow` first.
Told to go ahead anyway: do, but list the states you assumed at the top, so the missing ones are visible.

Text written for the happy path only is the most common reason empty states and errors ship with "No data" and "An error occurred".

## What interface text is for

Interface text has one job: the user knows what will happen and what to do next, without reading anything twice. GOV.UK's guidance on [writing for user interfaces](https://www.gov.uk/service-manual/design/writing-for-user-interfaces) and Material's [content design](https://m3.material.io/foundations/content-design/overview) guidance agree on almost everything below. Where they differ, the more specific and more tested one wins, which for forms and errors is usually GOV.UK.

## Rules that carry the quality

**Name the thing the way users name it.** Use the words from the context brief and from support requests, not the data model. One term per concept across the whole product, written into the glossary. If the list says "Candidate", the detail page does not say "Applicant".

**Buttons name the action.** Verb plus object: "Send invitation", "Move to shortlist". Not "OK", "Submit", "Yes". A button inside a dialog repeats the dialog's verb, so the user can answer without reading the question again.

**Labels stay visible.** A placeholder is not a label; it disappears the moment the user types. Hints go under the label, above the field, and say what format or what example, not what the field is.

**Front-load.** The word that decides whether to read on comes first. "Interview on 12 March cancelled", not "We would like to inform you that the interview...".

**Say it once.** No heading that repeats the button, no hint that repeats the label, no success message that repeats the action ("Saved successfully" after "Save").

## Error messages

The logic follows the GOV.UK [error message](https://design-system.service.gov.uk/components/error-message/) and [error summary](https://design-system.service.gov.uk/components/error-summary/) components and the [recover from validation errors](https://design-system.service.gov.uk/patterns/validation/) pattern. Read those pages before writing errors for a form.

1. **At the field, say what to do.** "Enter a start date", "Enter a date after today". Not "Invalid date", not "Error". The message is specific to what went wrong in this field.
2. **At the top of the form, list every error** in a summary, each one a link to its field, with the same wording as at the field. Move focus to the summary and put "Error: " in front of the page title, so keyboard and screen reader users learn about it first.
3. **Keep what the user entered.** An error that clears the field makes the user do the work twice.
4. **Validate when the user is done**, on submit, never while they are still typing. GOV.UK validates on submit only. Material shows field errors once the user has interacted with the field; if you do that, still not keystroke by keystroke.
5. **Prevent before you report.** Accept a value in every unambiguous format (with or without spaces, with or without the leading zero) and ignore stray characters from copy and paste. Every error message you avoid this way is one the user never reads.
6. **No blame, no drama.** No "you failed to", no exclamation marks, no "Oops". The same neutral tone for a missing field and a server outage.

System errors, where the user did nothing wrong, say so: what happened, whether their work is safe, what they can do now (retry, come back later, contact someone).

## Empty states

Every empty state answers three questions: what normally appears here, why it is empty now, and the one thing to do about it. Material's [empty states](https://m2.material.io/design/communication/empty-states.html) guidance is the reference.

| Cause | Text does |
|---|---|
| First use | Says what will appear, offers the action that creates the first item |
| No results | Names the active search or filters, offers to clear them |
| Everything done | Says so plainly. An empty inbox is a success, not a problem |
| No permission | Says the content exists and who can grant access |

"No data" answers none of the three.

## German interfaces

German text fails in its own ways. When the product language is German:

- **Du or Sie, once, everywhere.** Decide per product and write it into the glossary. Mixed address in one product reads as two products.
- **Verbs, not nouns.** "Wenn Sie den Antrag stellen", not "Bei der Antragstellung". Nominal style is the fastest way to sound like an authority letter.
- **Buttons in the infinitive**: "Einladung senden", "Auf die Shortlist setzen". Not "Senden Sie die Einladung", not "Absenden".
- **Error messages as instructions**: "Geben Sie ein Startdatum ein". Not "Ungültige Eingabe", not "Das Feld Startdatum ist ein Pflichtfeld".
- **Inclusive without breaking the line.** Prefer neutral forms (Bewerbende, Mitarbeitende, Team) over gender characters in short UI text, where a colon or asterisk in a button or column header hurts scanning and screen reader output. Decide once, write it into the glossary.
- **Plan for length.** German runs roughly a third longer than English. A label that only fits when shortened to an abbreviation needs a different layout, not an abbreviation.
- **Short sentences.** One thought per sentence, under about fifteen words, active voice. For software used by a broad workforce, including people working in their second language, this is the largest single lever on support load. Plain language is standardised as ISO 24495-1.
- **No "Bitte" by reflex.** "Bitte geben Sie Ihre E-Mail-Adresse ein" is a longer "E-Mail-Adresse". Politeness belongs where the user is asked for a favour, not in every label.

## What to write down

Per view and state, the final text next to the element. The glossary of terms and the address form. For every text that replaced an existing one, one line on why. A change you cannot defend is a preference, not an improvement.

## What this skill does not do

It does not give the product a voice or personality; that is a separate job (`microcopy`, not in this collection). It does not restructure the flow when the real problem is that a step asks two things at once; that goes back to `ux-flow`. It does not translate; it writes for one language at a time.

## Where it sits

`ux-context` → `ux-flow` → screen → **`ux-text`** → `ux-pattern` → `ux-check`
