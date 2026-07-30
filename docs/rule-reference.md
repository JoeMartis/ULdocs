# Rule Reference

**133 rules** across **26 categories** — 120 static, 13 AI-powered.

By severity: **60 error**, **67 warning**, **6 info**. **103 on** by default, **30 off** (opt-in per program — most of the biology/writing/prompt/objective rules ship off).

Assisted correction: **19 rules auto-fix**, **8 offer a suggestion** (see the end of this file).

|  |  |
| --- | --- |
| **Severity** | `error` blocks publish-readiness · `warning` should be reviewed · `info` advisory only |
| **Type** | `static` runs locally in <1s · `ai` calls Claude (requires API key) |
| **Default** | ✓ on out-of-the-box · ✗ opt-in (enabled per program) |
| **Fix / Suggest** | `auto-fix` edits the file (revertable) · `suggest` proposes text to apply · `—` detect-only |

## Categories

- [Assignments](#assignments) (20)
- [Knowledge Checks](#knowledge-checks) (12)
- [Content Quality](#content-quality) (10)
- [Lectures](#lectures) (9)
- [Learning Objectives](#learning-objectives) (7)
- [Library Content](#library-content) (7)
- [Recitations](#recitations) (7)
- [Admin](#admin) (7)
- [Writing Style](#writing-style) (6)
- [Question Prompts](#question-prompts) (6)
- [Biology Terminology](#biology-terminology) (6)
- [Fonts](#fonts) (4)
- [Transcripts](#transcripts) (4)
- [Custom Pages](#custom-pages) (4)
- [Video](#video) (3)
- [Terms](#terms) (3)
- [Module Summary](#module-summary) (3)
- [Accessibility](#accessibility) (3)
- [Structure](#structure) (3)
- [PDF Slides](#pdf-slides) (2)
- [Broken References](#broken-references) (2)
- [Lists](#lists) (1)
- [Bolding](#bolding) (1)
- [Headings](#headings) (1)
- [AskTIM](#asktim) (1)
- [Summaries](#summaries) (1)

---

## Assignments

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Assignment Explanation Quality** | `assignments-explanation-quality` | warning | ai | ✓ | suggest | Uses AI to evaluate whether assignment solution explanations provide enough detail for learners to understand the underlying concepts. |
| **No Truncated Answer Options** | `assignments-truncated-options` | warning | ai | ✓ | — | Uses AI to detect assignment answer choices that appear incomplete or cut off during authoring, which can confuse learners. |
| **Assignment Naming** | `assignments-naming` | error | static | ✓ | — | Ensures assignments follow the standard naming pattern: "Assignment N: Part N" for consistency across the course. |
| **Question Numbering** | `assignments-question-numbering` | error | static | ✓ | — | Verifies that assignment questions are numbered sequentially from "Question 1" through "Question N" with no gaps or duplicates. |
| **Multiple Choice Attempts** | `assignments-attempts-multiple-choice` | error | static | ✓ | auto-fix | Ensures multiple-choice assignment problems allow exactly 2 attempts, balancing learner practice with assessment rigor. The effective value accounts for edX inheritance: library wrapper, then the problem, then the course-wide max\_attempts default. |
| **Checkbox Attempts** | `assignments-attempts-checkbox` | error | static | ✓ | auto-fix | Ensures standard checkbox assignment problems allow exactly 3 attempts, since selecting multiple correct answers is harder. The effective value accounts for edX inheritance: library wrapper, then the problem, then the course-wide max\_attempts default. |
| **Complex Checkbox Attempts** | `assignments-attempts-complex-checkbox` | warning | static | ✗ | — | Deprecated — all checkbox assignment problems now use 3 attempts via the Checkbox Attempts rule, and checkboxes with 5+ options are instead flagged for rewrite by Too Many Answer Options. Previously gave complex checkboxes (5+ options) an extra attempt. |
| **Problem Bank 2-Option MC Attempts** | `assignments-attempts-problem-bank-2option` | error | static | ✓ | — | Ensures multiple-choice problems from problem banks with only 2 options allow exactly 1 attempt, since a second try would be a guaranteed correct answer. The effective value accounts for edX inheritance: library wrapper, then the problem, then the course-wide max\_attempts default. |
| **Numerical Input Attempts** | `assignments-attempts-numerical` | error | static | ✓ | auto-fix | Ensures numerical input assignment problems allow exactly 3 attempts, giving learners room to correct calculation errors. The effective value accounts for edX inheritance: library wrapper, then the problem, then the course-wide max\_attempts default. |
| **Dropdown Attempts** | `assignments-attempts-dropdown` | error | static | ✓ | auto-fix | Ensures dropdown (option response) problems allow attempts scaled to the option count: 1 attempt for 2 options, 2 attempts for 3–4 options. Dropdowns with 5+ options are left to the "Too Many Answer Options" rule. Scans assignments by default; set params.scope to "all" to also cover knowledge checks. The effective value accounts for edX inheritance. |
| **Simple Checkbox Attempts** | `assignments-attempts-checkbox-simple` | error | static | ✗ | — | Deprecated — checkbox problems now use 3 attempts regardless of option count (below the too-many-options threshold) via the Checkbox Attempts rule. Previously gave simple checkboxes (4 or fewer options) a reduced attempt count. |
| **Text Response Attempts** | `assignments-attempts-text` | error | static | ✗ | auto-fix | Ensures text/short-answer (string response) assignment problems allow a set number of attempts (expectedAttempts param). Scans assignments by default; set params.scope to "all" to also cover knowledge checks. Disabled by default; enabled for this program with expectedAttempts set to 4. |
| **Show Answer Setting** | `assignments-showanswer` | error | static | ✓ | auto-fix | Ensures the "show answer" setting is configured to "after\_all\_attempts\_or\_correct" so learners must try the problem before seeing the answer. |
| **Explanation Present** | `assignments-explanation-present` | error | static | ✓ | suggest | Verifies that every assignment problem has a complete solution explanation to support learning from mistakes. |
| **Explanation Not Question Copy** | `assignments-explanation-not-question` | warning | static | ✓ | — | Detects when the question text was accidentally copied into the explanation field instead of writing an actual explanation. |
| **Overview and Summary Pages** | `assignments-overview-summary` | error | static | ✓ | — | Verifies that each assignment includes both an overview page (introducing the assignment) and a summary page (wrapping it up). |
| **Assignment Not Blank** | `assignments-not-blank` | error | static | ✓ | — | Detects assignment sections that have no content, which usually indicates incomplete course development. |
| **Label Present** | `assignments-label-present` | error | static | ✓ | — | Ensures each assignment problem has a `<label>` element containing the question text, which is required for screen reader accessibility. |
| **Correct Answer Marked** | `assignments-correct-answer` | error | static | ✓ | — | Verifies that every choice-based assignment problem has at least one answer marked as correct. Problems without a correct answer can never be completed. |
| **Notebook Links** | `assignments-notebook-links` | warning | static | ✓ | — | When a Jupyter notebook is referenced in an assignment, verifies that the link points to the correct notebook file. |

## Knowledge Checks

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Knowledge Check Naming** | `knowledge-checks-naming` | error | static | ✓ | — | Ensures knowledge checks follow the standard naming pattern: "Knowledge Check: Question N" (where N is the question number), optionally preceded by a topic prefix like "Editing: ". |
| **Knowledge Check Named After Video** | `knowledge-checks-video-name` | warning | static | ✗ | — | Biology naming convention: a knowledge check is named after the video that precedes it in the module, e.g. "Knowledge Check: Molecular Biology Experiment". When a video has two or more knowledge checks, they take an A/B/C… suffix ("Knowledge Check A: …", "Knowledge Check B: …"). An alternative to the "Question N" naming rule; disabled by default, enable per program. |
| **Sequential Numbering** | `knowledge-checks-sequential-numbering` | error | static | ✓ | — | Verifies that knowledge checks are numbered sequentially across each module with no gaps or duplicates. |
| **Max Attempts** | `knowledge-checks-max-attempts` | error | static | ✓ | auto-fix | Ensures knowledge check problems allow the expected number of attempts (default 3; knowledge checks are low-stakes formative assessments). Individual problem types can require a different count via params.perTypeAttempts — in biology, numerical and text (string) problems allow 5. Problem types listed in params.excludeProblemTypes are governed instead by their own option-scaled attempt rules — in biology, multiple-choice, checkbox, and dropdown. The effective value accounts for edX inheritance: library wrapper, then the problem, then the course-wide max\_attempts default. |
| **Complex Checkbox Attempts** | `knowledge-checks-complex-checkbox-attempts` | warning | static | ✗ | — | Deprecated — all knowledge check problems now use 3 attempts via the Max Attempts rule. Previously gave complex checkboxes (5+ options) an extra attempt. |
| **Show Answer Setting** | `knowledge-checks-showanswer` | error | static | ✓ | auto-fix | Ensures the "show answer" setting is configured to "after\_all\_attempts\_or\_correct" so learners must attempt the problem before seeing the answer. |
| **Explanation Present** | `knowledge-checks-explanation-present` | error | static | ✓ | suggest | Verifies that every knowledge check has a non-empty solution/explanation block, so learners understand why the answer is correct. Whether that explanation is labeled with the word "Explanation" is checked separately by knowledge-checks-explanation-keyword. |
| **Explanation Keyword** | `knowledge-checks-explanation-keyword` | warning | static | ✓ | — | Warns when a knowledge check has an explanation that does not include the word "Explanation" (a labeling convention). A trivial wording fix, so this is a warning with no AI suggestion. |
| **Label Present** | `knowledge-checks-label-present` | error | static | ✓ | — | Ensures each knowledge check problem has a `<label>` element containing the question text, which is required for screen reader accessibility. |
| **Correct Answer Marked** | `knowledge-checks-correct-answer` | error | static | ✓ | — | Verifies that every choice-based knowledge check has at least one answer marked as correct. Problems without a correct answer can never be completed. |
| **Knowledge Check Explanation Quality** | `knowledge-checks-explanation-quality` | warning | ai | ✓ | suggest | Uses AI to evaluate whether solution explanations are detailed enough to help learners understand the concept, not just the correct answer. |
| **No Truncated Answer Options** | `knowledge-checks-truncated-options` | warning | ai | ✓ | — | Uses AI to detect answer choices that appear incomplete or cut off during authoring, which can confuse learners. |

## Content Quality

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **No Empty HTML Components** | `html-empty-content` | warning | static | ✓ | — | Detects HTML components that are blank or contain only whitespace, which appear as empty space to learners. |
| **No Duplicate Choices** | `problem-duplicate-choices` | error | static | ✓ | — | Detects multiple-choice and checkbox problems that have identical answer choices, which confuse learners and indicate a copy-paste error. |
| **No Single-Choice Questions** | `problem-single-choice` | error | static | ✓ | — | Ensures multiple-choice problems have at least 2 answer choices. A single choice makes the question trivial. |
| **Links Open New Window** | `links-open-new-window` | error | static | ✓ | — | Ensures links to Jupyter notebooks (.ipynb) and PDF slides open in a new window (target="\_blank") so learners don't lose their place in the course. |
| **No Paste Artifacts in Problems** | `problem-paste-artifacts` | error | static | ✓ | auto-fix | Detects Word/Office or AI (ChatGPT) copy-paste artifacts in problem XML, such as mso-\* styles, data-start attributes, or ChatGPT wrapper markup. |
| **No Empty Paragraphs** | `html-empty-paragraphs` | warning | static | ✓ | auto-fix | Detects empty paragraph tags (  ,  , or  ) that create unwanted blank space in the content. |
| **No Empty Choices** | `problem-empty-choice` | error | static | ✓ | — | Detects answer choices that are blank or contain only whitespace, which usually indicates the problem was not fully authored. |
| **No Option Letters or Numbers** | `problem-option-labels` | warning | static | ✓ | — | Flags answer choices that are hand-labeled with a letter or number ("A. ", "1) ", "(a) ") and explanations that refer to a choice by its position ("option B", "the first choice"). edX shuffles option order, so hand-typed labels and positional references end up wrong. |
| **Dropdown Correct Answer Matches an Option** | `problem-dropdown-correct-match` | error | static | ✓ | — | For dropdown (option response) problems that mark the correct answer with a correct="…" attribute, verifies that value exactly matches one of the listed options. A stray space or typo makes no option correct, so the problem can never be completed. |
| **Too Many Answer Options** | `problem-too-many-options` | warning | static | ✗ | — | Flags multiple-choice, checkbox, and dropdown problems with more than 4 answer options in a single response group (5 or more), which the faculty guide flags for rewrite or double-checking. Threshold configurable via params.maxOptions. |

## Lectures

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Lecture Naming** | `lectures-naming` | warning | static | ✓ | — | Ensures lectures follow the standard naming pattern: "L X.Y" followed by the topic name (e.g., "L 1.2 Introduction to Python"). |
| **Overview Present** | `lectures-overview-present` | error | static | ✓ | — | Verifies that each lecture includes an overview page with learning objectives so learners know what to expect. |
| **Summary Present** | `lectures-summary-present` | error | static | ✓ | — | Verifies that each lecture includes a summary page to reinforce key concepts covered in the lecture. |
| **Summary Key Takeaways** | `lectures-summary-takeaways` | warning | static | ✓ | — | Checks that each lecture summary includes a list of key takeaways to help learners remember the most important points. |
| **Overview Bold Title** | `lectures-overview-bold-title` | warning | static | ✓ | — | Checks that the lecture title is bolded in the overview page for visual prominence and consistent formatting. |
| **Overview Bold Professor** | `lectures-overview-bold-professor` | warning | static | ✓ | — | Checks that the professor's name is bolded in the lecture overview page for consistent formatting. |
| **Video Duration** | `lectures-video-duration` | warning | static | ✓ | — | Checks that lecture videos are between 5 and 10 minutes long. Shorter videos may lack depth; longer ones reduce learner engagement. |
| **Title Matches Video** | `lectures-title-matches-video` | warning | static | ✓ | — | Verifies that the unit title matches the embedded video title, catching cases where videos were placed in the wrong unit. |
| **Lecture Not Blank** | `lectures-not-blank` | error | static | ✓ | — | Detects lecture units that have no content, which usually indicates incomplete course development. |

## Learning Objectives

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Bold Topics in Objectives** | `learning-objectives-bold-topics` | info | static | ✓ | — | Checks that key topic names in learning objectives are bolded with  **tags for visual emphasis and scannability.** |
| **AskTIM on Objectives** | `learning-objectives-asktim` | warning | static | ✓ | — | Verifies that the AskTIM chat assistant is enabled on learning objectives pages so learners can ask questions about what they'll learn. |
| **Avoid Vague Objective Verbs** | `learning-objectives-vague-verbs` | warning | static | ✗ | — | Flags learning objectives that begin with vague, non-measurable verbs (e.g. "understand", "know", "be familiar with"); objectives should use measurable action verbs from Bloom's taxonomy. The deterministic counterpart to the AI "Measurable Objective Verbs" check. |
| **Objectives Use Bullet Points** | `learning-objectives-use-bullets` | info | static | ✗ | — | Flags learning objectives presented as a numbered list (  ) rather than bullet points (  ). |
| **Objectives Introductory Stem** | `learning-objectives-stem-format` | warning | static | ✗ | — | Checks that a learning-objectives list is introduced with an expected stem, e.g. "At the end of this \_\_\_, you will/should be able to:" or "Our goals for this \_\_\_ are:". |
| **Measurable Objective Verbs** | `learning-objectives-action-verbs` | warning | ai | ✗ | — | Uses AI to check that learning objectives begin with specific, measurable action verbs (Bloom's taxonomy) rather than vague verbs like "understand" or "be familiar with". |
| **Student-Centered Objectives** | `learning-objectives-student-centered` | warning | ai | ✗ | — | Uses AI to check that learning objectives are student-centered — framed as what the learner will be able to do ("students will be able to ...") — rather than instructor- or content-centered ("this lecture covers ..."). |

## Library Content

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **No Truncated Answer Options** | `library-content-truncated-options` | warning | ai | ✓ | — | Uses AI to detect problem bank answer choices that appear incomplete or cut off during authoring, which can confuse learners. |
| **Explanation Present** | `library-content-explanation-present` | error | static | ✓ | suggest | Verifies that every problem in the shared problem bank has a non-empty solution/explanation block. Whether that explanation is labeled with the word "Explanation" is checked separately by library-content-explanation-keyword. |
| **Explanation Keyword** | `library-content-explanation-keyword` | warning | static | ✓ | — | Warns when a problem-bank problem has an explanation that does not include the word "Explanation" (a labeling convention). A trivial wording fix, so this is a warning with no AI suggestion. |
| **Label Present** | `library-content-label-present` | error | static | ✓ | — | Ensures problem bank problems have a `<label>` or `<div>` element containing the question text for accessibility. |
| **Correct Answer Marked** | `library-content-correct-answer` | error | static | ✓ | — | Verifies that every choice-based problem in the problem bank has at least one answer marked as correct. |
| **Explanation Not Question Copy** | `library-content-explanation-not-question` | warning | static | ✓ | — | Detects when the solution text is just a copy of the question text, which usually indicates the explanation was not actually written. |
| **Library Content Explanation Quality** | `library-content-explanation-quality` | warning | ai | ✓ | suggest | Uses AI to evaluate whether problem bank solution explanations are detailed enough to support deeper learning beyond just knowing the answer. |

## Recitations

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Recitation Naming** | `recitations-naming` | warning | static | ✓ | — | Ensures recitations follow the standard naming pattern: "R X.Y" followed by the topic name (e.g., "R 1.2 Data Wrangling Practice"). |
| **Overview Present** | `recitations-overview-present` | error | static | ✓ | — | Verifies that each recitation includes an overview page introducing what will be covered. |
| **Summary Present** | `recitations-summary-present` | error | static | ✗ | — | Verifies that each recitation includes a summary page to reinforce key concepts. |
| **Overview Bold Title** | `recitations-overview-bold-title` | warning | static | ✓ | — | Checks that the recitation title is bolded in the overview page for consistent formatting. |
| **Overview Bold Professor** | `recitations-overview-bold-professor` | warning | static | ✓ | — | Checks that the professor's name is bolded in the recitation overview page for consistent formatting. |
| **Video Duration** | `recitations-video-duration` | warning | static | ✓ | — | Checks that recitation videos are between 5 and 10 minutes long to maintain learner engagement. |
| **Title Matches Video** | `recitations-title-matches-video` | warning | static | ✓ | — | Verifies that the unit title matches the embedded video title, catching misplaced videos. |

## Admin

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Homework Grading Weight** | `admin-grading-homework-weight` | error | static | ✓ | — | Ensures the Homework grading category is weighted at 20% of the total grade. |
| **Assignment Grading Weight** | `admin-grading-assignment-weight` | error | static | ✓ | — | Ensures the Assignment grading category is weighted at 80% of the total grade. |
| **Self-Paced Mode** | `admin-self-paced` | error | static | ✓ | — | Ensures the course is set to self-paced mode, allowing learners to progress at their own speed. |
| **Start Date Future** | `admin-start-date-future` | warning | static | ✓ | — | Ensures the course start date is set and is in the future. A start date in the past means the course may already be visible to learners. |
| **Beta Days Early** | `admin-beta-days` | error | static | ✓ | — | Ensures days\_early\_for\_beta is set to 365 so beta testers can access the course a full year before the start date. |
| **Discussions Disabled** | `admin-discussions-disabled` | error | static | ✓ | — | Ensures the global Discussions tab is hidden, since this course uses alternative discussion mechanisms. |
| **No Discussions in Sections** | `admin-discussions-enabled-in-sections` | error | static | ✓ | auto-fix | Ensures no individual sections have discussion\_enabled set to true, preventing stray discussion threads in the course content. |

## Writing Style

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Avoid "Please"** | `writing-avoid-please` | warning | static | ✗ | — | Flags use of "please" in instructional text. Course directions should be stated directly (e.g. "Select the best answer" rather than "Please select the best answer"). |
| **Space Between Number and Unit** | `writing-number-unit-space` | warning | static | ✗ | — | Flags a number written with no space before its unit — "37°C" instead of "37 °C", "5kg" instead of "5 kg". Standard scientific notation always puts a space between the numeric value and the unit symbol (including the degree symbol). Covers the degree symbol (literal or ° entity) and a list of multi-character units; single-letter units are excluded to avoid false positives (1990s, 100s). Percent is opt-in via params.flagPercent; extend the unit list via params.extraUnits. |
| **Avoid US Idioms** | `text-avoid-idioms` | warning | static | ✗ | — | Flags US idioms and figurative phrases ("break a leg", "reach out", "a piece of cake") in HTML, problems, and video transcripts, which can confuse learners reading English as a second language. Prefer a literal phrasing. Override or extend the phrase list via params.idioms. |
| **No Contractions** | `writing-no-contractions` | warning | static | ✗ | — | Flags contractions (don't, it's, you're, etc.) in instructional and problem text, in favor of a more formal tone. Possessives ("the cell's membrane") are not flagged. |
| **Active Voice** | `writing-active-voice` | warning | ai | ✗ | — | Uses AI to flag instructional text that relies heavily on passive voice where active voice would read more clearly. |
| **Oxford Comma** | `writing-oxford-comma` | warning | ai | ✗ | — | Uses AI to flag lists of three or more items that omit the serial (Oxford) comma before the final "and"/"or". |

## Question Prompts

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Multiple Choice: "Select the best answer"** | `prompts-mc-select-best-answer` | warning | static | ✗ | — | Ensures single-answer multiple-choice problems include the instruction "Select the best answer." so learners know exactly one option is expected. |
| **Checkbox: "Select all that apply"** | `prompts-checkbox-select-all` | warning | static | ✗ | — | Ensures checkbox (multi-answer) problems include the instruction "Select all that apply." so learners know more than one option may be correct. |
| **Numerical: Answer-Format Instruction** | `prompts-numerical-answer-format` | warning | static | ✗ | — | Ensures numerical-input problems tell the learner how to format their answer. The expected phrase depends on the answer type: whole number ("Enter your answer as a whole number in the space provided."), percentage ("Enter your answer as a percentage with no rounding. Do not include the percent symbol in your response."), or decimal ("Enter your answer as a decimal to two significant figures."). |
| **Dropdown: "Use the drop-down options to …"** | `prompts-dropdown-instruction` | warning | static | ✗ | — | Ensures dropdown (option response) problems include a prompt beginning "Use the drop-down options to …" (the remainder is question-specific). |
| **Open-Ended: Auto-Credit Phrase** | `prompts-open-ended-credit-phrase` | warning | static | ✗ | — | Ensures open-ended one-sentence problems that auto-grade any non-empty answer as correct (a customresponse with a textline and an any-answer check) end with "Any thoughtful answer will receive credit; click the Show Answer button to check your thoughts." |
| **Answer Option Formatting** | `prompts-answer-option-format` | warning | ai | ✗ | — | Uses AI to check answer-choice capitalization and terminal punctuation. Options should start lowercase unless the option is a proper noun or a full sentence. A terminal period is expected only on full-sentence options. |

## Biology Terminology

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Avoid "PCR reaction"** | `bio-pcr-reaction` | warning | static | ✗ | — | Flags the redundant phrase "PCR reaction", including prefixed variants (qPCR, RT-PCR, ddPCR, real-time PCR) — the R in PCR already stands for "reaction". |
| **Avoid Possessives on Scientific Terms** | `bio-active-site-possessive` | warning | static | ✗ | — | Flags the possessive form of scientific terms (e.g. "protein's", "DNA's", "cell's", "gene's") regardless of the following word — prefer "the active site of the protein" over "the protein's active site". |
| **Dideoxy (Sanger) sequencing** | `bio-sanger-dideoxy` | warning | static | ✗ | — | Flags bare "Sanger sequencing"; the method should be introduced as "dideoxy (Sanger) sequencing". |
| **Address learners as "you"** | `bio-address-as-you` | info | static | ✗ | — | Flags "student"/"user" in prose in favor of addressing the reader directly as "you". Per faculty, "learner" is the accepted third-person term (used in Universal) and is not flagged. |
| **Italicize biological nomenclature** | `bio-italics-nomenclature` | warning | ai | ✗ | — | Uses AI to check that genus/species names, gene symbols, and restriction-enzyme prefixes are italicized, and that protein names are not. These are conventional typographic italics, not emphasis — use `<i>`, not `<em>`. |
| **Dominant/Recessive Describes the Trait** | `bio-phenotype-dominance` | warning | static | ✗ | — | Per faculty convention, a phenotype/trait is dominant or recessive — an allele, gene, or mutation is not. Flags "dominant"/"recessive" attached to "allele", "gene", or "mutation" (e.g. "the dominant allele") and suggests rephrasing (e.g. "the allele encoding the dominant trait"). "Dominant trait", "recessive phenotype", "dominant eye color" are correct and not flagged. |

## Fonts

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **No Custom Font Family** | `fonts-family-default` | error | static | ✓ | auto-fix | Ensures no inline font-family styles are applied. Custom fonts break the platform's consistent look and may not render correctly on all devices. |
| **No Custom Font Size** | `fonts-size-default` | warning | static | ✓ | auto-fix | Ensures no inline font-size styles are applied. Custom font sizes override the platform's responsive typography and can harm readability. |
| **No Custom Font Color** | `fonts-color-default` | warning | static | ✓ | auto-fix | Ensures no inline color styles are applied. Custom colors can break accessibility contrast requirements and visual consistency. |
| **No Copy-Paste Artifacts** | `word-paste-artifacts` | error | static | ✓ | auto-fix | Detects leftover markup from pasting content out of Word, Office, or AI tools. Catches mso- *styles, Mso* classes,  tags,  tags, and AI-generated data attributes like data-start and data-end. |

## Transcripts

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Transcript Present** | `transcripts-present` | error | static | ✓ | — | Verifies that every video has an associated transcript file. Transcripts are required for accessibility and aid comprehension. |
| **Transcript Downloadable** | `transcripts-downloadable` | error | static | ✓ | — | Verifies that transcripts have download\_track set to true so learners can download them for offline use. |
| **Instructor Speaker Name** | `transcripts-instructor-speaker` | warning | static | ✓ | — | Checks that all transcripts use "INSTRUCTOR" as the speaker name for consistency across the course. |
| **Transcripts Not Empty** | `transcripts-not-empty` | error | static | ✓ | — | Ensures transcript SRT files contain real content (at least 10 lines) and are not empty or placeholder-only files. |

## Custom Pages

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Resources Tab Exists** | `custom-pages-resources-exists` | error | static | ✓ | — | Verifies that the course includes a Resources tab where learners can find supplemental materials. |
| **Glossary Tab Exists** | `custom-pages-glossary-exists` | error | static | ✓ | — | Verifies that the course includes a Glossary tab defining key terms used throughout the course. |
| **Attributions Tab Exists** | `custom-pages-attributions-exists` | warning | static | ✓ | — | Checks for an Attributions tab that credits third-party content used in the course. |
| **Glossary Course Name** | `custom-pages-glossary-course-name` | warning | static | ✓ | — | Verifies that the glossary page references the correct course name, catching cases where a glossary was copied from another course. |

## Video

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Video Present** | `video-present` | error | static | ✓ | — | Verifies that every lecture and recitation vertical contains a video component. Missing videos indicate incomplete content. |
| **Video Downloadable** | `video-downloadable` | error | static | ✓ | — | Verifies that videos have download\_video set to true so learners can download them for offline viewing. |
| **Unique Video Name in Module** | `video-unique-name-in-module` | warning | static | ✓ | — | Flags two or more videos sharing the same display name within one module (chapter). Duplicate video names cause knowledge checks named after their video to collide. |

## Terms

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Learner Not Student** | `terms-learner-not-student` | warning | static | ✓ | suggest | Ensures inclusive language by checking that content uses "learner(s)" instead of "student", "user", or second-person "you". |
| **Acronym Plural Consistency** | `terms-acronym-consistency` | info | ai | ✓ | — | Uses AI to check that acronyms are pluralized consistently throughout the course (e.g., always "APIs" or always "API's", not a mix). |
| **Define Acronyms on First Use** | `text-acronym-first-use` | warning | static | ✓ | — | Flags an acronym used in HTML or problem text before it is defined. The first course-wide use should spell it out, e.g. "endoplasmic reticulum (ER)"; bare uses after that are fine. Widely understood acronyms (DNA, RNA, PCR, …) are exempt; extend the exemptions via params.allowAcronyms. |

## Module Summary

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Module Summary Exists** | `module-summary-exists` | error | static | ✓ | — | Verifies that each module has a summary page providing a wrap-up of the module's content. |
| **Module Feedback Form Link** | `module-summary-has-survey-link` | warning | static | ✓ | — | Checks that the module summary includes a link whose text is "Module Feedback Form" so learners can share their experience. |
| **Dashboard Link Present** | `module-summary-has-dashboard-link` | warning | static | ✓ | — | Checks that the module summary includes a link back to the course dashboard for easy navigation. |

## Accessibility

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Image Alt Text** | `html-img-alt-text` | error | static | ✓ | — | Ensures every `<img>` tag has a non-empty alt attribute so screen readers can describe images to visually impaired learners. |
| **No Empty Links** | `html-empty-links` | error | static | ✓ | — | Ensures every tag has visible link text or an aria-label so screen readers can describe the link's purpose. |
| **Math Notation Should Use MathJax** | `accessibility-math-mathjax` | warning | static | ✗ | — | Flags math/science notation authored as plain text or HTML that the accessibility team's screen-reader testing found needs MathJax to read correctly: caret exponents (x^2), scientific notation (2 × 10^-5), unicode and HTML super/subscripts including lone letters and charges (mⁿ, Cl- — screen readers don't announce the super/subscript; ordinals like "1st" are exempt), the multiplication sign × (read as the letter "x"), and symbols that only read aloud in MathJax. Only fires outside existing MathJax. Does not flag standalone Greek letters, temperature degrees, or relational operators (≤ ≥ ≠ ±), which read correctly in HTML. Plain-text chemical formulas/ions (H2O, Mg2+) are flagged only when params.flagChemistry is true (element-symbol validated to limit noise). Extend the MathJax-only symbol list via params.specialSymbols. |

## Structure

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Chapters Have Content** | `chapter-has-content` | error | static | ✓ | — | Verifies that every chapter contains at least one sequential (subsection). Empty chapters indicate incomplete course structure. |
| **Sequential Ordering Consistent** | `sequential-ordering-consistency` | warning | static | ✓ | — | Checks that subsections within each chapter follow consistent numbering without unexpected gaps. |
| **Draft Content Warning** | `structure-has-drafts` | info | static | ✓ | — | Reports drafts in the drafts/ directory that are genuinely unpublished — new content with no published counterpart, or drafts whose content differs from the published version. Stale drafts identical to published content (common after re-runs and imports) are ignored. |

## PDF Slides

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Slide Link Format** | `pdf-slides-link-format` | warning | static | ✓ | — | Checks that slide download link text is a label naming the deck and ends with "(PDF)", e.g. "Lecture 1.1 (PDF)". Texts like "PDF version" or a bare "(PDF)" don't qualify. |
| **Slide Link Separate Component** | `pdf-slides-separate-component` | warning | static | ✓ | — | Verifies that the slide download link is placed in its own HTML component directly below the video, not embedded in other content. |

## Broken References

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Static File Links Valid** | `html-broken-static-links` | error | static | ✓ | — | Verifies that all links pointing to /static/ files actually reference files that exist in the course export. |
| **Video Has edX ID** | `video-missing-edx-id` | error | static | ✓ | — | Ensures every video component has a non-empty edxVideoId. Missing IDs mean the video won't play on the platform. |

## Lists

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **No Paragraphs in List Items** | `lists-no-p-in-li` | error | static | ✓ | auto-fix, suggest | Ensures list items do not contain nested tags, which cause extra spacing and inconsistent rendering across browsers. |

## Bolding

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Use Strong for Bold** | `bolding-use-strong` | error | static | ✓ | auto-fix | Ensures bold text uses semantic  **tags instead of deprecated  **tags or inline font-weight styles, improving accessibility and consistency.**** |

## Headings

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **H4 in Overview/Summary** | `headings-h4-overview-summary` | error | static | ✓ | auto-fix | Ensures section headers in overview and summary pages usetags to maintain a consistent heading hierarchy across the course. |

## AskTIM

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **AskTIM Chat Enabled** | `asktim-present` | warning | static | ✓ | — | Checks that the AskTIM AI chat assistant is enabled on relevant content blocks via OL\_OPENEDX\_CHAT settings, giving learners on-demand help. |

## Summaries

| Rule | ID | Severity | Type | Default | Fix / Suggest | What it checks |
| --- | --- | --- | --- | --- | --- | --- |
| **Summary Bolding Standards** | `summaries-bolding-standards` | info | static | ✓ | — | Checks that bold formatting in summary takeaways follows course standards, using  **tags consistently for key terms.** |

---

## Auto-fix rules

These rules can edit the export file directly (the change is revertable in the UI).

- **No Discussions in Sections** (`admin-discussions-enabled-in-sections`)
- **Checkbox Attempts** (`assignments-attempts-checkbox`)
- **Dropdown Attempts** (`assignments-attempts-dropdown`)
- **Multiple Choice Attempts** (`assignments-attempts-multiple-choice`)
- **Numerical Input Attempts** (`assignments-attempts-numerical`)
- **Text Response Attempts** (`assignments-attempts-text`)
- **Show Answer Setting** (`assignments-showanswer`)
- **Use Strong for Bold** (`bolding-use-strong`)
- **No Custom Font Color** (`fonts-color-default`)
- **No Custom Font Family** (`fonts-family-default`)
- **No Custom Font Size** (`fonts-size-default`)
- **H4 in Overview/Summary** (`headings-h4-overview-summary`)
- **No Empty Paragraphs** (`html-empty-paragraphs`)
- **Max Attempts** (`knowledge-checks-max-attempts`)
- **Show Answer Setting** (`knowledge-checks-showanswer`)
- **No Paragraphs in List Items** (`lists-no-p-in-li`)
- **No Paste Artifacts in Problems** (`problem-paste-artifacts`)
- **No Copy-Paste Artifacts** (`word-paste-artifacts`)

## Suggestion rules

These rules propose replacement text for the author to apply. The "Explanation Quality" suggestions are AI-generated; the rest are template/text replacements.

- **Explanation Present** (`assignments-explanation-present`)
- **Assignment Explanation Quality** (`assignments-explanation-quality`)
- **Explanation Present** (`knowledge-checks-explanation-present`)
- **Knowledge Check Explanation Quality** (`knowledge-checks-explanation-quality`)
- **Explanation Present** (`library-content-explanation-present`)
- **Library Content Explanation Quality** (`library-content-explanation-quality`)
- **No Paragraphs in List Items** (`lists-no-p-in-li`)
- **Learner Not Student** (`terms-learner-not-student`)
