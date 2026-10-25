# gate-cse-mocks — GATE CSE 2027 mock test series

Daily, self-contained mock tests for **GATE CSE 2027**, one unit at a time on the 16-unit rotation of Discrete
Mathematics. Every test is a single HTML file that opens in any browser, offline, in a TCS iON–style exam shell:
question palette with the standard status colours, a running countdown, radio MCQ, checkbox MSQ and typed NAT answers,
and no answer, option mark or hint visible until the test is submitted.

## Latest test

- **Unit 4 — Relations, Set 1 of 2**, 2026-10-26 → [`discrete-mathematics/relations/gate_dm_mock_4_2026-10-26.html`](discrete-mathematics/relations/gate_dm_mock_4_2026-10-26.html)
- 25 questions: 15 MCQ · 5 MSQ · 5 NAT · difficulty 10 easy / 10 medium / 5 hard · 60 minutes · 35 marks
- Subtopics: relation properties · equivalence relations & classes · partial orders & Hasse diagrams · lattices in
  posets · composition & transitive closure · counting relations
- Unit 3 closed at 50 banked questions, so the rotation advanced: (2 + 1) mod 16 = 3 → Unit 4. This is Unit 4's first
  paper; nothing was archived for this unit.

## Status

| Item | Value |
| --- | --- |
| Papers published | 10 (3 on Unit 16, 2 on Unit 1, 2 on Unit 2, 2 on Unit 3, 1 on Unit 4) |
| Units covered | 5 of 16 |
| Questions in master_bank.json | 250 (75 in Unit 16, 50 each in Units 1–3, 25 in Unit 4) |
| Verified official PYQs | 2 |
| Archived sets (earlier runs) | 5 (2 Unit 16, 1 Unit 1, 1 Unit 2, 1 Unit 3) |

## Rotation log

- **2026-10-26, Unit 3 → Unit 4.** `master_bank.json` showed Unit 3 at 50 banked questions — the 50-question cap — so
  the rotation advanced by the modulo rule: (2 + 1) mod 16 = 3 → Unit 4, Relations. Unit 4 now holds 25 questions,
  Set 1 of 2.
- The 25 questions are new: no id, stem, option set or numeric answer repeats an earlier paper. All six of Unit 4's
  subtopics are represented (relation properties 4, equivalence relations 5, partial orders 4, lattices 4, composition
  4, counting 4), and the difficulty split is 10 easy / 10 medium / 5 hard as in every paper.
- Every computational answer in this set was checked by brute force before shipping: 8 relations are both symmetric and
  antisymmetric on three elements; 512 relations and 64 symmetric relations on three elements; 12 antisymmetric
  relations on two; 4096 reflexive relations on four; 5 equivalence relations on four elements keep 1 and 2 together;
  the divisibility poset on {1,2,3,4,6,12} has 7 Hasse edges; the largest antichain of {1,…,30} has 15 elements; exactly
  4 elements of D(72) have a complement; and the transitive closures in Q2, Q13 and Q25 contain 6, 5 and 10 pairs.
  Option D of Q18 was corrected during verification — "24 covers 8" is *true* in that poset, so the false option is now
  "24 covers 6" (12 lies between).
- Filed only at `discrete-mathematics/relations/gate_dm_mock_4_2026-10-26.html`. Nothing was written at the repository
  root, and no unit folder holds two current papers — Unit 4 had no earlier paper to archive.
- Shell parity checked this run: the `<style>` block and the `<script>` block are byte-identical to the Unit 3 Set 2
  paper's, and the `:root` block still matches `design-tokens.css` exactly. No new literal hex value was introduced.
- The paper was exercised in a DOM harness before shipping: timer starts at 60:00, the answer key tab stays locked, no
  option mark or solution renders before submit, the palette reaches `ans` / `mrk` / `amr` / `cur` correctly, all 25
  answered correctly scores 35/35, and the key tab unlocks on submit.
- The Question Bank tab inside the paper now lists 225 solved questions — Unit 3's Set 2 has been superseded, so its 25
  join Set 1 there; Unit 4's own 25 are the active test and are not repeated in the tab. `index.html` holds all 250.
- No second pass has started; units 5–15 are still untouched.
- Subject selection: the series is still running Discrete Mathematics, the only subject with a question bank, until its
  16 units complete a pass. No override was used for this run.

- **2026-10-25, Unit 3 → Unit 3 (Set 2).** `master_bank.json` showed Unit 3 with 25 banked questions, current since the
  same date — under the 50-question cap and current for 0 days — so the rotation re-selected Unit 3 instead of advancing.
  25 + 25 = 50 closes Unit 3 at the cap; the next run for this subject advances to (2 + 1) mod 16 = 3 → Unit 4, Relations.
- Set 2 repeats no question from Set 1: the two sets share no id, no stem, no formula and no numeric answer. Each of the
  five subtopics carries five questions, and the difficulty split is 10 easy / 10 medium / 5 hard as in every paper.
- Set 2 contains no `GATE_PYQ_VARIATION` item — no set-theory PYQ has been verified against an official paper and key —
  and the About tab says so; every question is `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`.
- Filed only at `discrete-mathematics/set-theory/gate_dm_mock_3_2026-10-25.html`. Set 1 was moved into that unit's
  `archive/` as `..._run1.html` before the new file was written, so the unit folder never held two current papers and
  nothing was written at the repository root.
