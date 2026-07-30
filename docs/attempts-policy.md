# Attempts Policy

| Problem type | Answer options | Knowledge Check | Assignment | Enforced by |
| --- | --- | --- | --- | --- |
| Multiple choice (single answer) | any | **2** | **2** | Multiple Choice Attempts |
| Multiple choice — problem bank | exactly 2 | 2 † | **1** | Problem Bank 2-Option MC Attempts |
| Numerical input | — | **5** | **3** | KC Max Attempts / Numerical Attempts |
| Dropdown | 2 | **1** | **1** | Dropdown Attempts |
| Dropdown | 3–4 | **2** | **2** | Dropdown Attempts |
| Checkbox (multi-select) | ≤ 4 | **3** | **3** | Checkbox Attempts |
| MC / Checkbox / Dropdown | 5 or more | *flagged to rewrite* | *flagged to rewrite* | Too Many Answer Options |
| Text / short-answer (string) | — | **5** | **4** | KC Max Attempts / Text Response Attempts |
| Drag and drop | — | **5** | **4** | *pending parser support (see below)* |
| Open response, ungraded (ORA) | — | **2** | — | *pending parser support (see below)* |

## Notes & edge cases

- **KC vs Assignment divergence:** numerical (KC 5 / assignment 3) and text
  (KC 5 / assignment 4) intentionally differ — knowledge checks are low-stakes
  formative practice, so learners get more tries there. Multiple choice,
  dropdown, and checkbox still match across the two.
- **† 2-option problem-bank MC → 1 attempt** applies to **assignments only** (a
  second try on a 2-option question guarantees the correct answer). A directly
  authored 2-option MC follows the general MC rule (2). A 2-option MC pooled
  inside a knowledge check is not specifically reduced — a small known gap.
- **5+ options:** no attempt count is enforced — the "Too Many Answer Options" rule
  flags the question for rewrite instead (faculty guidance is to avoid 5+
  options).
- **Drag and drop / Open response (ORA):** the parser does not yet recognize the
  `drag_and_drop_v2` or `openassessment` block types (it detects only
  `multiplechoiceresponse`, `choiceresponse`, `numericalresponse`,
  `stringresponse`, and `optionresponse`). Their attempt rules are specified
  above but **not yet enforced** — they await parser support keyed off a sample
  export. ORA in particular has no standard `max_attempts` attribute, so where
  its "2 attempts" lives in the export needs to be confirmed.
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
