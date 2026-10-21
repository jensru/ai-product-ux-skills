# AI Product UX Skills

**Skills for product and UX work in software that already exists.** Four skills in three roles: a concept that describes the experience, a build plan that translates it into technology, and a check that the build delivers the concept.

Each skill is a folder with a `SKILL.md` that says what it is for, what it needs, what it produces, and how it is run. An agent such as Claude Code picks the skill by its description and does the work; the person decides.

by Jens Rusitschka, [kick & boost](https://kickboost.io/)

---

## How the skills work together

```
Concept                      Build                     Check
ux-flow  →  ux-text   →   ux-build-plan  →  build  →   ux-validate
```

| Role | Skill | Does | Does not |
|---|---|---|---|
| **Concept** | [ux-flow](skills/ux-flow/) | Describes the experience: the user's goal and the moment it pays off, every step with before, during and after, how each step is acknowledged. Knows what technology makes possible and proposes modern interactions (image upload, AI suggestions, chat) where they shorten the way to the goal | Carries technical detail: no data model, no services, no build briefing |
| **Concept** | [ux-text](skills/ux-text/) | Writes the words for every step and state, as a handover developers can work down: IDs, variables, a binding glossary | Gives the product a brand voice |
| **Build** | [ux-build-plan](skills/ux-build-plan/) | Translates the concept into a build plan: technical steps, data, components, services. Adds only what the code needs and marks it. Sends back what cannot be built as described | Changes the experience |
| **Check** | [ux-validate](skills/ux-validate/) | Compares the plan or the build with the concept, step by step, and lists what is missing, added or changed | Judges taste or redesigns |

**Why three roles.** A concept that also tries to be a build briefing fills up with technical detail and loses the experience. A build with no concept to go back to fills the gaps with whatever is usual. The split keeps the concept clean, makes the translation a job of its own, and makes that job checkable.

**Keep the roles apart.** Build plan and validation work only when they are done by someone who did not write what they work on: another person, or a fresh agent that gets only the concept, the text handover and the brief. In Claude Code that means a separate subagent for the build plan and another one for validation. An agent that validates its own build finds what it meant, not what it made.

**When to skip build plan and validation.** They cost time. Skip them when the change is small and whoever builds it can go straight from the concept, when the person who wrote the concept also builds it, or for an early prototype meant to be thrown away. Use them when the concept goes to someone else, when it proposes an interaction nobody has built here before, or before a release.

## Which skill do I need?

| Situation | Skill |
|---|---|
| A task, form or feature needs its steps designed before screens are built | [ux-flow](skills/ux-flow/) |
| Users drop out and nobody can say where | [ux-flow](skills/ux-flow/) |
| The flow is a stack of form windows, or every action answers with a toast | [ux-flow](skills/ux-flow/) |
| Errors say "invalid input", empty states say "No data" | [ux-text](skills/ux-text/) |
| A German interface reads like a translation | [ux-text](skills/ux-text/) |
| A concept is ready and developers or a coding agent have to build it | [ux-build-plan](skills/ux-build-plan/) |
| Nobody can say whether what was built is what was designed | [ux-validate](skills/ux-validate/) |

## What the concept is built on

- **Every flow is an onboarding.** Lead the user to their goal as fast as possible; every step is actionable, has a visible effect, says why it matters now and teaches how the product works.
- **Before, during, after**, following Krystal Higgins, [Better Onboarding](https://abookapart.com/products/better-onboarding): what the user needs ready, the help to get the step right, and what changed afterwards.
- **Acknowledge, don't announce**, following Material's [confirmation and acknowledgement](https://m2.material.io/design/communication/confirmation-acknowledgement.html): the lightest acknowledgement that makes the change clear, undo instead of "are you sure".
- **[GOV.UK](https://www.gov.uk/service-manual/design/form-structure)** for steps that make sense on their own: ask only what is needed, mandatory and optional clear, documents named up front.
- **[Nielsen's heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) or ISO 9241-110** as the check while designing, not afterwards.
- **Never a menu of interaction patterns.** Answers picked from a list produce the average; the answer comes out of this product's situation.

## Install

**Claude Code.** Copy a skill folder into `.claude/skills/` in your project, or into `~/.claude/skills/` to have it everywhere. Claude Code picks the skill up by its `description`.

```bash
git clone https://github.com/jensru/ai-product-ux-skills.git
cp -R ai-product-ux-skills/skills/ux-* ~/.claude/skills/
```

Or symlink the folders, so a `git pull` updates them:

```bash
for s in ai-product-ux-skills/skills/ux-*; do ln -s "$PWD/$s" ~/.claude/skills/; done
```

**Other agents.** Point the agent at the `SKILL.md`. It is plain Markdown and works pasted into any chat model. Each skill is self-contained, and skills refer to each other by name, never by path.

## Structure

```
README.md             This file
AGENTS.md             Conventions for writing and changing skills
LICENSE               CC BY 4.0
evals/README.md       How the skills were tested, what the runs showed, what is still open
skills/
  ux-flow/SKILL.md
  ux-text/SKILL.md
  ux-build-plan/SKILL.md
  ux-validate/SKILL.md
```

## Status

October 2026. Tested blind on two invented cases (a dispatch tool used all day by experts, an expense form used occasionally on the phone), and once end to end: concept, text, build plan, clickable prototype and validation, compared with a prototype built from the previous version and one built without any skill. The full chain was rated best. One run per condition, no real product yet, and several questions are still open: see [evals](evals/README.md), section "Further testing needed".

Contributions: open an issue with the situation the skill got wrong. A skill changes because a run showed a gap, not because a rule sounded nicer.

## About

**Jens Rusitschka** is an interaction designer with over 20 years in product work and several years focused on prompt engineering, AI prototyping and agentic workflows.

[Website](https://kickboost.io/) | [LinkedIn](https://www.linkedin.com/in/jensru)

---

*AI Product UX Skills | Jens Rusitschka, kick & boost | 2026 | Licensed under [CC BY 4.0](LICENSE)*
