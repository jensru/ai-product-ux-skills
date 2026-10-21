# Evals

How the skills were tested, what the runs showed, and what still goes wrong. A skill changes because a run showed a gap; this file is where the runs are recorded.

[← README](../README.md)

---

## Method

- **Two invented cases** from different domains, chosen to differ in routine:
  - **Dispatch:** a work list in building-services software, used all morning by four expert dispatchers (daily, dense, two people on the same data, a legal qualification rule, a spreadsheet kept next to the tool).
  - **Expense claim:** a travel expense form in an HR self-service portal, used occasionally by a mixed workforce, mostly on the phone, some in a second language, some with a screen reader.
- The dispatch case was used to sharpen the skills. The expense case was written before the changes and not looked at while changing them; it is the holdout.
- Each case has a deliberately flawed screen with a list of planted problems (24 and 29 items), used as the answer key for text and review tasks.
- Every run is a fresh agent with only the input files and, depending on the condition, one skill. No human answers questions during the run.
- Results are anonymised and judged **blind** by a separate agent per case, on five criteria scored 1 to 5 (25 maximum), with length explicitly not counted as merit.

## ux-flow

| Round | Case | Without skill | Previous skill | Current skill |
|---|---|---|---|---|
| 1 | Dispatch | 20 | 22 (first version) | |
| 2 | Dispatch | | 17 (first version) | **22** |
| 2 | Expense claim (holdout) | | 19 (first version) | **21** |

**What works**

- A real state catalogue per view (empty first use, no results, loading, partial, errors, no permission, success). Without the skill, loading, no-permission and initial load errors were missing.
- Decisions instead of requirements: a keyboard model with actual keys, a conditional write against double assignment, undo timings in seconds, where each column of the spreadsheet workaround lives inside the flow. Judges said developers "could start" with the current version and would "hold a session" to decide the same points with the first one.
- The routine logic holds across both cases: dense board, bulk actions and undo for the daily tool; one question per step, inferred master data and a check page for the occasional form.

**What still goes wrong**

- On the holdout, one run grounded parts of its argument in an existing form that was not in the brief. Assumptions about the current system need marking like any other assumption.
- Results are long (180 to 300 lines). Judges did not penalise this where the lines carried decisions, but a shorter handover would be easier to review.

## ux-text

| Round | Case | Without skill | Previous skill | Older private skill with handover format | Current skill |
|---|---|---|---|---|---|
| 1 | Dispatch | 21 | 16 | 22 | |
| 2 | Dispatch | | 15 | 19 | **23** |
| 2 | Expense claim (holdout) | | 17 | 18 | **22** |

The first version of `ux-text` scored below running without a skill. The current version combines its GOV.UK rules with the handover format of an older private skill and replaces it.

**What works**

- A handover developers can work down without asking: stable IDs per element and state, final strings with defined variables instead of example values, a binding glossary the strings actually follow, and a behaviour table that links each needed change to the text IDs that depend on it.
- Full state coverage, including states the screen does not show yet (load error, conflict between two users, delete, failed actions with retry).
- Text and flow kept apart: an inverted confirmation (asking before a reversible action, not before an irreversible one) was recognised as a flow problem and solved there, not reworded.
- Voice from the routine: short strings for experts, plain language for an occasional and mixed audience.

**What went wrong before, and is fixed**

- The first version renamed terms users already use ("Techniker" to "Zuständig") in the name of inclusive language. The rule now keeps existing role and domain names.
- It wrote strings with example data, spread over prose sections, and explained GOV.UK rules that did not apply.

**What still goes wrong**

- System error texts sometimes state a cause or a reassurance the product cannot know ("the connection was interrupted", "your data is not affected").
- Occasional over-explaining for experts in empty states.

## What was not kept

Three more skills were written and tested in the first round and taken out of this collection: a context brief skill (barely better than no skill; its task lines now open `ux-flow`), a pattern skill (level with no skill), and a combined accessibility and usability review (strong on correct WCAG levels, but splitting it into two reports made the result worse, so it needs more work before it is published).

## Limits

One run per condition and one judge per case. The same text by the first `ux-flow` scored 22 with one judge and 17 with another, so differences of three to five points can be noise. Only results that point the same way on both cases are treated as findings here. Neither skill has been run on a real product yet.

---

[← README](../README.md)