- Shell parity checked this run: the `<style>` block and the `<script>` block of Set 2 are byte-identical to Set 1's, and
  the `:root` block still matches `design-tokens.css` exactly. No new literal hex value was introduced.
- The paper was exercised in a DOM harness before shipping: timer starts at 60:00, the answer key stays locked, no option
  mark or solution renders before submit, palette states `na` / `ans` / `mrk` / `amr` all set correctly, all 25 answered
  correctly scores 35/35, and an MSQ with one option deselected scores zero for that question.
- No second pass has started; units 4–15 are still untouched.

- **2026-10-25, Unit 2 → Unit 3.** `master_bank.json` showed Unit 2 at 50 banked questions — the 50-question cap — so the
  rotation advanced by the modulo rule: (1 + 1) mod 16 = 2 → Unit 3, Set Theory. Unit 3 now holds 25 questions, Set 1 of 2.
- The 25 questions are new: no id, stem or option set repeats an earlier paper, and each of the five subtopics carries
  exactly five questions. The set contains no `GATE_PYQ_VARIATION` item — no set-theory PYQ has been verified against an
  official paper and key — and the About tab says so; every question is `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`.
- Filed only at `discrete-mathematics/set-theory/`. Nothing was written at the repository root, and Unit 2's paper stayed
  where it was as that unit's final paper, so no unit folder holds two current papers.
- Unit 3's paper is built from the same shell as every earlier paper: identical `<style>` block, identical `<script>`
  block, identical structural markup; only the payload, the meta strip, the header and the tab contents differ.
- No second pass has started; units 4–15 are still untouched.

- **2026-10-25, Unit 2 → Unit 2 (Set 2).** `master_bank.json` showed Unit 2 with 25 banked questions, current since the
  same date — under the 50-question cap and current for 0 days — so the rotation re-selected Unit 2 instead of
  advancing. 25 + 25 = 50 closes Unit 2 at the cap; the next run for this subject advances to
  (1 + 1) mod 16 = 2 → Unit 3, Set Theory.
- Set 2 repeats no question from Set 1: the two sets share no id, no formula and no stem. Its five subtopics carry five
  questions each, so no subtopic is under-represented. It contains no `GATE_PYQ_VARIATION` item, and the About tab says
  so: every question is `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`.
- The new paper is filed only at `discrete-mathematics/predicate-logic/`; the previous paper was moved into that unit's
  `archive/` as `..._run1.html` before the new file was written, so the unit folder never held two current papers.

- **2026-10-25, Unit 1 → Unit 2.** `master_bank.json` showed Unit 1 with 50 banked questions — at the 50-question cap —
  so the rotation advanced by the modulo rule: (0 + 1) mod 16 = 1 → Unit 2, Predicate & First-Order Logic.
- Unit 2 contains no `GATE_PYQ_VARIATION` item: no first-order-logic previous-year question has been verified against an
  official paper and key, so none is claimed.

- **2026-10-25, Unit 1 (second set).** Unit 1 was at 25 banked questions and current for 0 days, so the rotation
  re-selected it; 25 + 25 = 50 closed Unit 1 at the cap.

- **2026-10-25, Unit 16 → Unit 1.** Unit 16 had reached 75 banked questions, i.e. at or beyond the 50-question unit cap,
  so the rotation advanced by the modulo rule: (15 + 1) mod 16 = 0 → Unit 1.
- The unit for a run is chosen from `master_bank.json` (questions banked per unit, and the date of that unit's first
  paper), never from the calendar. Unit 16 stops at 75 because runs 1–3 were produced before the cap rule was applied;
  it is closed to new sets and will be revisited only after the other 15 units complete a pass.
- Subject selection: the series is running Discrete Mathematics, the only subject with a question bank. Subject
  rotation across all 11 GATE CSE subjects begins once this subject's 16 units complete a pass.
- No override was used for any run.

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
| 2 | Predicate & First-Order Logic | `predicate-logic` | 50 | yes |
| 3 | Set Theory | `set-theory` | 50 | yes |
| 4 | Relations | `relations` | 25 | yes |
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

- `6.4 No raw hex outside :root` is not yet met (the Unit 3 Set 2 paper carries exactly the same literal hex
  occurrences — 114 — as the shell it was built from, so nothing new was added): the shipped shell uses literal hex
  values for a handful of tints and borders (`#f8fafc`, `#b9c6d2`, `#eaf2f8`, …). Because every paper must share one
  byte-identical shell, this can only be corrected by re-issuing all papers together, so it is recorded here rather than
  fixed in one file and breaking shell parity.
- The `index.html` archive prints an answer line from `answer_display` and, for records created before 2026-10-25, a
  second identical line inside `solution_html`. The 50 Unit 2 records and the 25 Unit 1 Set 2 records carry it once; the
  older records still carry it twice. Normalising them is part of the same one-pass fix as the raw-hex item above.
- `6.1` requires an archived paper to be rebuilt on the current shell. The archived papers are frozen exactly as they
  shipped; they already use the current shell, so no rebuild was needed. Shell parity between the archived Unit 3 Set 1
  file and the new Unit 3 Set 2 file was checked this run: identical `<style>` block, identical `<script>` block,
  identical structural markup.
