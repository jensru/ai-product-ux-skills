# AGENTS.md

Conventions for this repo. Read before adding or changing a skill.

[← README](README.md)

---

## What this repo is

A collection of skills for product and UX work in existing software. Nothing else. No course material, no client material, no stock of patterns.

The unit is the **skill**: one job, one trigger, one folder.

```
skills/<name>/
  SKILL.md       what it is for, what it needs, what it produces, and how it is run
  references/    optional, for what a run looks up rather than needs
```

The five skills form one workflow and share a prefix: `ux-context` → `ux-flow` → screen → `ux-text` → `ux-pattern` → `ux-check`. The screen step is deliberately not a skill here; every setup builds screens differently, and a skill that names one tool would be wrong for the others.

## SKILL.md format

Frontmatter, then the classification block, then the skill itself.

```markdown
---
name: skill-name
description: What it does, then "Use when ..." with concrete situations.
---

# Title

Category: **Understand | Flow | Build | Check**

|  |  |
|---|---|
| **Use when** | concrete situations, separated by · |
| **Skip when** | the neighbouring skill that fits better, named |
| **Needs** | input artifacts, with the skill that produces them |
| **Produces** | the artifact |
| **Then** | what usually comes next |

[what the skill decides, the rules that carry the quality, and what to write down]

[link or table for references/, if the skill has any]
```

## references/ is optional

It holds what a run **looks up**, not what a run **needs**:

| Needed on | Where it goes |
|---|---|
| Every run | `SKILL.md` |
| Some runs | `references/`: checklists, catalogues, a worked example |
| No run | Out |

An agent reads the skill and acts, so a second file is usually a second read on text it needed anyway. A reference earns its place when it is long, looked up rather than read (the WCAG checklist), and would bury the procedure if inlined.

## Every skill checks its one precondition

A skill is invoked from wherever the work happens to be, so it cannot assume that the thing before it has run. `Needs` is documentation and nobody reads it at runtime. Name the one load-bearing input and check for it, in a short block right after the classification table:

```markdown
## Before you start

Look for <the artifact>. It usually comes from `<skill>`.

Found it: build on it and say in one line what you are building on.
Not found: say what is missing and offer to run `<skill>` first.
Told to go ahead anyway: do, but write the assumption visibly into the result.
```

Rules that keep this from turning into an interrogation:

- **One precondition, not three.** The one whose absence ruins the result, not everything that would be nice.
- **Answerable by looking, never by asking.** Search the repo, the project, the conversation. Only speak when something is genuinely missing.
- **Offer, never block.** A skill that refuses to work is worse than one that works on a stated assumption.

This exists because it was learned the expensive way: a skill was run eight times without the input its own `Needs` row named, and the results were measured, analysed and written up before anyone noticed the input was missing.

## Rules that keep the collection usable

1. **The description carries the trigger.** An agent picks a skill by its `description` alone, so it names situations, not topics. "Use when error messages say what went wrong but not what to do" beats "covers UX writing".
2. **No two skills compete for the same trigger.** If two descriptions would both match, either merge them or make **Skip when** point at the other by name.
3. **Skip when is not optional.** Naming the neighbouring skill is what keeps the collection navigable. A neighbour that is not part of this collection is named anyway, marked "separate, not in this collection", so the reader knows the job exists and this skill does not do it.
4. **Needs and Produces are artifacts**, not moods. They are what lets skills be chained.
5. **No narrative.** No "you will learn", no step numbering that only makes sense in a sequence. A skill is used on its own, in whatever order the work demands.

## Sources are linked, not copied

The skills build on the GOV.UK Design System, the GOV.UK Service Manual, Material Design and the WAI-ARIA Authoring Practices. Describe what is taken and link it. Do not paste their text: the copy ages, the source moves on, and the licence of the source is not ours to relicense. Where a skill departs from a source, it says how and why.

Reference files that summarise a standard (WCAG, ISO 9241-110, Nielsen) are short paraphrases written for working, marked as such, with the source named. Every external link is checked before it is committed.

Accessibility target is **WCAG 2.1 level AA**. Levels are stated correctly (2.5.5 Target Size is AAA; 2.5.8 is AA and only in 2.2). WCAG 2.2 additions go in a separate, clearly marked block.

## This repo is public

- No client names, product names or project details. Examples are generic; the recurring one is recruiting (an applicant list, a shortlist), chosen because everyone understands it.
- No personal data, no local paths, no internal tool names.
- Nothing that was taken from a third party without its licence allowing it and a note saying so.

## Naming

- Folders: lowercase, hyphenated, prefixed with the group (`ux-`), named after the job (`ux-text`, not `writing`)
- Files in `references/`: named after what they hold (`wcag-21-aa.md`)
- English throughout. Language-specific rules (the German section in `ux-text`) live inside the skill that applies them

## Cross-references

Skills reference each other **by name** in prose (`see \`ux-flow\``), not by relative path. Paths break on every restructure, names do not. Relative links are only for files inside the same skill folder.

This is a portability rule. A skill folder gets copied into someone's `.claude/skills/` on its own, so a relative link that leaves the folder is a link that breaks on arrival.

## What does not become a skill

A skill is a procedure with a trigger: someone wants something, the agent works, an artifact exists afterwards. Text that is pasted or looked up is not a skill, however useful it is.

| Kind | Where it goes |
|------|---------------|
| Checklist, catalogue, worked example | `references/` inside the skill that uses it |
| A pattern for a specific product | that product's own library, written with `ux-pattern` |
| A stock of generic patterns | nowhere. Patterns come from gaps found in real work |

The test: if the answer to "what does the agent do here" is "it hands you the text", it is not a skill.

## Content quality

1. **Technically precise.** No exaggerations, no invented capabilities, no misquoted standard levels.
2. **Self-contained.** Each skill is understandable without the others. Dependencies are named in **Needs**, not assumed.
3. **Consistent vocabulary.** Context brief, routine (rare, occasional, daily), one thing per step, state catalogue, dead end, pattern status "to test" or "decided", finding (criterion, location, what happens, severity, fix) mean the same thing everywhere.
4. **Markdown is master.** Everything else is derived from it.
5. **A change needs a run.** A skill changes because a run showed a gap, not because a rule sounded nicer. Say in the commit which run.

---

[← README](README.md)
