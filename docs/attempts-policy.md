# Attempts Policy

| Problem type | Answer options | Knowledge Check | Assignment | Enforced by |
| --- | --- | --- | --- | --- |
| Multiple choice (single answer) | any | **2** | **2** | Multiple Choice Attempts |
| Multiple choice — problem bank | exactly 2 | 2 † | **1** | Problem Bank 2-Option MC Attempts |
| Numerical input | — | **5** | **3** | KC Max Attempts / Numerical Attempts |
| Dropdown — one dropdown | 2 | **1** | **1** | Dropdown Attempts |
| Dropdown — one dropdown | 3–4 | **2** | **2** | Dropdown Attempts |
| Dropdown — 2–4 dropdowns, incl. matching | any | **2** | **2** | Dropdown Attempts *(see below)* |
| Dropdown — 5 or more dropdowns | any | *split into more than one problem* | *split into more than one problem* | *no rule checks this* |
| Checkbox (multi-select) | ≤ 4 | **3** | **3** | Checkbox Attempts |
| MC / Checkbox / Dropdown | 5 or more | *flagged to rewrite* | *flagged to rewrite* | Too Many Answer Options |
| Text / short-answer (string) | — | **5** | **4** | KC Max Attempts / Text Response Attempts |
| Drag and drop | 2–4 items | **3** | **2** | *pending parser support (see below)* |
| Drag and drop | 5–6 items | **4** | **3** | *pending parser support (see below)* |
| Drag and drop | 7–8 items | **5** | **4** | *pending parser support (see below)* |
| Drag and drop | 9+ items | *flagged to split into multiple problems* | *flagged to split into multiple problems* | *pending parser support (see below)* |
| Open response, ungraded (ORA) | — | **2** | — | *pending parser support (see below)* |

Where a count is enforced it is exact — too few attempts is flagged just like
too many. A quick-reference copy of this table is in the
[Problem Templates](problem-authoring-guide.html#attempts-quick-reference) guide.

## Notes & edge cases

- **KC vs Assignment divergence:** numerical (KC 5 / assignment 3), text
  (KC 5 / assignment 4), and drag and drop (KC always one more than assignment)
  intentionally differ — knowledge checks are low-stakes formative practice, so
  learners get more tries there. Multiple choice, dropdown, and checkbox still
  match across the two.
- **† 2-option problem-bank MC → 1 attempt** applies to **assignments only** (a
  second try on a 2-option question guarantees the correct answer). A directly
  authored 2-option MC follows the general MC rule (2). A 2-option MC pooled
  inside a knowledge check is not specifically reduced — a small known gap.
- **5+ options:** no attempt count is enforced — the "Too Many Answer Options" rule
  flags the question for rewrite instead (faculty guidance is to avoid 5+
  options).
- **Several dropdowns in one question** are counted by the number of dropdowns,
  not the choices in each: 2–4 dropdowns get 2 attempts whatever each one
  offers, and a question with 5 or more should be split into more than one
  problem. A one-to-one match set is several dropdowns and follows the same
  counts. The QA pass's Dropdown Attempts rule is described as scaling by the
  number of choices — 1 attempt for 2 — so on a question of several
  two-choice dropdowns it may expect 1. The policy is 2: if it flags such a
  question, do not apply its auto-fix, which would set it to 1.
- **Drag and drop scales with item count:** more draggable items means more
  chances to place one wrong, so attempts step up in the same spirit as the
  Dropdown and Checkbox option-count scaling. A problem with 9 or more items
  should be split into multiple problems rather than given more attempts,
  mirroring the "Too Many Answer Options" philosophy above. A **strict
  one-to-one match** (every zone used exactly once, no repeats) gets **one
  additional attempt** at every tier, since there is no elimination benefit the
  way there is when zones repeat.
- **Drag and drop / Open response (ORA):** the parser does not yet recognize the
  `drag-and-drop-v2` or `openassessment` block types (it detects only
  `multiplechoiceresponse`, `choiceresponse`, `numericalresponse`,
  `stringresponse`, and `optionresponse`). Their attempt rules are specified
  above but **not yet enforced** — they await parser support keyed off a sample
  export. ORA in particular has no standard `max_attempts` attribute, so where
  its "2 attempts" lives in the export needs to be confirmed.
- **Polls** take no attempts: a poll is not graded, and how many times a learner
  may vote is its own **Submissions allowed** setting — 1 unless the poll says
  otherwise.
- **Scope:** these rules apply to problems in KC sections, assignment sections,
  **and** any practice ("Test Yourself") questions embedded in lectures, so a
  learner sees consistent behavior everywhere. If ungraded lecture practice
  should be exempt, that is a future refinement.

## Where this is configured

- Attempt rules: `src/lib/rules/checks/assignments.ts` (per-type, incl. Text
  Response Attempts), `src/lib/rules/checks/knowledge-checks.ts` (KC Max
  Attempts, now with a `perTypeAttempts` map).
- Which are enabled/tuned for Biology: `config/profiles/ubio.json`
  (`scope: "all"` extends a rule to knowledge checks; `excludeProblemTypes` on
  KC Max Attempts hands types off to the per-type rules; `perTypeAttempts` sets
  numerical/text KCs to 5).
- Rule catalog: [Rule Reference](rule-reference.html).
