# WCAG 2.1 level AA checklist

All 50 success criteria of WCAG 2.1 at level A and AA, in one line each, written as the question to check. The wording is a short paraphrase for working, not the normative text. Before reporting a finding, read the criterion in the [Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/) and its [Understanding](https://www.w3.org/WAI/WCAG21/Understanding/) page.

**2.1** marks criteria new in WCAG 2.1 compared to 2.0.

## 1 Perceivable

| # | Criterion | Level | Check |
|---|---|---|---|
| 1.1.1 | Non-text Content | A | Every meaningful image, icon and control has a text alternative; decoration is hidden from assistive technology |
| 1.2.1 | Audio-only and Video-only (Prerecorded) | A | Prerecorded audio has a transcript, silent video a text or audio alternative |
| 1.2.2 | Captions (Prerecorded) | A | Prerecorded video with sound has captions |
| 1.2.3 | Audio Description or Media Alternative (Prerecorded) | A | Visual information in video is described or offered as text |
| 1.2.4 | Captions (Live) | AA | Live video with sound has captions |
| 1.2.5 | Audio Description (Prerecorded) | AA | Prerecorded video has audio description where visuals carry meaning |
| 1.3.1 | Info and Relationships | A | Headings, lists, tables, labels and groups are marked up as such, not only styled |
| 1.3.2 | Meaningful Sequence | A | Reading order in the code matches the meaning |
| 1.3.3 | Sensory Characteristics | A | Instructions do not rely only on shape, position, colour or sound ("the round button on the right") |
| 1.3.4 | Orientation (2.1) | AA | Works in portrait and landscape unless one is essential |
| 1.3.5 | Identify Input Purpose (2.1) | AA | Fields asking for the user's own data carry the right `autocomplete` value |
| 1.4.1 | Use of Color | A | Colour is never the only way information is conveyed (status, required, error, links in text) |
| 1.4.2 | Audio Control | A | Audio playing longer than 3 seconds can be paused or muted |
| 1.4.3 | Contrast (Minimum) | AA | Text 4.5:1, large text (24px, or 18.66px bold) 3:1 |
| 1.4.4 | Resize Text | AA | Text zoomed to 200 % without loss of content or function |
| 1.4.5 | Images of Text | AA | Real text instead of text in images, except logos |
| 1.4.10 | Reflow (2.1) | AA | At 320 CSS pixels width, no horizontal scrolling for text content (data tables and similar are exempt) |
| 1.4.11 | Non-text Contrast (2.1) | AA | Controls, their states, focus indicators and meaningful graphics 3:1 against adjacent colours |
| 1.4.12 | Text Spacing (2.1) | AA | Nothing breaks when line height, paragraph, letter and word spacing are increased |
| 1.4.13 | Content on Hover or Focus (2.1) | AA | Tooltips and popovers can be dismissed, hovered and stay until dismissed |

## 2 Operable

| # | Criterion | Level | Check |
|---|---|---|---|
| 2.1.1 | Keyboard | A | Everything works with the keyboard alone |
| 2.1.2 | No Keyboard Trap | A | Focus can always leave any component by keyboard |
| 2.1.4 | Character Key Shortcuts (2.1) | A | Single-key shortcuts can be turned off, remapped, or only work on focus |
| 2.2.1 | Timing Adjustable | A | Time limits can be turned off, adjusted or extended |
| 2.2.2 | Pause, Stop, Hide | A | Moving, blinking or auto-updating content can be paused |
| 2.3.1 | Three Flashes or Below Threshold | A | Nothing flashes more than three times per second |
| 2.4.1 | Bypass Blocks | A | A way to skip repeated blocks (skip link, landmarks, headings) |
| 2.4.2 | Page Titled | A | Each page or view has a descriptive title |
| 2.4.3 | Focus Order | A | Focus moves in an order that preserves meaning |
| 2.4.4 | Link Purpose (In Context) | A | Link text, with its context, says where it goes |
| 2.4.5 | Multiple Ways | AA | More than one way to find a page (navigation, search, sitemap), except steps in a process |
| 2.4.6 | Headings and Labels | AA | Headings and labels describe their topic or purpose |
| 2.4.7 | Focus Visible | AA | Keyboard focus is always visible |
| 2.5.1 | Pointer Gestures (2.1) | A | Multipoint and path-based gestures have a single-pointer alternative |
| 2.5.2 | Pointer Cancellation (2.1) | A | Actions fire on release, not on press, or can be aborted or undone |
| 2.5.3 | Label in Name (2.1) | A | The accessible name contains the visible label text |
| 2.5.4 | Motion Actuation (2.1) | A | Shake or tilt actions have a control alternative and can be disabled |

## 3 Understandable

| # | Criterion | Level | Check |
|---|---|---|---|
| 3.1.1 | Language of Page | A | The page language is set |
| 3.1.2 | Language of Parts | AA | Passages in another language are marked |
| 3.2.1 | On Focus | A | Focus alone never triggers a change of context |
| 3.2.2 | On Input | A | Changing a setting never triggers an unexpected change of context |
| 3.2.3 | Consistent Navigation | AA | Repeated navigation appears in the same order |
| 3.2.4 | Consistent Identification | AA | The same function has the same name and icon everywhere |
| 3.3.1 | Error Identification | A | Errors are identified and described in text |
| 3.3.2 | Labels or Instructions | A | Inputs have labels or instructions |
| 3.3.3 | Error Suggestion | AA | Where a fix is known, the error message suggests it |
| 3.3.4 | Error Prevention (Legal, Financial, Data) | AA | Commitments can be reversed, checked or confirmed before submit |

## 4 Robust

| # | Criterion | Level | Check |
|---|---|---|---|
| 4.1.1 | Parsing | A | Removed in WCAG 2.2. For HTML and XML content, W3C has since noted in 2.1 that it is always satisfied; do not report findings under it |
| 4.1.2 | Name, Role, Value | A | Every component exposes name, role, state and value to assistive technology |
| 4.1.3 | Status Messages (2.1) | AA | Status messages (saved, 12 results, error count) are announced without moving focus |

## Often mistaken for AA

| # | Criterion | Actual level | Note |
|---|---|---|---|
| 2.5.5 | Target Size (44 by 44 CSS px) | **AAA** in 2.1 | Called "Target Size (Enhanced)" in 2.2, still AAA. Not part of an AA audit |
| 1.4.6 | Contrast (Enhanced), 7:1 | AAA | AA is 4.5:1 (1.4.3) |
| 3.1.5 | Reading Level | AAA | Plain language belongs in the usability pass |
| 2.4.8 to 2.4.10 | Location, Link Purpose (Link Only), Section Headings | AAA | |
| 3.3.5, 3.3.6 | Help, Error Prevention (All) | AAA | |

Platform guidance such as Material's 48 by 48 dp touch target, or Apple's 44 by 44 pt, is design guidance, not WCAG. Report it as a usability observation, not as a WCAG failure.

## New in WCAG 2.2 (for a 2.2 AA target)

| # | Criterion | Level | Check |
|---|---|---|---|
| 2.4.11 | Focus Not Obscured (Minimum) | AA | The focused element is not entirely hidden by sticky headers, banners or overlays |
| 2.5.7 | Dragging Movements | AA | Every drag action has a single-pointer alternative (buttons, menus) |
| 2.5.8 | Target Size (Minimum) | AA | Targets at least 24 by 24 CSS px, or enough spacing, with exceptions |
| 3.2.6 | Consistent Help | A | Help mechanisms appear in the same place across pages |
| 3.3.7 | Redundant Entry | A | Information already entered in the same process is not asked for again |
| 3.3.8 | Accessible Authentication (Minimum) | AA | Login does not require a cognitive test such as remembering or transcribing, unless an alternative or help exists |

## Links

| What | Where |
|---|---|
| WCAG 2.1 | https://www.w3.org/TR/WCAG21/ |
| WCAG 2.2 | https://www.w3.org/TR/WCAG22/ |
| Quick Reference 2.1 | https://www.w3.org/WAI/WCAG21/quickref/ |
| Understanding WCAG 2.1 | https://www.w3.org/WAI/WCAG21/Understanding/ |
| ARIA Authoring Practices | https://www.w3.org/WAI/ARIA/apg/ |
| axe-core | https://github.com/dequelabs/axe-core |
| BITV-Test, test steps in German | https://www.bitvtest.de/bitv_test/das_testverfahren_im_detail/pruefschritte.html |

## Which rules point here

WCAG is the base of the chain. The European standard EN 301 549 incorporates the WCAG 2.1 A and AA criteria for web content and adds requirements for software and documents. National rules then point to EN 301 549, in Germany for example BITV 2.0 for public bodies and the BFSG (implementing the European Accessibility Act) for products and services for consumers since 28 June 2025. Business-to-business software usually has no direct legal duty, but public-sector buyers ask for conformance in their tenders. Check the version of EN 301 549 a tender names before citing it; it changes.
