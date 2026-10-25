# gate-cse-mocks — GATE CSE 2027 mock test series

Daily, self-contained mock tests for **GATE CSE 2027**, one unit per day on a 16-unit rotation of Discrete
Mathematics. Every test is a single HTML file that opens in any browser, offline, in a TCS iON–style exam shell:
question palette with the standard status colours, a running countdown, radio MCQ, checkbox MSQ and typed NAT answers,
and no answer, option mark or hint visible until the test is submitted.

## Latest test

- **Unit 1 — Propositional Logic**, 2026-10-25, Set 2 → [`discrete-mathematics/propositional-logic/gate_dm_mock_1_2026-10-25.html`](discrete-mathematics/propositional-logic/gate_dm_mock_1_2026-10-25.html)
- Set 1 of the same unit and date is archived at [`.../archive/gate_dm_mock_1_2026-10-25_run1.html`](discrete-mathematics/propositional-logic/archive/gate_dm_mock_1_2026-10-25_run1.html)
- 25 questions: 15 MCQ · 5 MSQ · 5 NAT · difficulty 10 easy / 10 medium / 5 hard · 60 minutes · 35 marks
- Subtopics: propositions & connectives · truth tables · logical equivalences · implications & inference · CNF/DNF · validity & satisfiability

## Status

| Item | Value |
| --- | --- |
| Mock tests published | 3 (Unit 16 Set 3, Unit 1 Set 2; 2 units) |
| Units covered | 2 of 16 |
| Questions in master_bank.json | 125 (75 in Unit 16, 50 in Unit 1) |
| Verified official PYQs | 2 |
| Archived sets (earlier runs) | 3 (2 Unit 16, 1 Unit 1) |

## Rotation log

- **2026-10-25, Unit 1 (second set).** `master_bank.json` showed Unit 1 with 25 banked questions, current since the
  same date — under the 50-question cap and current for 0 days — so the rotation re-selected Unit 1 instead of
  advancing. 25 + 25 = 50 closes Unit 1 at the cap; the next run for this subject advances to
  (0 + 1) mod 16 = Unit 2, Predicate & First-Order Logic.
- Set 2 repeats no question from Set 1. It contains no `GATE_PYQ_VARIATION` item, and the About tab says so: every
  question is `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`.

- **2026-10-25, Unit 16 → Unit 1.** Unit 16 had reached 75 banked questions, i.e. at or beyond the
  50-question unit cap, so the rotation advanced by the modulo rule: (15 + 1) mod 16 = 0 → Unit 1.
- The unit for a run is chosen from `master_bank.json` (questions banked per unit, and the date of that unit's first
  paper), never from the calendar. Unit 16 stops at 75 because runs 1–3 were produced before the cap rule was applied;
  it is closed to new sets and will be revisited only after the other 15 units complete a pass.
- No second pass has started yet; units 2–15 are still untouched.
- Subject selection: the series is running Discrete Mathematics, the only subject with a question bank. Subject
  rotation across all 11 GATE CSE subjects begins once this subject's 16 units complete a pass.
- No override was used for this run.

## Repository layout

```
index.html                                   master portal (test list + topic/subtopic archive)
README.md
design-tokens.css                            canonical :root token block (copied into every page, never linked)
discrete-mathematics/
  <unit-slug>/gate_dm_mock_<unit>_<date>.html current paper for that unit
  <unit-slug>/archive/                       superseded sets, content frozen, shell current
  question-bank/master_bank.json             append-only master question bank
```

## Syllabus coverage checklist

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Propositional Logic | `propositional-logic` | 50 | yes |
| 2 | Predicate & First-Order Logic | `predicate-logic` | 0 | — |
| 3 | Set Theory | `set-theory` | 0 | — |
| 4 | Relations | `relations` | 0 | — |
| 5 | Functions | `functions` | 0 | — |
| 6 | Mathematical Induction & Recursion | `induction-recursion` | 0 | — |
| 7 | Counting & Combinatorics | `combinatorics` | 0 | — |
| 8 | Recurrence Relations & Generating Functions | `recurrence-generating-functions` | 0 | — |
| 9 | Graph Theory Fundamentals | `graph-theory-fundamentals` | 0 | — |
| 10 | Graph Theory Advanced | `graph-theory-advanced` | 0 | — |
| 11 | Boolean Algebra & Switching Logic | `boolean-algebra` | 0 | — |
| 12 | Algebraic Structures | `algebraic-structures` | 0 | — |
| 13 | Lattices & Posets | `lattices-posets` | 0 | — |
| 14 | Number Theory | `number-theory` | 0 | — |
| 15 | Discrete Probability | `discrete-probability` | 0 | — |
| 16 | Logic & Proof Techniques | `proof-techniques` | 75 | yes |

## Provenance rules used in every test

1. A question is called an official GATE PYQ **only** when its year, paper and official answer key have been verified;
   those records live in `master_bank.json` under `verified_pyqs`.
2. Questions built on a verified PYQ pattern are tagged `GATE_PYQ_VARIATION` and are explicitly *not* official questions.
   Unit 1's single variation is built on the GATE CSE 2014 Set 1 Q53 pattern (formula true exactly when a stated number
   of p, q, r are TRUE; official key B).
3. Everything else is tagged `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS` and is practice material written for this series.
4. Historical questions are never deleted, never counted towards an active test, and are always filed under their
   `data-subtopic` slug.

## Answer key policy

The active mock test reveals nothing before submission. On submit, the file grades itself, marks the correct options,
unlocks the answer-key tab and shows a detailed solution for every question (concept, steps, final answer, why the other
options fail, common misconception, faster method, takeaway). Banked historical questions use a separate expand-on-demand
review interface.

## Known deviations (to be fixed in one pass across every paper)

- `6.4 No raw hex outside :root` is not yet met: the shipped shell uses literal hex values for a handful of tints and
  borders (`#f8fafc`, `#b9c6d2`, `#eaf2f8`, …). Because every paper must share one byte-identical shell, this can only
  be corrected by re-issuing all papers together, so it is recorded here rather than fixed in one file and breaking
  shell parity.
- `6.1` requires an archived paper to be rebuilt on the current shell. The archived Unit 1 Set 1 file is frozen exactly
  as it shipped; it already uses the current shell, so no rebuild was needed.
