# gate-cse-mocks — GATE CSE 2027 mock test series

Daily, self-contained mock tests for **GATE CSE 2027**, one unit at a time on a per-subject unit rotation.
Ten subjects are now in the series: Discrete Mathematics (16 units), Algorithms (7 units), Databases (5 units), Compiler Design (5 units), Operating Systems (6 units), Engineering Mathematics (5 units), Programming and Data Structures (7 units), Computer Networks (6 units), Theory of Computation (4 units) and Digital Logic (4 units). Every test is a single HTML file that opens in any browser, offline, in a TCS iON–style exam shell:
question palette with the standard status colours, a running countdown, radio MCQ, checkbox MSQ and typed NAT answers,
and no answer, option mark or hint visible until the test is submitted.

## Latest test

- **Databases · Unit 2 — SQL & Advanced Querying, Set 1 of 2**, 2026-10-26 → [`databases/sql-querying/gate_db_mock_2_2026-10-26.html`](databases/sql-querying/gate_db_mock_2_2026-10-26.html)
- 25 questions: 15 MCQ · 5 MSQ · 5 NAT · difficulty 10 easy / 10 medium / 5 hard · 60 minutes · 35 marks
- Subtopics: DDL, DML & DCL (5) · nested & correlated subqueries (5) · aggregates, GROUP BY & HAVING (5) · joins & outer joins (5) · views, triggers & constraints (5)
- Rotation: MODE A drew Databases at random from the 11 subjects (draw index 9 of 11). The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "2 of 2"}` with **50** questions banked on Unit 1 — exactly
  `UNIT_QUESTION_CAP = 50` — so step B3 failed on the cap and step B4 advanced one unit:
  `(0 + 1) mod 5` = Unit 2, SQL & Advanced Querying. This is Set 1 of 2; 25 questions are banked, so a second
  Databases run today would re-select Unit 2. No override was used and no second pass has started.
- Previous test: **Engineering Mathematics · Unit 1 — Linear Algebra: Matrices & Systems, Set 2 of 2**, 2026-10-26 → [`engineering-mathematics/linear-algebra-matrices/gate_em_mock_1_2026-10-26.html`](engineering-mathematics/linear-algebra-matrices/gate_em_mock_1_2026-10-26.html)

## Status

| Item | Value |
| --- | --- |
| Papers published | 31 (13 Discrete Mathematics, 2 Algorithms, 3 Databases, 2 Compiler Design, 3 Operating Systems, 2 Engineering Mathematics, 2 Programming and Data Structures, 1 Computer Networks, 2 Theory of Computation, 1 Digital Logic) |
| Units covered | 6 of 16 in Discrete Mathematics; 1 of 7 in Algorithms; 2 of 5 in Databases; 1 of 5 in Compiler Design; 2 of 6 in Operating Systems; 1 of 5 in Engineering Mathematics; 1 of 7 in Programming and Data Structures; 1 of 6 in Computer Networks; 1 of 4 in Theory of Computation; 1 of 4 in Digital Logic |
| Questions in the subject banks | 775 (325 Discrete Mathematics, 50 Algorithms, 75 Databases, 50 Compiler Design, 75 Operating Systems, 50 Engineering Mathematics, 50 Programming and Data Structures, 25 Computer Networks, 50 Theory of Computation, 25 Digital Logic) |
| Verified official PYQs | 6 (2 Discrete Mathematics, 1 Databases, 1 Operating Systems, 2 Digital Logic) |
| Archived sets (earlier runs) | 14 (7 Discrete Mathematics, 1 Algorithms, 1 Compiler Design, 1 Operating Systems, 1 Theory of Computation, 1 Programming and Data Structures, 1 Databases, 1 Engineering Mathematics) |

## Rotation log

- **2026-10-26, Databases → Unit 2 (SQL & Advanced Querying), Set 1 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (seed 1450085313,
  draw index 9 of 11) and it gave **Databases**. The bank read back `runs[-1] = {date 2026-10-26, unit 1, set "2 of
  2"}` with **50** questions banked on Unit 1. Since 50 >= `UNIT_QUESTION_CAP = 50`, step B3 failed on the cap and
  step B4 advanced exactly one unit: `(index_of(1) + 1) mod 5 = (0 + 1) mod 5 = 1` → **Unit 2, SQL & Advanced
  Querying**. This is Set 1 of 2 for the unit; a second Databases run today would re-select Unit 2, since 25 < 50 and
  the unit is current for 0 days. No override was used and no second pass has started for this subject.
- All 25 items are new: each question body was compared as an exact string against the 50 Unit 1 questions already in
  `master_bank.json`; none repeats. Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the 10 easy / 10 medium /
  5 hard split, and marks total 15 × 1 + 10 × 2 = 35. Coverage is 5 / 5 / 5 / 5 / 5 across DDL–DML–DCL, nested and
  correlated subqueries, aggregates with GROUP BY and HAVING, joins and outer joins, and views, triggers and
  constraints, so all five subtopics are represented.
- **Every answer that can be executed was recomputed by running it, not by hand.** The schema the questions refer to —
  `student(roll, name, dept, cgpa)`, `course(cid, title, credits)`, `enroll(roll, cid, marks)` with two ungraded
  enrollments — was built in SQLite and each query was run against it. Confirmed: the two-step DML trace leaves **4**
  students (rolls 1–4); `NOT EXISTS` returns only roll **6**, while the `NOT IN` over graded rows returns 5 and 6 and
  the `<> ALL` over ungraded rows returns 1, 3, 4, 6; `NOT IN` over a subquery containing a NULL returns **no rows**
  even for a value that matches nothing; the doubly nested correlated count returns **1** student (roll 4, whose
  CS101 mark 95 exceeds 91.5 and whose CS102 mark 80 exceeds 73); `COUNT(*)`/`COUNT(marks)` gives **(8, 6)**; the
  `HAVING COUNT(*) > 1` query returns **2** rows, CSE 8.8 and ECE 7.5; `AVG(marks)` for CS101 is **91.5** (the
  NULL-as-zero error gives 61); the left join returns **9** rows against 8 for the inner join; the Cartesian product
  is **18**; the anti-join returns **1**; the three-table CSE/credits join returns **6**; and the aggregate view
  yields **2** groups with n > 1. The verifier ran **38 checks, all passing**, including the structural ones
  (25 questions, 15/5/5, 10/10/5, 35 marks, 5 questions per subtopic, one answer per MCQ, at least two per MSQ).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4,
  (C) 4 and (D) 3, and the five MSQ answer sets are (B,C), (A,B,C), (A,B,D), (B,C,D) and (A,C). As first drafted
  12 of the 15 MCQs had their answer at (A), which would have let a candidate score about 28/35 by always choosing
  A; the option order of ten questions was rebalanced and every letter reference in the solutions remapped with the
  same transposition, so option text and solution still agree.
- The conceptual items were settled by the standard rather than by taste: `TRUNCATE` is DDL; `ON DELETE SET NULL`
  keeps the child rows and nulls the key; a `CHECK` rejects only FALSE, so UNKNOWN passes; the SQL standard permits
  several NULLs in a `UNIQUE` column (SQL Server is the known deviation); `= ANY` is `IN` and `> ALL` over an empty
  subquery is vacuously true; `NOT IN` and `NOT EXISTS` diverge exactly when a NULL can appear; `AVG` divides by
  `COUNT(col)`; an aggregate query without `GROUP BY` always returns one row; a predicate on the NULL-extended side in
  `WHERE` turns a left join into an inner join; and `CHECK` is a table constraint, not a view constraint.
- No `GATE_PYQ_VARIATION` item ships: no SQL previous-year question has been verified against an official paper and
  answer key for this unit, so none is claimed and `verified_pyqs` for this subject stays at the single Unit 1 entry.
  Every item is `STANDARD_TEXTBOOK` (13) or `ORIGINAL_SYNTHESIS` (12). The About tab and the Question Bank tab both
  say so.
- Unit 2 had no earlier paper, so nothing was archived: `databases/sql-querying/` holds exactly one current paper and
  the Databases Unit 1 paper was not touched. No root copy was written and no unit folder holds two current papers.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. After
  normalising the title, the header brand and sub-line, the candidate block, the tab labels, the meta strip,
  `#qhost`, the payload, the Question Bank pane and the About pane, the remaining bytes are **identical to the
  Databases Unit 1 Set 2 paper — 27 582 bytes on both sides**. The `<style>` block and the exam `<script>` are
  byte-for-byte identical (9 428 bytes), and the `:root` block (521 bytes) matches `design-tokens.css` and
  `index.html` exactly. No new literal hex value was introduced: the paper's hex values outside `:root` are a subset
  of the shell's.
- The paper was exercised in a jsdom harness before shipping (**64 checks, all passing**): nothing is revealed
  pre-submit (no solution text or `Answer:` string in the test pane, every `.sol` empty and hidden, no option mark, no
  mark text, key tab disabled, key pane empty, summary hidden, timer at 60:00); the palette reaches
  `na` / `ans` / `mrk` / `amr` / `cur` and falls back correctly on Clear Response; all 25 answered correctly scores
  **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette buttons and 25 key entries; a paper with one correct MCQ and
  one MSQ one option short scores **1 / 35** with 1 correct, 1 wrong and 23 skipped, confirming an MSQ pays nothing
  unless the exact option set is chosen; an MSQ with one extra wrong option also pays nothing; a blank paper scores
  **0 / 35** with 25 skipped; each tab shows exactly one view; every card carries `data-subject`, `data-unit`,
  `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`; and all five subtopics appear.
- The Question Bank tab inside the paper lists the **50** solved questions of Unit 1 under four subtopic accordions,
  every solution collapsed, and no active question is repeated there. `index.html` holds all **775** questions; the
  new Databases Unit 2 card reads "25 solved" with five subtopic pills and one "Practise Set 1 →" button, and its
  data block was updated in place — the record was appended so the newest paper renders first — with the derived
  header strings recomputed from it: 59 units, 775 solved, 31 sets published, 775 records, 255 subtopics. The portal
  harness (**37 checks, all passing**) confirms 17 test cards with the new one first, every `href` resolving, and
  every per-subject count matching its `master_bank.json`.
- **A pre-existing gap in `index.html` was repaired.** The Databases Unit 1 card listed only Set 1 in its launch row
  even though the bank holds the 50 questions of both sets, so Set 2 had no "Practise" button. Set 2 was added,
  bringing the card into line with the other subjects' cards.
- **One known deviation, not introduced by this run.** Two archived papers —
  `discrete-mathematics/proof-techniques/archive/gate_dm_mock_16_2026-10-25_run1.html` and `..._run2.html` — carry a
  476-byte `:root` block from an older shell with different token names (`--purple`, `--accent`, `--green-ink`) and a
  13 449-byte `<style>` block. Their content is frozen and their CSS references their own tokens, so swapping the
  token block alone would break them; rebuilding them on the current shell is a separate job. Every other paper in
  the repository, including this one, carries the canonical 521-byte block.
- No unit exceeds 50 questions: Databases Unit 1 closed at exactly 50, Unit 2 now stands at 25 of its 50, and the
  rotation will re-select Unit 2 on the next Databases run.

- **2026-10-26, Engineering Mathematics → Unit 1 (Linear Algebra: Matrices & Systems), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded
  `random.SystemRandom()` draw (seed 61724851, draw index 1 of 11) and it gave **Engineering Mathematics**. The bank
  read back `runs[-1] = {date 2026-10-26, unit 1, set "1 of 2"}` with **25** questions banked on Unit 1. Since 25 <
  `UNIT_QUESTION_CAP = 50` and the unit had been current for 0 days, step B3 regenerated Unit 1 rather than advancing.
  This is the second and final set for the unit: 25 + 25 = 50, exactly the cap, so no partial set was added and the
  unit ends at 50, not 60. The next Engineering Mathematics run advances to `(0 + 1) mod 5` = Unit 2, Linear Algebra:
  Eigenvalues & Vectors. No override was used and no second pass has started.
- All 25 items are new: no stem, option set or numeric answer is shared with Set 1 (checked by exact-string comparison
  against the 25 questions already in `master_bank.json`; the only repeated option texts are bare numerals such as
  `0` and `1`). Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the 10 easy / 10 medium / 5 hard split; marks
  total 15 × 1 + 10 × 2 = 35. Coverage is 7 / 7 / 6 / 5 across matrix operations, rank and nullity, systems of linear
  equations and Gauss elimination, so all four of the unit's subtopics are represented.
- **Every numeric answer was recomputed by an independent script, not by hand.** `sympy` confirmed: the determinant of
  `[[1,1,1],[1,2,3],[1,4,a]]` is `a − 7`, so uniqueness holds exactly for `a ≠ 7`; the system
  `x + 2y + z = 8`, `2x − y + 3z = 9`, `x + y − z = 0` has determinant `11` and the unique solution `(1, 2, 3)`, so
  `x + 2y + 3z = 14`; the rank of `[[1,2,3,4],[2,4,6,8],[1,0,1,0],[0,1,1,2]]` is `2`; `det(2A⁻¹)` with `det(A) = 3` on a
  `4 × 4` matrix is `16/3`; Cramer's rule on `2x + y = 5`, `x + 3y = 10` gives `x = 1`; and the `(1,2)` entry of the
  inverse of `[[2,1],[1,1]]` is `−1`. The counting items were checked by simulating the elimination: `4 + 3 + 2 + 1 = 10`
  row updates for a `5 × 5` matrix, against the `n³/3 ≈ 42` arithmetic operations those updates contain.
- The conceptual items were settled by proof rather than by taste: `A² = 0` with `A ≠ 0` on `3 × 3` forces rank 1
  because `col(A) ⊆ ker(A)` gives `2·rank ≤ 3`; `rank(AB) ≤ min(rank A, rank B)` is attained here because `A` of
  rank 3 with 3 columns is injective on the image of `B`; a `3 × 5` matrix of rank 3 has nullity 2, so a consistent
  `Ax = b` has a plane of solutions; and `nullity(Aᵀ) = 3 − 3 = 0`, which differs from `nullity(A) = 2`.
- No `GATE_PYQ_VARIATION` item ships: no linear-algebra previous-year question has been verified against an official
  paper and answer key, so none is claimed and `verified_pyqs` stays empty for this subject. Every item is
  `STANDARD_TEXTBOOK` (13) or `ORIGINAL_SYNTHESIS` (12). The About tab and the Question Bank tab both say so.
- The Set 1 paper moved to `engineering-mathematics/linear-algebra-matrices/archive/gate_em_mock_1_2026-10-26_run1.html`
  with its questions, options, answers, solutions and duration frozen — it is byte-for-byte the file that was current
  before this run (118 900 bytes). The new Set 2 paper (165 261 bytes) is filed only at
  `engineering-mathematics/linear-algebra-matrices/`; no root copy was written and the unit folder never held two
  current papers.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block (13 228 bytes) and the exam `<script>` (9 411 bytes) are byte-for-byte identical to the Operating
  Systems Unit 2 paper, and after normalising the title, the header brand and sub-line, the candidate block, the tab
  label, the metadata chips, `#qhost`, the payload, the Question Bank pane and the About pane, the remaining bytes
  differ only in the subject name — 27 795 against 27 789, the six extra characters of "Engineering Mathematics". The
  `:root` block (521 bytes) matches `design-tokens.css` and `index.html` exactly. The paper carries 84 literal hex
  occurrences outside `:root` against the reference shell's 86, so no new hex value was introduced.
- The paper was exercised in a jsdom harness before shipping (**68 checks, all passing**): nothing is revealed
  pre-submit (no solution text or `Answer:` string in the test pane, every `.sol` empty and hidden, no option mark, no
  mark text, key tab disabled, key pane empty, summary hidden, timer at 60:00); the palette reaches `ans` / `mrk` /
  `amr` / `cur` and falls back to `mrk` on Clear Response; all 25 answered correctly scores **35 / 35** with 25
  correct, 0 wrong, 25 `ok` palette buttons and 25 key entries; a paper with all five MSQs one option short scores
  **25 / 35** with 5 wrong, confirming an MSQ pays nothing unless the exact option set is chosen; a blank paper scores
  **0 / 35** with 25 skipped; each tab shows exactly one view; every card carries `data-subject`, `data-unit`,
  `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`; and all four subtopics appear.
- The Question Bank tab inside the paper lists the **25** solved questions of Set 1 under four subtopic accordions
  (8 / 7 / 6 / 4), every solution collapsed, and the active 25 are not repeated there. `index.html` holds all **750**
  questions; the Engineering Mathematics Unit 1 card now reads "50 solved" with subtopic pills 15 / 14 / 12 / 9 and
  both "Practise Set 1 →" (the archived paper) and "Practise Set 2 →". Its data block was updated in place — the
  Engineering Mathematics record moved to the end so the newest paper renders first — and its static header strings
  were recomputed from it: 10 subjects, 59 units, 750 solved, 30 sets published, 750 records, 255 subtopics. The
  portal harness (part of the same 68 checks) confirms 16 test cards with the new one first, "50 solved" and both
  practise buttons on the new card, 50 banked cards under its expander, every `href` resolving, and every per-subject
  count matching its `master_bank.json`.
- No unit exceeds 50 questions: Engineering Mathematics Unit 1 closes at exactly 50 with this set, and the rotation
  advances to Unit 2 on the next run for this subject.

- **2026-10-26, Databases → Unit 1 (ER Models & Relational Algebra), Set 2 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects and it gave **Databases**. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "1 of 2"}` with **25** questions banked on Unit 1. Since 25 <
  `UNIT_QUESTION_CAP = 50` and the unit had been current for 0 days, step B3 regenerated Unit 1 rather than
  advancing. This is the second and final set for the unit: 25 + 25 = 50, exactly the cap, so no partial set was
  added and the unit ends at 50, not 60. The next Databases run advances to `(0 + 1) mod 5` = Unit 2,
  SQL & Advanced Querying. No override was used and no second pass has started.
- All 25 items are new: no question text, option set or numeric answer is shared with Set 1 (DB-U1-Q01..Q25).
  Coverage is 6 / 6 / 8 / 5 across the four subtopics, so every subtopic is represented at least once.
- The previously current paper moved to
  `databases/er-relational-algebra/archive/gate_db_mock_1_2026-10-26_run1.html` with its content frozen. The new
  paper is filed at unit level only; no copy was written to the repository root.
- This set carries no GATE_PYQ_VARIATION. The one verified PYQ recorded for the unit (GATE CSE 2014, Set 3,
  Question 30, official key D) informed DB-U1-Q17 of Set 1; nothing in Set 2 is presented as an official question.
- Interface unchanged: the `<style>` block and the exam logic script are byte-identical to Set 1's, so shell
  parity holds without a rebuild of the archive.

- **2026-10-26, Programming and Data Structures → Unit 1 (C Programming Foundations), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded
  `random.SystemRandom().choice` (draw index 4 of 11) and it gave **Programming and Data Structures**. The bank read
  back `runs[-1] = {date 2026-10-26, unit 1, set "1 of 2"}` with **25** questions banked on Unit 1. Since 25 <
  `UNIT_QUESTION_CAP = 50` and the unit had been current for 0 days, step B3 regenerated Unit 1 rather than
  advancing. This is the second and final set for the unit: 25 + 25 = 50, exactly the cap, so no partial set was
  added and the unit ends at 50, not 60. The next Programming and Data Structures run advances to
  `(0 + 1) mod 7` = Unit 2, Pointers, Memory & Preprocessors. No override was used and no second pass has started.
- All 25 items are new: no question text, code listing, option set or numeric answer is shared with Set 1 (checked
  by exact-string comparison of each full question body — stem, code block and options — against the 25 questions
  already in `master_bank.json`; the shared stem "What does this program print?" appears in both sets, but the
  program under it never repeats). Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the 10 easy / 10 medium /
  5 hard split; marks total 15 × 1 + 10 × 2 = 35. Coverage is 7 / 6 / 6 / 6 across data types & operators, control
  structures, functions & parameter passing, and recursion & stack execution, so all four of the unit's subtopics
  are represented.
- **Every program-output answer was compiled and executed, not reasoned about by hand.** All twenty program listings
  were built into one C11 translation unit and run on a 32-bit-`int` target (zig cc 0.17.0, `-std=c11 -O0`). Confirmed
  outputs: `sizeof(1.0f + 1) = 4`; `017, 0x1F → 15 31`; `-1 < 1u → 0`; `x <<= 3; x |= 1; x ^= 5 → 12`;
  `(5>3)+(2==2)+(1!=1) → 2`; `3000000000u * 2u → 1705032704`; `while + continue → 12`; nested `break → 3`;
  the switch with `default` written first `→ 4`; `do-while → 4`; the stride-2 nested loop `→ 30`; the by-value
  array element `→ 2`; the static accumulator `→ "2 5"`; the re-pointed pointer parameter `→ 5`; the nested
  maximum `→ 9`; the call counter `→ 5`; the digit printer `→ "704"`; the odd-only recurrence `→ 16`; the binary
  bit counter `→ 3`; and a stack-depth probe on `f(16)` reporting a maximum depth of **5**. One item was **corrected
  by the compiler**: the signed/unsigned comparison in Q28 was drafted with the answer 1 and the run printed 0, so
  the option set and the solution were rewritten around 0 before the paper was built.
- The MSQ items were settled by the same rules rather than by taste: character constants have type `int` in C
  (`sizeof('a') == 4` confirmed by the same run), `011` is octal 9, a `do-while` body always runs once, `break`
  binds to the nearest loop or switch, `continue` in a `while` re-tests the condition, empty parentheses in a
  declaration are not a prototype, a static local is initialised once, and the standard fixes no recursion depth.
- No `GATE_PYQ_VARIATION` item ships: no C-programming previous-year question has been verified against an official
  paper and answer key, so none is claimed and `verified_pyqs` stays empty for this subject. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10). The About tab and the Question Bank tab both say so.
- The Set 1 paper moved to `programming-data-structures/c-programming-core/archive/gate_ds_mock_1_2026-10-26_run1.html`
  with its questions, options, answers, solutions and duration frozen — it is byte-for-byte the file that was current
  before this run (130 868 bytes). The new Set 2 paper is filed only at `programming-data-structures/c-programming-core/`;
  no root copy was written and the unit folder never held two current papers.
- Shell parity: the paper was produced by splicing new content into the shipped shell. After normalising the title,
  the brand and sub-line, the candidate block, the tab labels, the meta strip, `#qhost`, the payload, the Question
  Bank pane and the About pane, the remaining bytes are **identical to this unit's Set 1 and to the Algorithms
  Unit 1 paper — 27 568 bytes on all three sides**. The `<style>` block (13 243 bytes) and the exam `<script>`
  (9 428 bytes) are byte-for-byte identical, and the `:root` block (521 bytes) matches `design-tokens.css` and
  `index.html` exactly. No new literal hex value was introduced: the paper carries the same 34 literal hex
  occurrences outside `:root` as the shell (33 × `#5b6b7a`, 1 × `#1e8449`).
- The paper was exercised in a jsdom harness before shipping (**50 checks, all passing**): nothing is revealed
  pre-submit (no solution text or `Answer:` string in the test pane, every `.sol` empty and hidden, no option mark,
  no mark text, key tab disabled, key pane empty, summary hidden, timer at 60:00); the palette reaches
  `ans` / `na` / `mrk` / `amr` and falls back to `na` on Clear Response; Save & Next and Previous work from a card
  other than Question 1; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette
  buttons and 25 key entries; an MSQ with one option short pays nothing, giving **1 / 35** with 1 wrong and 23
  skipped; a blank paper scores **0 / 35** with 25 skipped; each tab shows exactly one view; and the Question Bank
  pane holds 25 cards with no active question repeated.
- The Question Bank tab inside the paper lists the **25** solved questions of Set 1 under four subtopic accordions
  (7 / 6 / 6 / 6), every solution collapsed; the active 25 are not repeated there. `index.html` holds all **700**
  questions; the Programming and Data Structures Unit 1 card now reads "50 solved" with subtopic pills
  14 / 12 / 12 / 12 and both "Practise Set 1 →" (the archived paper) and "Practise Set 2 →". Its data block was
  updated in place — the Programming and Data Structures record moved to the end so the newest paper renders first —
  and its static header strings were recomputed from it: 10 subjects, 59 units, 700 solved, 28 sets published,
  700 records, 255 subtopics. A second jsdom harness on the portal (**20 checks, all passing**) confirms 16 test
  cards with the new one first, 16 archive cards, "50 solved" and both practise buttons on the new card, 50 banked
  cards under the expander, every `href` resolving, and every per-subject count matching its `master_bank.json`.
- No unit exceeds 50 questions: Programming and Data Structures Unit 1 closes at exactly 50 with this set, and the
  rotation advances to Unit 2 on the next run for this subject.

- **2026-10-26, Algorithms → Unit 1 (Asymptotic Analysis & Recurrences), Set 2 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom().choice` (draw index 5 of
  11) and it gave **Algorithms**. The bank read back `runs[-1] = {date 2026-10-26, unit 1, set "1 of 2"}` with **25**
  questions banked on Unit 1. Since 25 < `UNIT_QUESTION_CAP = 50` and the unit had been current for 0 days, step B3
  regenerated Unit 1 rather than advancing. This is the second and final set for the unit: 25 + 25 = 50, exactly the
  cap, so no partial set was added and the unit ends at 50, not 60. The next Algorithms run advances to
  `(0 + 1) mod 7` = Unit 2, Divide and Conquer & Sorting. No override was used and no second pass has started.
- All 25 items are new: no stem, option set or numeric answer is shared with Set 1 (checked by exact-string
  comparison against the 25 questions already in `master_bank.json`). Composition is the standard 15 MCQ / 5 MSQ /
  5 NAT with the 10 easy / 10 medium / 5 hard split; marks total 15 × 1 + 10 × 2 = 35. Coverage is 8 / 6 / 7 / 4 across
  Big-O / Ω / Θ, the Master Theorem cases, the recursion-tree method and the substitution method, so all four of the
  unit's subtopics are represented.
- **Every answer was recomputed by an independent script, not by hand.** A checker unrolled each recurrence at a
  power-of-two argument and compared against the closed form: `T(n) = 2T(n/2) + n` with `T(1) = 1` gives **T(16) = 80**
  and **T(8) = 32**; `T(n) = 4T(n/2) + n²` gives **T(8) = 256**; `T(n) = T(n/3) + 1` gives `T(81) = 4 = log₃ 81`;
  `T(n) = T(n/2) + n` gives `T(n) = 2n − 2`, so the smallest integer `c` with `T(n) ≤ cn` is **2**; the leaf counts are
  **3³ = 27** at `n = 8` and **3⁴ = 81** at `n = 16`. The Master Theorem items were checked by computing
  `log_b a` numerically: `4T(n/2) + n → Θ(n²)`, `8T(n/2) + n² log n → Θ(n³)`, `7T(n/2) + n² → Θ(n^{log₂ 7})`
  (`log₂ 7 ≈ 2.807`), `9T(n/3) + n² → Θ(n² log n)` so `k = 2`, and `2T(n/2) + n/log₂ n` has no applicable case.
  The growth-order item was settled on the base-2 logarithms (`n!` at `Θ(n log n)` beats `(log₂ n)ⁿ` at
  `n log₂ log₂ n`); the identity `n^{1 + 1/log₂ n} = 2n` was checked numerically at `n = 2 … 2²⁰`; and
  `n^{0.1}/log₂ n → ∞`, `√n/(n/log₂ n) → 0`, `3ⁿ/2ⁿ → ∞`, `log₂ 3 < 1.6` were each confirmed by ratio.
- No `GATE_PYQ_VARIATION` item ships: no asymptotic-analysis or recurrence previous-year question has been verified
  against an official paper and answer key, so none is claimed and `verified_pyqs` stays empty for this subject. Every
  item is `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10). The About tab and the Question Bank tab both say so.
- The Set 1 paper moved to `algorithms/asymptotic-analysis/archive/gate_algo_mock_1_2026-10-26_run1.html` with its
  questions, options, answers, solutions and duration frozen — it is byte-for-byte the file that was current before
  this run. The new Set 2 paper is filed only at `algorithms/asymptotic-analysis/`; no root copy was written and the
  unit folder never held two current papers.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. After
  normalising the title, the header brand and sub-line, the candidate block, the metadata chips, `#qhost`, the
  payload, the Question Bank pane and the About pane, the remaining bytes are identical to the Operating Systems
  Unit 2 paper and to this unit's archived Set 1 — **27 917 bytes on all three sides**. The `<style>` block
  (13 243 bytes) and the exam `<script>` (9 428 bytes) are byte-for-byte identical, and the `:root` block (521 bytes)
  matches `design-tokens.css` and `index.html` exactly. No new literal hex value was introduced: the paper carries the
  same 115 literal hex occurrences outside `:root` as the shell.
- The paper was exercised in a jsdom harness before shipping (**22 checks, all passing**): nothing is revealed
  pre-submit (no solution text or `Answer:` string in the test pane, every `.sol` empty, no option mark, no mark text,
  key tab disabled, key pane empty, summary hidden, timer at 60:00); the palette reaches `na` / `ans` / `amr` and falls
  back to `mrk` on Clear Response; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25 `ok`
  palette buttons and 25 key entries; a paper with one correct MCQ and one partially-selected MSQ scores **1 / 35**
  with 1 wrong and 23 skipped, confirming an MSQ pays nothing unless the exact option set is chosen; a blank paper
  scores **0 / 35** with 25 skipped; each tab shows exactly one view; and every card carries `data-subject`,
  `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`.
- The Question Bank tab inside the paper lists the **25** solved questions of Set 1 — the active 25 are not repeated
  there — under four subtopic accordions (7 / 6 / 7 / 5), with every solution collapsed. `index.html` holds all **675**
  questions, and the Algorithms Unit 1 card now carries "50 solved", the four subtopic pill counts and both
  "Practise Set 1 →" (the archived paper) and "Practise Set 2 →". Its data block was updated in place — the Algorithms
  record moved to the end so the newest paper renders first — and its static header strings were recomputed from it:
  10 subjects, 59 units, 675 solved, 27 sets published, 675 records, 255 subtopics. A second jsdom harness on the
  portal (**14 checks, all passing**) confirms 16 test cards with the new one first, 16 archive cards, "50 solved" on
  the Algorithms card, both practise buttons, 675 banked cards, and that every `href` resolves.
- **A pre-existing defect in `index.html` was repaired.** The 25 Compiler Design Set-2 records (`CD-U1-Q26`–`Q50`) had
  been written without a `subject` field, so the portal's `subj()` fallback counted them against Discrete Mathematics
  Unit 1: DM Unit 1 read "75 solved" and Compiler Design Unit 1 read "25 solved" while both banks actually hold 50.
  Those 25 records now carry `"subject": "compiler-design"`, identified by their `CD-` id prefix. Counts after the
  repair: DM 325, Compiler Design 50, Algorithms 50, total 675 — matching the subject banks exactly.
- No unit exceeds 50 questions: Algorithms Unit 1 closes at exactly 50 with this set, and the rotation advances to
  Unit 2 on the next Algorithms run.

- **2026-10-26, Theory of Computation → Unit 1 (Regular Languages & Finite Automata), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.Random` draw (seed 823142602,
  draw index 6 of 11) and it gave **Theory of Computation**. The bank read back `runs[-1] = {date 2026-10-26, unit 1,
  set "Set 1 of 2"}` with 25 questions banked on Unit 1. Since 25 < `UNIT_QUESTION_CAP = 50` and the unit had been
  current for 0 days, step B3 regenerated Unit 1 rather than advancing. This is the second and final set for the unit:
  25 + 25 = 50, exactly the cap, so no partial set was added and the unit ends at 50, not 60. The next Theory of
  Computation run advances to `(0 + 1) mod 4` = Unit 2, Grammars & Context-Free Languages. No override was used and no
  second pass has started for this subject.
- All 25 items are new: no stem, option set or numeric answer is shared with Set 1 (checked by exact-string comparison
  against the 25 questions already in `master_bank.json`). Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the
  10 easy / 10 medium / 5 hard split; marks total 15 × 1 + 10 × 2 = 35. Coverage is 7 / 6 / 6 / 6 across DFA
  construction & minimisation, NFA to DFA by subset construction, regular expressions and the pumping lemma, so all
  four of the unit's subtopics are represented.
- **Every answer was recomputed by an independent script, not by hand.** A checker built each automaton, minimised it
  by reachability pruning plus partition refinement, ran a brute-force enumeration of the language, and evaluated a
  formal-regex engine written for the purpose. Confirmed: minimal complete DFA for "ends in `ab`" = **3** states; for
  "contains `aba`" = **4**; for "value ≡ 2 (mod 3)" = **3**; the 6-state table of Q13 has all six states reachable and
  exactly one equivalent pair (`B ≡ E`), giving **5**; the 4-state NFA of Q14 recognises "the third symbol from the
  right is 1", whose minimal DFA has **8** states, and its subset construction produces exactly those 8 reachable
  subsets; the 3-state NFA of Q23 yields **4** reachable subset states; length-5 strings over `{a,b}` with no `aa` =
  **13**; length-6 strings with an even number of `a`'s = **32**. The regex and MSQ options were settled by exhaustive
  comparison over all strings up to length 9: `(a*ba*ba*)*a*` equals "even number of `b`'s" while `(a*b)*`,
  `(ba*ba*)*` and `(a*ba*b)*` do not; `(ab)*a = a(ba)*` and `(a+b)* = (a*b*)*` hold; `(a*b)* ≠ a*b*` (separated by
  `ba`) and `(ab+ba)*` is not "equal numbers of `a` and `b`" (separated by `aabb`). All 28 checks passed.
- No `GATE_PYQ_VARIATION` item ships: no regular-language or finite-automata previous-year question has been verified
  against an official paper and answer key, so none is claimed and `verified_pyqs` stays empty for this subject. Every
  item is `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10). The About tab and the Question Bank tab both say so.
- The Set 1 paper moved to `theory-of-computation/regular-languages-fa/archive/gate_toc_mock_1_2026-10-26_run1.html`
  with its questions, options, answers, solutions and duration frozen. Its header sub-line read "Unit 1 — Asymptotic
  Analysis & Recurrences", a copy-paste from the Algorithms paper; that one string was repaired to name Regular
  Languages & Finite Automata, as was done for the Compiler Design paper previously. Nothing else in the archive was
  touched. The new Set 2 paper is filed only at `theory-of-computation/regular-languages-fa/`; no root copy was
  written and the unit folder never held two current papers.
- **A stale count in `index.html` was repaired.** The portal's data block was 25 records short: the whole
  Digital Logic Unit 1 set (25 questions) had never been added, so the dashboard held 625 of the 650 records in the
  subject banks and the Digital Logic card was missing from the archive view. Those 25 records were appended in the
  index record shape, and the id sets now match exactly — 650 banked ids, 650 dashboard ids, no difference in either
  direction. The three derived strings that count them were recomputed in the same edit.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. After
  normalising the title, the header brand and sub-line, the candidate block, the metadata chips, `#qhost`, the
  payload, the Question Bank pane and the About pane, the remaining bytes are identical to the Operating Systems
  Unit 2 paper — **27 807 bytes on both**. The `<style>` block (13 243 bytes) and the exam `<script>` (9 428 bytes)
  are byte-for-byte identical, and the `:root` block (521 bytes) matches `design-tokens.css` and `index.html` exactly.
  No new literal hex value was introduced: the automaton tables use the monospaced `var(--bg)` / `var(--line)` block
  the Set 1 paper already used, not a `<table>` (the shell has no table styling).
- The paper was exercised in a jsdom harness before shipping (**52 checks, all passing**): nothing is revealed
  pre-submit (no solution text, no option mark, no key content, base64 payload, key tab disabled, summary hidden,
  timer at 60:00); all 25 answered correctly scores **35 / 35** with 25 correct and the key unlocks with 25 solutions;
  a mixed paper (1 correct MCQ, 1 wrong MCQ, 1 partially-selected MSQ, 1 correct NAT) scores **3 / 35** with 2
  correct, 2 wrong and 21 unattempted, confirming an MSQ pays nothing unless the exact option set is chosen; dropping
  a single correct option from one MSQ costs exactly 2 marks (**33 / 35**); a blank paper scores **0 / 35** with 25
  skipped; the palette reaches `na` / `ans` / `mrk` / `amr` / `cur` and falls back to `mrk` on Clear Response, then
  switches to `ok` / `bad` / `skip` after submit; each tab shows exactly one view; and every card carries
  `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`.
- The Question Bank tab inside the paper lists the **25** solved questions of Set 1 — the active 25 are not repeated
  there — under four subtopic accordions (7 / 6 / 6 / 6), with every solution collapsed. `index.html` holds all **650**
  questions, and the Theory of Computation Unit 1 card now carries "50 solved", the four subtopic pill counts and both
  "Practise Set 1 →" (the archived paper, where those questions live) and "Practise Set 2 →". Its data block was
  updated in place and its six static header strings were recomputed from it: 10 subjects, 59 units, 650 solved,
  26 sets published, 650 records, 255 subtopics. A second jsdom harness on the portal (**25 checks, all passing**)
  confirms 16 test cards with the new one first, 50 banked cards with unique ids `TOC-U1-Q01`–`Q50`, two practise
  buttons, and that every `href` resolves.

- **2026-10-26, Digital Logic → Unit 1 (Number Systems & Representation), Set 1 of 2.** MODE A: the subject was drawn
  at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom().choice` (draw seed 1426181344, index 2
  of 11) and the draw gave **Digital Logic**, a subject with no bank yet. `digital-logic/question-bank/master_bank.json`
  did not exist, so there was no `runs[]` to read and step B6 applied: `(2026-10-26 − 2026-10-26) mod 4 = 0` →
  **Unit 1, `number-systems`**. This is Set 1 of 2; 25 questions are now banked, so a second Digital Logic run today
  would re-select Unit 1 (25 < `UNIT_QUESTION_CAP = 50`, unit current for 0 days). No override was used and no second
  pass has started.
- Coverage is 8 / 7 / 5 / 5 across base conversions, one's and two's complement, IEEE 754 and range & overflow, so all
  four of the unit's subtopics are represented. Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the 10 easy /
  10 medium / 5 hard split; marks total 15 × 1 + 10 × 2 = 35.
- **Every numeric answer was recomputed by script, not by hand.** A checker rebuilt each answer independently: octal and
  base-7 expansions (`(756)₈` = 494 = `111101110₂`; `(2026)₇` = 706), two's complement patterns via modular arithmetic
  (`−21` in 12 bits = `1111 1110 1011`; `1111 0000` = −16; negating `1000 0000` returns `1000 0000`), one's complement
  addition with the end-around carry (`(−5)+(−3)` = −8), unsigned wraparound (200 + 100 → 44 with carry 1), 16-bit
  signed wraparound (30000 + 10000 → −25536), and IEEE 754 decoding with `struct.unpack` (`0x3F000000` = 0.5,
  `0x41A00000` = 20, smallest subnormal = 2<sup>−149</sup>). The smallest-width questions were solved by search
  (11 bits for ±1000; 10 bits for 1000 as unsigned). All 23 machine-checkable items passed.
- Two items are `GATE_PYQ_VARIATION` and carry verified provenance in `master_bank.json`: `DL-U1-Q03` from **GATE CSE
  2019, Question 4** (official key option C, the 16-bit pattern for −28) and `DL-U1-Q04` from **GATE CSE 2016, Set 1,
  Question 7** (official key −11). Both attributions were confirmed against two independent public PYQ collections in
  this run. No other item claims official status.
- Shell parity: the paper was spliced into the shipped shell, not re-typed. After normalising the title, the header
  brand/sub/candidate lines, the metadata chips, `#qhost`, the payload, the Question Bank pane and the About pane, the
  remaining bytes are identical to the Computer Networks Unit 1 paper — **27 840 bytes on both**. The `<style>` block and
  the exam `<script>` are byte-for-byte identical, and the `:root` token block matches `design-tokens.css`.
- Every card carries `data-subject="digital-logic"`, `data-unit="number-systems"`, `data-unit-number="1"`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`. Unit 1 had no earlier paper, so nothing was
  archived: the unit folder holds exactly one current paper, and no root copy was written.

- **2026-10-26, Theory of Computation → Unit 1 (Regular Languages & Finite Automata), Set 1 of 2.** MODE A: the
  subject was drawn at random from the 11 GATE CSE subjects with an unseeded `random.choice` this run (the two earlier
  runs today used a date-seeded draw, which both returned Operating Systems); the draw gave **Theory of Computation**, a
  subject with no bank yet. `theory-of-computation/question-bank/master_bank.json` did not exist, so there was no
  `runs[]` to read and step B6 applied: `(2026-10-26 − 2026-10-26) mod 4 = 0` → **Unit 1, `regular-languages-fa`**.
  This is Set 1 of 2; 25 questions are banked, so a second Theory of Computation run today would re-select Unit 1
  (25 < `UNIT_QUESTION_CAP = 50`, unit current for 0 days). No override was used and no second pass has started.
- Coverage is 7 / 6 / 6 / 6 across DFA construction & minimisation, NFA to DFA (subset construction), regular
  expressions, and the pumping lemma, so all four of the unit's subtopics are represented. Composition is the standard
  15 MCQ / 5 MSQ / 5 NAT with the 10 easy / 10 medium / 5 hard split; marks total 15 × 1 + 10 × 2 = 35.
- **Every numerical and state-count answer was recomputed by an independent simulator, not by hand.** A script built
  each automaton, ran the language against brute-force enumeration, then minimised it by reachability pruning plus table
  filling. Confirmed: minimal complete DFA for even number of `a`'s = **2** states; for `#0 ≡ 0 (mod 3) ∧ #1 ≡ 0 (mod 2)`
  = **6**; for binary strings divisible by 5 = **5**; for `{a^n b^m : n ≥ 1, m ≥ 2}` = **5**; for `a(a+b)*` = **3**;
  for the 5-state DFA of Question 12 = **4** (states `A` and `E` merge, and the language really is "even `0`'s and even
  `1`'s"); the 3-state NFA of Question 23 yields exactly **4** reachable subset states; the 4-state NFA of Question 13
  yields **8** reachable subsets that survive minimisation; length-4 strings containing `ab` = **11** (16 total minus the
  5 strings of the form `b*a*`); and the regex `b*(ab*ab*)*ab*` matches exactly the odd-`a` strings for all lengths ≤ 6.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. After
  normalising the title, the header brand/sub lines, the candidate block, the metadata chips, `#qhost`, the payload, the
  Question Bank pane and the About pane, the remaining bytes are identical to the Algorithms Unit 1 paper — **27 933
  bytes on both**. The `<style>` block and the exam `<script>` are byte-for-byte identical, and the `:root` token block
  matches `design-tokens.css`.
- Every card carries `data-subject="theory-of-computation"`, `data-unit="regular-languages-fa"`, `data-unit-number="1"`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`. Unit 1 had no earlier paper, so nothing was
  archived: the unit folder holds exactly one current paper, and no root copy was written.

- **2026-10-26, Operating Systems → Unit 2 (Inter-Process Communication & Synchronization), Set 1 of 2.** MODE A: the
  subject came from the same date-seeded draw as the earlier run today (seed 852190219, the SHA-256 of
  `2026-10-26-gate-cse-mock` reduced modulo 10⁹) and again gave Operating Systems. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "2 of 2"}` with **50** questions banked on Unit 1, which equals
  `UNIT_QUESTION_CAP = 50`. Step B3 therefore failed on the cap, and step B4 advanced exactly one unit:
  `(index_of(1) + 1) mod 6 = (0 + 1) mod 6 = 1` → Unit 2. This is Set 1 of 2 for Unit 2; a second Operating Systems run
  today would re-select Unit 2, since 25 < 50 and the unit is current for 0 days. No override was used and no second
  pass has started for this subject.
- All 25 items are new. Each stem was compared as an exact string against all 50 Unit 1 questions already in
  `master_bank.json`; none repeats. Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the 10 easy / 10 medium /
  5 hard split, and coverage is 5 / 6 / 8 / 6 across critical section & Peterson's solution, hardware primitives,
  semaphores, and the classic problems, so all four of the unit's subtopics are represented.
- **Every numerical answer was recomputed by an independent simulator, not by hand.** Confirmed: the semaphore trace
  `P,P,V,P,P,P,V,V,P` from 3 ends at **0**; 5 with seven P and four V ends at **2**; a capacity-9 buffer with `full` = 4
  admits **5** more inserts; the swap-based lock leaves `true` in the caller's `key` on **2** of three acquisitions
  after the first is never released; and the asymmetric dining-philosophers rule admits at most ⌊7/2⌋ = **3**
  simultaneous eaters. Each value was produced by a script that models the primitive's semantics directly.
- Shell parity: the paper was produced by splicing new content into the shipped Operating Systems shell rather than
  re-typing it. After normalising the title, the header sub-line, the metadata chips, `#qhost`, the payload, the
  Question Bank pane and the About pane, the remaining bytes are identical to the Unit 1 Set 2 paper — **27 756 bytes
  on both**. The `<style>` block (13 228 bytes) and the exam `<script>` (9 400 bytes) are byte-for-byte identical, and
  the `:root` token block matches `design-tokens.css`.
- Unit 2 had no earlier paper, so nothing was archived: the unit folder holds exactly one current paper. The Unit 1
  paper was not touched. No root copy was written.

- **2026-10-26, Operating Systems → Unit 1 (Process Management & CPU Scheduling), Set 2 of 2.** MODE A: the subject was
  drawn at random from the 11 GATE CSE subjects with a seeded draw for this date (seed 852190219, the SHA-256 of
  `2026-10-26-gate-cse-mock` reduced modulo 10⁹) and came out Operating Systems. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "1 of 2"}` with 25 questions on Unit 1. Since 25 < `UNIT_QUESTION_CAP = 50`
  and the unit had been current for 0 days, step B3 regenerated Unit 1 rather than advancing. This is the second and
  final set for the unit: 25 + 25 = 50, exactly the cap, so no partial set was added and the unit ends at 50, not 60.
  The next Operating Systems run will advance to `(0 + 1) mod 6` = Unit 2, Inter-Process Communication &
  Synchronization. No override was used and no second pass has started for this subject.
- All 25 items are new: no stem, option set, table or numeric answer is shared with Set 1 (checked by exact-string
  comparison against the 25 questions already in `master_bank.json`). Composition is the standard 15 MCQ / 5 MSQ /
  5 NAT with the 10 easy / 10 medium / 5 hard split, and coverage is 7 / 6 / 6 / 6 across process states & PCB,
  threads, preemptive vs non-preemptive scheduling, and FCFS/SJF/SRTF/RR/priority, so every one of the unit's four
  subtopics is represented.
- The Set 1 paper moved to `operating-systems/process-scheduling/archive/gate_os_mock_1_2026-10-26_run1.html` with its
  questions, options, answers, solutions and duration frozen (137 422 bytes, byte-for-byte the file that was current
  before this run). The new Set 2 paper is filed only at `operating-systems/process-scheduling/`; no root copy was
  written and the unit folder never held two current papers.
- **Every scheduling answer was recomputed by an independent step-by-step simulator, not by hand.** Confirmed:
  3 × 12 ms of work with two 0.4 ms switches gives **36.8 ms** elapsed; SRTF on (0,9) (2,3) (4,6) (8,2) preempts
  **twice** (P1 at t = 2 and P3 at t = 8) with completion times 20/5/13/10; preemptive priority on
  (0,6,pri 3) (2,4,pri 1) (4,2,pri 2) finishes P1 at **12 ms** because P3's priority 2 cannot displace P2's 1; the
  preemptive-priority average waiting time on (0,8,4) (1,4,1) (2,9,3) (3,5,2) is **7 ms**; FCFS on (0,5) (1,3) (2,8)
  (4,2) gives an average turnaround of **10 ms** and non-preemptive SJF on the same table an average waiting time of
  **3.75 ms**; round robin with q = 4 on (0,6) (1,3) (2,7) gives an average turnaround of **11 ms**; round robin with
  q = 2 on (0,5) (1,4) (2,2) (3,3) gives **9.75 ms**; and the 20 ms process in the two-level feedback queue runs
  **once** in the 8 ms top queue. Each value was produced by a script that walks the timeline one quantum or one
  arrival at a time, and the round-robin figures were re-derived by hand from the same trace.
- Shell parity: the paper was produced by splicing a new payload into the shipped shell rather than re-typing it. After
  normalising the title, the header brand and sub-line, the candidate block, the metadata chips, `#qhost`, the payload,
  the Question Bank pane and the About pane, the remaining bytes are identical to the Compiler Design, Computer
  Networks and Programming and Data Structures papers and to this unit's archived Set 1 — **27 771 bytes on all five
  sides**. The `:root` block still matches `design-tokens.css` and `index.html` byte for byte (521 bytes). The payload
  uses `var(--muted)`, `var(--line)` and `var(--bg)` instead of the literal `#5b6b7a` the older cards carried, so this
  paper has **84 literal hex occurrences outside `:root` against the shell's 114** — no new hex value was introduced,
  and the count fell.
- The paper was exercised in a jsdom harness before shipping (**221 checks, all passing**): nothing is revealed
  pre-submit (no solution text in the test or key pane, no option mark, no key content, base64 payload, key tab
  disabled, summary hidden, timer at 60:00); all 25 answered correctly scores **35 / 35** with 25 correct and the key
  unlocks with 25 solutions; a mixed paper (1 correct MCQ, 1 wrong MCQ, 1 partially-selected MSQ, 1 correct NAT)
  scores **3 / 35** with 21 unattempted, confirming an MSQ pays nothing unless the exact option set is chosen; the
  palette reaches `mrk` / `amr` and falls back to `mrk` on Clear Response, then switches to `ok` / `bad` / `skip` after
  submit; each tab shows exactly one view; and every card carries `data-subject`, `data-unit`, `data-unit-number`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`.
- The Question Bank tab inside the paper lists the **25** solved questions of Set 1 — the active 25 are not repeated
  there — under four subtopic accordions, with every solution collapsed. `index.html` holds all **550** questions and
  the Operating Systems Unit 1 card now carries "50 solved", the four subtopic pill counts (14 / 12 / 11 / 13) and both
  "Practise Set 1 →" and "Practise Set 2 →". Its data block was updated in place, and the six static header strings
  were recomputed from it: 8 subjects, 57 units, 550 solved, 13 sets, 550 records, 247 subtopics. Every `href` in the
  portal still resolves.
- Operating Systems still contains no new `GATE_PYQ_VARIATION` item: no further scheduling previous-year question has
  been verified against an official paper and key in this run, so none is claimed. The subject's one verified PYQ
  (GATE CSE 2021, Set 1, Q25) remains attached to `OS-U1-Q21` in Set 1, now archived. Every Set 2 item is
  `STANDARD_TEXTBOOK` (13) or `ORIGINAL_SYNTHESIS` (12).

- **2026-10-26, Computer Networks → Unit 1 (Layering, Physical & Framing).** MODE A: the subject was drawn at random
  from the 11 GATE CSE subjects and came out Computer Networks. No bank existed for it, so step B6's fallback applied:
  `(2026-10-26 − 2026-10-26) mod 6 = 0` → Unit 1. No override was used and no second pass has started. Unit 1 now
  holds 25 of its 50 questions, so the next run for this subject re-selects Unit 1 for Set 2 of 2.
- 25 questions, all new: 15 MCQ / 5 MSQ / 5 NAT, difficulty 10 easy / 10 medium / 5 hard. Coverage is 7 / 6 / 6 / 6
  across OSI & TCP/IP models, transmission delays & bandwidth-delay product, framing (bit & byte stuffing) and error
  detection (CRC, checksum, Hamming), so every one of the unit's four subtopics is represented.
- Filed only at `computer-networks/network-fundamentals-framing/gate_cn_mock_1_2026-10-26.html`. No earlier paper
  existed for this unit, so nothing was archived and no root copy was written.
- **Every numeric answer was recomputed in code before shipping**, not by hand: the encapsulated frame is
  600 + 20 + 20 + 14 + 4 = **658** bytes; the bandwidth-delay product of 100 Mbps × 20 ms is 2 × 10⁶ bits =
  250 000 bytes = **250 kB**; 3000 km at 3 × 10⁸ m/s is **10 ms**; three store-and-forward hops of 1 Mbps for a
  1000-byte packet are **24 ms**; the stuffed payload `41 7E 7D 42 7E 43` grows to **9** bytes
  (`41 7D5E 7D5D 42 7D5E 43`); bit stuffing `011111101111101111110` inserts **3** zeros; the stuffed form of
  `01111101111110` is `0111110011111010` (16 bits); the Hamming distance of 1011101 and 1001001 is **2**; 16 data
  bits need **5** parity bits (16 + 5 + 1 ≤ 32); the Internet checksum of 0x1234, 0x5678, 0x9ABC is **0xFC96**
  (0x68AC + 0x9ABC = 0x10368 → end-around carry 0x0369 → complement); and the CRC remainder for message 1101 with
  generator 1001 is `100`, i.e. **4**. Each was checked by an independent script, and the byte-stuffing and CRC values
  by direct simulation of the protocol rule.
- Shell parity: the paper was produced by splicing a new payload into the shipped shell rather than re-typing it. The
  `<style>` block (13 243 bytes) and the closing `<script>` block (9 445 bytes) are byte-identical to
  `operating-systems/process-scheduling/gate_os_mock_1_2026-10-26.html`, the `:root` block still matches
  `design-tokens.css` and `index.html` byte for byte, and the document's element nesting matches the template's
  exactly. No new literal hex value was introduced.
- The paper was exercised in a DOM harness before shipping (28 checks, all passing): nothing is revealed pre-submit
  (no solution text, no option mark, no key content, base64 payload, key tab disabled, summary hidden, timer at
  60:00); all 25 answered correctly scores **35/35** with 25 correct and the key unlocks with 25 solutions; a mixed
  paper (1 correct MCQ, 1 wrong MCQ, 1 exactly-selected MSQ, 1 partially-selected MSQ, 1 correct NAT, 1 wrong NAT)
  scores **5/35** with 3 correct, 3 wrong and 19 unattempted — confirming an MSQ pays nothing unless the exact option
  set is chosen; the palette reaches `na` / `ans` / `mrk` / `amr` / `cur` and switches to `ok` / `bad` / `skip` after
  submit; and every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`.
- A new subject folder and bank were created: `computer-networks/question-bank/master_bank.json` holds 25 questions on
  Unit 1 with all seven `data-*` attributes represented in its records. `index.html` gained the six Computer Networks
  units, one test card and the 25 banked questions, and its data block now holds 13 tests, 57 units and 525 questions.
  Its static header strings were recomputed from the data block in the same edit: 8 subjects, 57 units, 525 solved,
  13 sets published, 525 records, 247 subtopics. Every `href` in the portal still resolves.
- Computer Networks contains no `GATE_PYQ_VARIATION` item: no layering, framing or error-detection previous-year
  question has been verified against an official paper and key in this run, so none is claimed. Every item is
  `STANDARD_TEXTBOOK` (11) or `ORIGINAL_SYNTHESIS` (14).

- **2026-10-26, Programming and Data Structures → Unit 1 (C Programming Foundations).** MODE A: the subject was drawn
  at random from the 11 GATE CSE subjects and came out Programming and Data Structures. No bank existed for it, so step
  B6's fallback applied: `(2026-10-26 − 2026-10-26) mod 7 = 0` → Unit 1. No override was used and no second pass has
  started. Unit 1 now holds 25 of its 50 questions, so the next run for this subject re-selects Unit 1 for Set 2 of 2.
- 25 questions, all new: 15 MCQ / 5 MSQ / 5 NAT, difficulty 10 easy / 10 medium / 5 hard. Coverage is 7 / 6 / 6 / 6
  across data types & operators, control structures, functions & parameter passing, and recursion & stack execution,
  so every one of the unit's four subtopics is represented.
- Filed only at `programming-data-structures/c-programming-core/gate_ds_mock_1_2026-10-26.html`. No earlier paper
  existed for this unit, so nothing was archived and no root copy was written.
- **Every answer in this set was produced by compiling and running the snippet**, not by hand. No C compiler was
  installed in the build environment, so a Zig-based C compiler (`ziglang` from PyPI, `zig cc -std=c99`) was used as
  the driver and each program was executed; the printed values recorded in the paper are those program outputs.
  Confirmed: `7/2*2` and `-7/2` give `6 -3`; `sizeof('A')` is 4; `a ^ b | a & b` is 7; `unsigned char c = 250` plus 10
  prints 4; the comma expression `(y += 3, y * 2)` gives 10; `0xF0 << 4` promotes to 3840; `if (x = 0)` takes the else
  branch; the paired `for` header stops at `5 5`; the nested loop counts 15; the switch falls through to `twothree`;
  the switch/continue program accumulates 425; the value-parameter swap leaves `1 2`; `sq` sums to 30; the `static`
  local returns 3 on the third call; `inc`/`bump` leaves 6; the `static` accumulator returns 20; `f(4)` sums to 10;
  the bit-printing recursion emits `1 0 1 1` for 13; the post-recursion print gives `123`; `f(6)` of the Fibonacci
  recurrence is 8; and the call counter for `f(5)` reaches 15 (`C(n) = C(n−1) + C(n−2) + 1`, computed as
  1, 1, 3, 5, 9, 15). A second compiled program confirmed the remaining code-based items: `sizeof a` inside
  `g(int a[])` is 8, the pointer size, not 40; the post-recursion print emits `123`; the shared counter of `f(5)` is
  incremented 15 times; the unsigned `i >= 0` test stays true at `i = 0`, where the value wraps to 4 294 967 295; the
  `i != 10` stride-3 loop passes 10 without stopping; and the two terminating loops leave `i` at 1 and 6. The five MSQ
  items are conceptual — their statements were checked against the standard and, where the claim is runnable, against
  the compiler's behaviour.
- Shell parity: the paper was produced by splicing a new payload into the shipped shell rather than re-typing it. The
  `<style>` block (13 243 bytes) and the closing `<script>` block (9 428 bytes) are byte-identical to
  `engineering-mathematics/linear-algebra-matrices/gate_em_mock_1_2026-10-26.html`, the `:root` block still matches
  `design-tokens.css` and `index.html` byte for byte, and the document's element nesting matches the template's
  exactly. No new literal hex value was introduced: the code blocks in the questions use `var(--bg)` and
  `var(--line)`, never a raw colour.
- The paper was exercised in a jsdom harness before shipping (46 checks, all passing): nothing is revealed pre-submit
  (no solution text, no option mark, no key content, base64 payload, key tab disabled, summary hidden, timer at
  60:00); all 25 answered correctly scores **35/35** with 25 correct and the key unlocks with 25 solutions; a mixed
  paper (1 correct MCQ, 1 wrong MCQ, 1 exactly-selected MSQ, 1 partially-selected MSQ, 1 correct NAT, 1 wrong NAT)
  scores **5/35** with 3 correct, 3 wrong and 19 unattempted — confirming an MSQ pays nothing unless the exact option
  set is chosen; the palette reaches `ans` / `mrk` / `amr` / `na` / `cur` and switches to `ok` / `bad` / `skip` after
  submit; each tab shows exactly one view; and every card carries `data-subject`, `data-unit`, `data-unit-number`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`.
- A new subject folder and bank were created: `programming-data-structures/question-bank/master_bank.json` holds 25
  questions on Unit 1 with all seven `data-*` attributes represented in its records. `index.html` gained the seven
  Programming and Data Structures units, one test card and the 25 banked questions, and its data block now holds
  12 tests, 51 units and 500 questions.
- **The portal's static header was stale and has been corrected.** `index.html` still read "2 subjects",
  "7 units · 350 solved questions banked" and chips of 7 units / 350 / 350 / "23 units · 106 subtopics" while the
  data block already held 11 tests and 475 questions. The data block was updated in place, as required, and those six
  static strings were recomputed from it: 7 subjects, 51 units, 500 solved, 12 sets published, 51 units in the
  series, 222 subtopics. Every `href` in the portal still resolves.
- Programming and Data Structures contains no `GATE_PYQ_VARIATION` item: no C-programming previous-year question has
  been verified against an official paper and key in this run, so none is claimed. Every item is `STANDARD_TEXTBOOK`
  (13) or `ORIGINAL_SYNTHESIS` (12).

- **2026-10-26, Engineering Mathematics → Unit 1 (Linear Algebra: Matrices & Systems).** MODE A: the subject was drawn
  at random from the 11 GATE CSE subjects and came out Engineering Mathematics. No bank existed for it, so step B6's
  fallback applied: `(2026-10-26 − 2026-10-26) mod 5 = 0` → Unit 1. No override was used and no second pass has started.
- 25 questions, all new: 15 MCQ / 5 MSQ / 5 NAT, difficulty 10 easy / 10 medium / 5 hard. Coverage is 8 / 7 / 6 / 4
  across matrix operations, rank & nullity, systems of linear equations and Gauss elimination, so every one of the
  unit's four subtopics is represented.
- Filed only at `engineering-mathematics/linear-algebra-matrices/gate_em_mock_1_2026-10-26.html`. No earlier paper
  existed for this unit, so nothing was archived and no root copy was written.
- Shell parity: the paper was produced by splicing a new payload into the shipped shell rather than re-typing it. After
  normalising the title, the header brand and sub-line, the candidate block, the metadata chips, `#qhost`, the payload,
  the Question Bank pane and the About pane, the remaining bytes are identical to the Algorithms, Databases and
  Operating Systems papers (27 761 bytes on all four sides). The `:root` block still matches `design-tokens.css` and
  `index.html` byte for byte.
- The payload is base64 and every `.sol` div is empty until submit. A jsdom harness was run before shipping: no solution
  text, option mark, mark text, key content or summary is present pre-submit; all 25 answered correctly scores
  **35/35** with 25 correct and the key unlocks with 25 solutions; a mixed paper (1 correct MCQ, 1 wrong MCQ, 1
  exactly-selected MSQ, 1 partially-selected MSQ, 1 correct NAT, 1 wrong NAT) scores **5/35** with 3 correct, 3 wrong
  and 19 unattempted — confirming an MSQ pays nothing unless the exact option set is chosen; the palette reaches
  `amr` / `na` / `cur` / unvisited and Save & Next advances the position.
- Every numeric answer was recomputed independently with NumPy before shipping: `det(adj A) = 4` for a 3×3 matrix with
  determinant 2; `rank([[1,2,3],[2,4,7],[3,6,10]]) = 2`; the elimination of `[[2,1,1],[4,3,3],[8,7,9]]` gives
  `U₃₃ = 2`; the parameterised system is consistent with infinitely many solutions at exactly `k = 5`; and a 4×4
  idempotent matrix of rank 3 has trace 3.
- Engineering Mathematics contains no `GATE_PYQ_VARIATION` item: no linear-algebra previous-year question has been
  verified against an official paper and key, so none is claimed. Every item is `STANDARD_TEXTBOOK` (11) or
  `ORIGINAL_SYNTHESIS` (14).

- **2026-10-26, Compiler Design → Unit 1 (Lexical Analysis), Set 2 of 2.** MODE A: the subject was drawn at random
  from the 11 GATE CSE subjects and came out Compiler Design. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "1 of 2"}` and held 25 questions on Unit 1. 25 < `UNIT_QUESTION_CAP = 50`
  and the unit had been current for 0 days, so step B3 regenerated Unit 1 rather than advancing. This is the second
  and final set for the unit: 25 + 25 = 50, exactly the cap, so no partial set was added. The next Compiler Design run
  will advance to `(0 + 1) mod 5` = Unit 2.
- All 25 items are new: no stem, option set or answer is shared with Set 1 (checked by exact-string comparison of the
  two halves of `master_bank.json`). Coverage is 7 / 8 / 5 / 5 across the four subtopics, with the standard
  15 MCQ / 5 MSQ / 5 NAT composition and the 10 easy / 10 medium / 5 hard split.
- The Set 1 paper moved to `compiler-design/lexical-analysis/archive/gate_cd_mock_1_2026-10-26_run1.html` with its
  questions, options, answers, solutions and duration frozen. The new Set 2 paper is filed only at
  `compiler-design/lexical-analysis/`; no root copy was written.
- **Two defects in the shipped Compiler Design paper were repaired.** Its header sub-line read
  "Unit 1 — Asymptotic Analysis & Recurrences", a copy-paste from the Algorithms paper; it now names Lexical Analysis
  in both the live paper and the archive. Its About pane was missing a closing `</div>`, and the `#qhost` splice used
  to build this paper dropped the matching `</div>` as well — together these left `#view-bank` nested inside
  `#view-test`, so the Question Bank tab rendered blank. Both files now close every element except the `.wrap`
  container, exactly as the Databases paper does. The tab was re-rendered in a headless browser to confirm it draws
  its 25 solved questions under four subtopic accordions.
- The payload is base64 rather than plain JSON and the answer key pane is empty until submit. A jsdom harness was run
  before shipping: nothing is revealed pre-submit (no solution text, no option mark, no key content); all 25 answered
  correctly scores **35/35** with 25 correct; a mixed paper (1 correct MCQ, 1 wrong MCQ, 1 exactly-selected MSQ,
  1 partially-selected MSQ, 1 correct NAT, 1 wrong NAT) scores **5/35** with 3 correct, 2 wrong and 20 unattempted;
  the palette reaches `na` / `ans` / `mrk` / `amr` / `cur` and switches to `ok` / `bad` / `skip` after submit; the
  answer key unlocks with 25 solutions; the bank tab shows 25 solved cards with every solution collapsed.
- Shell parity: the paper was produced by splicing a new payload into the shipped shell rather than re-typing it.
  After normalising the title, the header sub-line, the metadata chips, `#qhost`, the payload, the Question Bank pane
  and the About pane, the remaining bytes are identical to the archived Set 1 paper (31 186 bytes on both sides).
  The `:root` block still matches `design-tokens.css` and `index.html` byte for byte.
- Compiler Design still contains no `GATE_PYQ_VARIATION` item. Two lexical-analysis PYQs were looked at — GATE CSE
  2000 Q1.18 (number of tokens in a `printf` statement, key 10) and GATE CSE 2011 (machine model needed for lexical
  analysis, key: finite state automata) — but both were read from secondary question archives, not from an official
  paper PDF, so neither is recorded as verified and no item is tagged as a PYQ. Several questions exercise the same
  skills (`CD-U1-Q32` token counting, `CD-U1-Q40` DFA state counting) without claiming PYQ status.

- **2026-10-26, Operating Systems → Unit 1 (Process Management & CPU Scheduling).** MODE A: the subject was drawn at
  random from the 11 GATE CSE subjects and came out Operating Systems. `operating-systems/question-bank/master_bank.json`
  did not exist, so there was no `runs[]` entry to read and no cap to check; the starting unit came from the documented
  fallback, `(2026-10-26 − 2026-10-26) mod 6 = 0` → Unit 1. No override was used and no second pass has started.
- The 25 questions cover all four of the unit's subtopics (7 / 6 / 5 / 7 by subtopic) with the standard 10 easy /
  10 medium / 5 hard split and the standard 15 MCQ / 5 MSQ / 5 NAT composition.
- Every scheduling number was recomputed with an independent unit-step simulator rather than by hand:
  preemptive priority on the Q18 table gives **3** preemptions (P1 displaced at t = 2, 4 and 6); FCFS on the Q19 table
  gives an average waiting time of **3 ms**; non-preemptive SJF on bursts 12/18/30 gives **14 ms**; round robin with
  q = 2 on the Q22 table completes P1 at **9 ms** (checked under both arrival-vs-requeue tie-breaks); SRTF on the Q24
  table gives an average waiting time of **3 ms**; SRTF on the Q25 table gives an average turnaround time of **5 ms**
  (tie-break independent). `fork()` twice gives **4** processes and 1 + 4 threads give **5** stacks.
- The set carries one `GATE_PYQ_VARIATION` item, `OS-U1-Q21`, built on GATE CSE 2021, Set 1, Question 25 (1-mark NAT;
  minimum achievable average waiting time of three processes with bursts 16, 20 and 10 ms arriving at time zero, whose
  value is 12 ms by SJF optimality). It is a re-worded variation with different burst lengths, not the original text,
  and it is not presented as an official question. `verified_pyqs` records the source paper and the derivation.
- This is the first paper for a unit with no earlier paper, so nothing was moved into `archive/`. The paper is filed
  only at `operating-systems/process-scheduling/`; no root copy was written.
- A new subject folder and bank were created: `operating-systems/question-bank/master_bank.json` holds 25 questions on
  Unit 1. `index.html` gained the six Operating Systems units, one test card and the 25 banked questions.
- Shell parity checked this run: the paper was generated from the existing exam shell by slicing the shell out of an
  existing paper rather than re-typing it, and after normalising the question payload, the Question Bank pane, the About
  pane and the metadata block, the remaining bytes are identical to
  `databases/er-relational-algebra/gate_db_mock_1_2026-10-26.html` (27 632 bytes on both sides). The `:root` block
  matches `design-tokens.css` and `index.html` byte for byte.
- The paper was exercised in a jsdom harness before shipping: nothing is revealed before submit (no solution text, no
  option mark, no answer-key content, and the payload is base64 rather than plain JSON); all 25 answered correctly
  scores 35/35 with 25 correct; a mixed paper (1 correct MCQ, 1 wrong MCQ, 1 partially-selected MSQ, 1 exact MSQ,
  1 correct NAT, 1 wrong NAT) scores 5/35 with 3 correct, 3 wrong and 19 unattempted; the palette reaches
  `na`/`ans`/`mrk`/`amr`/`cur` and switches to `ok`/`bad`/`skip` after submit; the answer key unlocks with all 25
  solutions; each tab shows exactly one view.

- **2026-10-26, Compiler Design → Unit 1 (Lexical Analysis).** MODE A: the subject was drawn at random from the
  11 GATE CSE subjects and came out Compiler Design. `compiler-design/question-bank/master_bank.json` did not exist, so
  there was no `runs[]` entry and no cap to check; the starting unit came from the documented fallback,
  `(2026-10-26 − 2026-10-26) mod 5 = 0` → Unit 1. Set 1 of 2, 25 questions, all four subtopics covered. No override.
- Compiler Design contains no `GATE_PYQ_VARIATION` item: no lexical-analysis previous-year question has been verified
  against an official paper and key in this run, so none is claimed.

- **2026-10-26, Databases → Unit 1 (ER Models & Relational Algebra).** MODE A: the subject was drawn at random from the
  11 GATE CSE subjects and came out Databases. `databases/question-bank/master_bank.json` did not exist, so there was no
  `runs[]` entry to read and no cap to check; the starting unit came from the documented fallback,
  `(2026-10-26 − 2026-10-26) mod 5 = 0` → Unit 1. No override was used.
- All four of the unit's subtopics are represented: ER diagrams / cardinality / weak entities (6 questions), relational
  model & constraints (6), relational algebra (8), tuple & domain relational calculus (5). Composition 15 MCQ / 5 MSQ /
  5 NAT, difficulty 10 easy / 10 medium / 5 hard, 35 marks.
- The set carries one `GATE_PYQ_VARIATION` item, `DB-U1-Q17`, built on the verified PYQ-GATE2014S3-Q30 (GATE CSE 2014,
  Set 3, Q30, official key D). It is a re-worded variation over Doctor/Patient, not the original text, and it is not
  presented as an official question.
- This is the first paper for a unit with no earlier paper, so nothing was moved into `archive/`. The paper is filed
  only at `databases/er-relational-algebra/`; no root copy was written.
- A new subject folder and bank were created: `databases/question-bank/master_bank.json` now holds 25 questions on
  Unit 1. `index.html` gained the five Databases units, one test card and the 25 banked questions.

- **2026-10-26, Algorithms → Unit 1 (Asymptotic Analysis & Recurrences).** MODE A: the subject was drawn at random from the 11 GATE CSE
  subjects and came out Algorithms. `algorithms/question-bank/master_bank.json` did not exist, so there was no `runs[]`
  entry to read and no cap to check; the starting unit came from the documented fallback,
  `(2026-10-26 − 2026-10-26) mod 7 = 0` → Unit 1. No override was used and no second pass has started. This is a new
  subject, not a continuation of the Discrete Mathematics rotation — that series is untouched by this run and Unit 6
  (Mathematical Induction & Recursion) is still the next unit there.
- The 25 questions cover all four of Unit 1's subtopics (8 / 8 / 6 / 4 by subtopic) with the standard 10 easy / 10
  medium / 5 hard split and the standard 15 MCQ / 5 MSQ / 5 NAT composition. Every recurrence in the paper was checked
  against its Master Theorem case or its recursion tree by hand, and every numeric answer was recomputed
  independently: `T(n) = 8T(n/2) + n²` → `n³`; `T(n) = 2T(n/4) + √n` → `√n log n`, so `k = 1`; `T(n) = T(n−1) + n`
  with `T(1) = 1` → `T(10) = 55`; the substitution bound `T(n) ≤ cn log₂ n` for `T(n) = 2T(n/2) + n` closes at
  `c = 1`; and the recursion tree for `T(n) = 4T(n/2) + n²` has `4⁵ = 1024` leaves at `n = 32`.
- No `GATE_PYQ_VARIATION` item ships: no algorithms PYQ has been verified against an official paper and answer key for
  this unit, so none is claimed. The About tab and the Question Bank tab both say so, and `verified_pyqs` is empty for
  this subject.
- Filed only at `algorithms/asymptotic-analysis/gate_algo_mock_1_2026-10-26.html`. Nothing was written at the repository
  root; `index.html` is still the only HTML file there.
- Shell parity checked this run: the new paper was generated from the existing exam shell, and after normalising the
  question payload, the Question Bank pane, the About pane and the metadata block, the remaining bytes are identical to
  `discrete-mathematics/functions/gate_dm_mock_5_2026-10-26.html` (27 487 bytes on both sides). The `:root` block still
  matches `design-tokens.css` byte for byte.
- The paper was exercised in a jsdom harness before shipping: no solution, no option mark and no answer-key content is
  in the DOM before submit; all 25 answered correctly scores 35/35; a mixed paper (2 correct MCQ, 1 wrong MCQ, 1 MSQ
  with a partial selection, 1 exact MSQ, 1 correct NAT, 1 wrong NAT) scores 5/35 with 3 correct, 3 wrong, 19
  unattempted; the palette reaches `na` / `ans` / `mrk` / `amr` / `cur` and switches to `ok` / `bad` / `skip` after
  submit; the answer key unlocks with all 25 solutions.
- `index.html` was extended, not rebuilt: seven `tests` entries, 23 `units` entries and 350 `questions` entries in its
  data block, with the two lookups made subject-aware so Algorithms Unit 1 does not collide with Discrete Mathematics
  Unit 1. Every `href` in the portal resolves.

- **2026-10-26, Unit 5 → Unit 5 (Set 2).** `master_bank.json` showed Unit 5 with 25 banked questions, current since the
  same date — under the 50-question cap and current for 0 days — so the rotation re-selected Unit 5 rather than
  advancing. 25 + 25 = 50 closes Unit 5 at the cap; the next run for this subject advances to
  (4 + 1) mod 16 = 5 → Unit 6, Mathematical Induction & Recursion.
- Set 2 repeats no question from Set 1: the two sets share no id, no stem, no option set and no numeric answer. Each of
  the five subtopics carries exactly five questions (5 / 5 / 5 / 5 / 5), so every subtopic is represented, and the
  difficulty split is 10 easy / 10 medium / 5 hard as in every paper.
- Set 2 contains no `GATE_PYQ_VARIATION` item — no functions PYQ has been verified against an official paper and
  answer key for this unit, so none is claimed — and the About tab says so; every question is `STANDARD_TEXTBOOK` or
  `ORIGINAL_SYNTHESIS`.
- Filed only at `discrete-mathematics/functions/gate_dm_mock_5_2026-10-26.html`. Set 1 was moved into that unit's
  `archive/` as `..._run1.html` before the new file was written, so the unit folder never held two current papers and
  nothing was written at the repository root.
- Every computational answer in this set was checked by brute force before shipping: 5³ = 125 functions and 0 injections
  from a 5-set to a 3-set; 4² = 16, P(4,2) = 12, 0 surjections and 0 bijections from a 2-set to a 4-set; 540 surjections
  from a 6-set onto a 3-set (exhaustive enumeration over 3⁶ = 729 maps agrees); 4⁴ − 4! = 232 non-bijections on a 4-set;
  ⌈40/12⌉ = 4; ⌈100/4⌉ = 25 for the 10 × 10 grid colouring; exactly 3 integers satisfy ⌊n/3⌋ = 12 and exactly 23 satisfy
  ⌊√n⌋ = 11 for n ≤ 200; ⌊−3.4⌋ + ⌈−3.4⌉ = −7; T(8) = 32 for T(n) = 2T(⌊n/2⌋) + n; (g ∘ f)⁻¹(8) = 3 for
  f(x) = 2x − 1, g(x) = x + 3; and exactly 2 of the six named test functions are bijections of ℝ onto ℝ.
- Shell parity checked this run: the `<style>` block and the `<script>` block are byte-identical to the Unit 5 Set 1
  paper's, the `:root` block still matches `design-tokens.css` exactly, and the paper carries the same literal hex
  occurrences as the shell it was built from — no new hex value was introduced.
- The paper was exercised in a jsdom harness before shipping (27 checks, all passing): timer starts at 60:00, the answer
  key tab stays locked, no option mark or solution renders before submit, the palette reaches `na` / `ans` / `mrk` /
  `amr` / `cur` correctly, all 25 answered correctly scores 35/35, an MSQ with one of three correct options selected
  scores zero for that question (33/35), a blank paper scores 0/35, and the key tab unlocks on submit with all 25
  solutions.
- The Question Bank tab inside the paper now lists 300 solved questions — Unit 5's Set 1 has been superseded, so its 25
  join Set 2 there; Unit 5 Set 2's own 25 are the active test and are not repeated in the tab. `index.html` holds all
  325.
- No second pass has started; units 6–15 are still untouched.
- Subject selection: the series is still running Discrete Mathematics, the only subject with a question bank, until its
  16 units complete a pass. No override was used for this run.

- **2026-10-26, Unit 4 → Unit 5.** `master_bank.json` showed Unit 4 with 50 banked questions — the 50-question cap — so
  the rotation advanced by the modulo rule: (3 + 1) mod 16 = 4 → Unit 5, Functions. Unit 5 now holds 25 questions,
  Set 1 of 2. The advance is computed from the bank, not from the calendar.
- The 25 questions are new: no id, stem, option set or numeric answer repeats an earlier paper. Each of the five
  subtopics carries exactly five questions (5 / 5 / 5 / 5 / 5), so every subtopic is represented, and the difficulty
  split is 10 easy / 10 medium / 5 hard as in every paper.
- Set 1 contains no `GATE_PYQ_VARIATION` item — no functions PYQ has been verified against an official paper and
  answer key for this unit, so none is claimed — and the About tab says so; every question is `STANDARD_TEXTBOOK` or
  `ORIGINAL_SYNTHESIS`.
- Filed only at `discrete-mathematics/functions/gate_dm_mock_5_2026-10-26.html`. Unit 5 had no earlier paper, so
  nothing was archived, no unit folder holds two current papers, and nothing was written at the repository root.
- Every numeric answer in this set was checked by brute force before shipping: `⌈n/2⌉` is onto `ℤ⁺` while `2n` is not;
  `f(x) = x/(x²+1)` collides at 2 and ½ and has range `[−½, ½]`; `x²−4x+7 = 3` has the single root 2; `(f⁻¹∘g⁻¹)(16) = 2`
  for `f(x)=2x+1`, `g(x)=3x+1`; 3⁴ = 81, `P(5,4) = 120`, and 150 onto maps from a 5-set onto a 3-set (exhaustive
  enumeration); 720 bijections on 6 elements; 533 integers in 1…1000 divisible by neither 3 nor 5; `f(1000) = 11` and
  `T(8) = 15` for the two halving recurrences; and no 5-tuple of residues mod 3 avoids a zero-sum triple, which is what
  Q19 asserts.
- Shell parity checked this run: the `<style>` block and the `<script>` block are byte-identical to the Unit 4 Set 2
  paper's, the `:root` block still matches `design-tokens.css` exactly, and the paper carries the same 114 literal hex
  occurrences as the shell it was built from — no new hex value was introduced.
- The paper was exercised in a jsdom harness before shipping: timer starts at 60:00, the answer key tab stays locked,
  no option mark or solution renders before submit, the palette reaches `na` / `ans` / `mrk` / `amr` / `cur`
  correctly, all 25 answered correctly scores 35/35, an MSQ with one of three correct options selected scores zero for
  that question, and the key tab unlocks on submit with all 25 solutions.
- The Question Bank tab inside the paper now lists 275 solved questions — Unit 4's Set 2 has been superseded, so its 25
  join Set 1 there; Unit 5's own 25 are the active test and are not repeated in the tab. `index.html` holds all 300.
- No second pass has started; units 6–15 are still untouched.
- Subject selection: the series is still running Discrete Mathematics, the only subject with a question bank, until its
  16 units complete a pass. No override was used for this run.

- **2026-10-26, Unit 4 → Unit 4 (Set 2).** `master_bank.json` showed Unit 4 with 25 banked questions, current since the
  same date — under the 50-question cap and current for 0 days — so the rotation re-selected Unit 4 rather than
  advancing. 25 + 25 = 50 closes Unit 4 at the cap; the next run for this subject advances to
  (3 + 1) mod 16 = 4 → Unit 5, Functions.
- Set 2 repeats no question from Set 1: the two sets share no id, no stem, no option set and no numeric answer. The
  six subtopics carry 5 / 4 / 4 / 4 / 4 / 4 questions, so every subtopic is represented, and the difficulty split is
  10 easy / 10 medium / 5 hard as in every paper.
- Set 2 contains no `GATE_PYQ_VARIATION` item — no relations PYQ has been verified against an official paper and key —
  and the About tab says so; every question is `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`.
- Filed only at `discrete-mathematics/relations/gate_dm_mock_4_2026-10-26.html`. Set 1 was moved into that unit's
  `archive/` as `..._run1.html` before the new file was written, so the unit folder never held two current papers and
  nothing was written at the repository root.
- Every computational answer in this set was checked by brute force before shipping: 10 relations on a three-element
  set are symmetric and transitive but not reflexive; `S(5,3) = 25`; the divisibility poset on
  {1,2,3,5,6,10,15,30} has 12 Hasse edges and the one on {1,2,3,4,6,12,18,36} has 10; exactly 4 elements of `D(36)`
  have a complement; 64 irreflexive relations on three elements; 729 reflexive-and-antisymmetric relations on four;
  19 partial orders on three elements; and Q20's closure adds exactly 4 pairs.
- Shell parity checked this run: the `<style>` block and the `<script>` block are byte-identical to the Unit 4 Set 1
  paper's, and the `:root` block still matches `design-tokens.css` exactly. No new literal hex value was introduced.
- The paper was exercised in a jsdom harness before shipping: timer starts at 60:00, the answer key tab stays locked,
  no option mark or solution renders before submit, the palette reaches `na` / `ans` / `mrk` / `amr` / `cur`
  correctly, all 25 answered correctly scores 35/35, an MSQ with one correct option deselected scores zero for that
  question (33/35), and the key tab unlocks on submit.
- The Question Bank tab inside the paper now lists 250 solved questions — Unit 4's Set 1 has been superseded, so its 25
  join the tab; Unit 4 Set 2's own 25 are the active test and are not repeated there. `index.html` holds all 275.
- No second pass has started; units 5–15 are still untouched.
- Subject selection: the series is still running Discrete Mathematics, the only subject with a question bank, until its
  16 units complete a pass. No override was used for this run.

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
algorithms/
  asymptotic-analysis/gate_algo_mock_1_<date>.html   current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
databases/
  er-relational-algebra/gate_db_mock_1_<date>.html   current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
compiler-design/
  lexical-analysis/gate_cd_mock_1_<date>.html        current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
operating-systems/
  process-scheduling/gate_os_mock_1_<date>.html      current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
engineering-mathematics/
  linear-algebra-matrices/gate_em_mock_1_<date>.html current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
programming-data-structures/
  c-programming-core/gate_ds_mock_1_<date>.html      current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
computer-networks/
  network-fundamentals-framing/gate_cn_mock_1_<date>.html  current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
theory-of-computation/
  regular-languages-fa/gate_toc_mock_1_<date>.html   current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
digital-logic/
  number-systems/gate_dl_mock_1_<date>.html          current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
```

## Syllabus coverage checklist

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Propositional Logic | `propositional-logic` | 50 | yes |
| 2 | Predicate & First-Order Logic | `predicate-logic` | 50 | yes |
| 3 | Set Theory | `set-theory` | 50 | yes |
| 4 | Relations | `relations` | 50 | yes |
| 5 | Functions | `functions` | 50 | yes |
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

Algorithms:

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Asymptotic Analysis & Recurrences | `asymptotic-analysis` | 25 | yes |
| 2 | Divide and Conquer & Sorting | `sorting-divide-conquer` | 0 | — |
| 3 | Greedy Algorithms | `greedy-algorithms` | 0 | — |
| 4 | Dynamic Programming | `dynamic-programming` | 0 | — |
| 5 | Graph Algorithms: Traversals & Spanning Trees | `graph-algorithms-traversals-mst` | 0 | — |
| 6 | Graph Algorithms: Shortest Paths | `shortest-paths` | 0 | — |
| 7 | Complexity Theory & NP-Completeness | `complexity-np-complete` | 0 | — |

### Programming and Data Structures

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | C Programming Foundations | `c-programming-core` | 25 | yes |
| 2 | Pointers, Memory & Preprocessors | `pointers-memory` | 0 | — |
| 3 | Linear Data Structures | `linear-data-structures` | 0 | — |
| 4 | Binary Trees & Tree Traversals | `trees-traversals` | 0 | — |
| 5 | Binary Search Trees & Balanced Trees | `search-trees` | 0 | — |
| 6 | Heaps & Priority Queues | `heaps-priority-queues` | 0 | — |
| 7 | Hashing & Hash Tables | `hashing` | 0 | — |

### Databases

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | ER Models & Relational Algebra | `er-relational-algebra` | 25 | yes |
| 2 | SQL & Advanced Querying | `sql-querying` | 0 | — |
| 3 | Database Normalization | `normalization` | 0 | — |
| 4 | Transactions & Concurrency Control | `transactions-concurrency` | 0 | — |
| 5 | Indexing, B-Trees & Storage | `indexing-storage` | 0 | — |

### Compiler Design

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Lexical Analysis | `lexical-analysis` | 25 | yes |
| 2 | Syntax Analysis: Top-Down Parsing | `top-down-parsing` | 0 | — |
| 3 | Syntax Analysis: Bottom-Up Parsing | `bottom-up-parsing` | 0 | — |
| 4 | Syntax-Directed Translation & Intermediate Code | `sdt-intermediate-code` | 0 | — |
| 5 | Runtime Environments & Code Optimization | `runtime-code-optimization` | 0 | — |

### Operating Systems

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Process Management & CPU Scheduling | `process-scheduling` | 50 | yes |
| 2 | Inter-Process Communication & Synchronization | `synchronization-ipc` | 25 | yes |
| 3 | Deadlocks | `deadlocks` | 0 | — |
| 4 | Memory Management & Paging | `memory-paging` | 0 | — |
| 5 | Virtual Memory & Page Replacement | `virtual-memory` | 0 | — |
| 6 | File Systems & Disk Scheduling | `storage-file-systems` | 0 | — |

### Engineering Mathematics

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Linear Algebra: Matrices & Systems | `linear-algebra-matrices` | 50 | yes |
| 2 | Linear Algebra: Eigenvalues & Vectors | `eigenvalues-eigenvectors` | 0 | — |
| 3 | Calculus: Limits, Continuity & Differentiability | `calculus-limits-derivatives` | 0 | — |
| 4 | Calculus: Maxima, Minima & Integrals | `calculus-optimization-integrals` | 0 | — |
| 5 | Continuous Probability & Distributions | `probability-distributions` | 0 | — |

### Computer Networks

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Layering, Physical & Framing | `network-fundamentals-framing` | 25 | yes |
| 2 | Data Link Protocols & MAC | `data-link-mac` | 0 | — |
| 3 | Network Layer: IP Addressing & Subnetting | `ipv4-subnetting` | 0 | — |
| 4 | Network Layer: Routing & Protocols | `routing-protocols` | 0 | — |
| 5 | Transport Layer: TCP, UDP & Congestion | `transport-layer` | 0 | — |
| 6 | Application Layer & Network Security | `application-layer-security` | 0 | — |

### Theory of Computation

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Regular Languages & Finite Automata | `regular-languages-fa` | 25 | yes |
| 2 | Grammars & Context-Free Languages | `cfl-grammars` | 0 | — |
| 3 | Pushdown Automata | `pushdown-automata` | 0 | — |
| 4 | Turing Machines & Decidability | `turing-machines-decidability` | 0 | — |

### Digital Logic

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Number Systems & Representation | `number-systems` | 25 | yes |
| 2 | Combinational Circuit Design | `combinational-circuits` | 0 | — |
| 3 | Sequential Circuits: Flip-Flops & Registers | `sequential-flipflops` | 0 | — |
| 4 | Sequential Circuits: Counters & State Machines | `sequential-fsm-counters` | 0 | — |

## Provenance rules used in every test

1. A question is called an official GATE PYQ **only** when its year, paper and official answer key have been verified;
   those records live in `master_bank.json` under `verified_pyqs`.
2. Questions built on a verified PYQ pattern are tagged `GATE_PYQ_VARIATION` and are explicitly *not* official questions.
   Discrete Mathematics Unit 1's single variation is built on the GATE CSE 2014 Set 1 Q53 pattern (formula true exactly
   when a stated number of p, q, r are TRUE; official key B). Databases Unit 1's single variation is built on the
   GATE CSE 2014 Set 3 Q30 pattern (difference of projections over a join; official key D). Operating Systems Unit 1's
   single variation is built on GATE CSE 2021 Set 1 Q25 (minimum achievable average waiting time under a non-preemptive
   scheduler for bursts 16, 20 and 10 arriving at time zero; value 12 ms, which follows from SJF optimality).
   Digital Logic Unit 1 carries two variations: `DL-U1-Q03` on the GATE CSE 2019 Q4 pattern (−28 in 16-bit two's
   complement, key option C) and `DL-U1-Q04` on the GATE CSE 2016 Set 1 Q7 pattern (1111 1111 1111 0101 = −11).
3. Everything else is tagged `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS` and is practice material written for this series.
4. Historical questions are never deleted, never counted towards an active test, and are always filed under their
   `data-subtopic` slug.

## Answer key policy

The active mock test reveals nothing before submission. On submit, the file grades itself, marks the correct options,
unlocks the answer-key tab and shows a detailed solution for every question (concept, steps, final answer, why the other
options fail, common misconception, faster method, takeaway). Banked historical questions use a separate expand-on-demand
review interface.

## Known deviations (to be fixed in one pass across every paper)

- `6.4 No raw hex outside :root` is not yet met (the Engineering Mathematics Unit 1 Set 2 paper carries 84 literal hex
  occurrences, against the reference shell's 86 — no new value was added, because the new cards use `var(--muted)`):
  the shipped shell uses literal hex
  values for a handful of tints and borders (`#f8fafc`, `#b9c6d2`, `#eaf2f8`, …). Because every paper must share one
  byte-identical shell, this can only be corrected by re-issuing all papers together, so it is recorded here rather than
  fixed in one file and breaking shell parity.
- The `index.html` archive prints an answer line from `answer_display` and, for records created before 2026-10-25, a
  second identical line inside `solution_html`. The 50 Unit 2 records and the 25 Unit 1 Set 2 records carry it once; the
  older records still carry it twice. Normalising them is part of the same one-pass fix as the raw-hex item above.
- ~~The exam shell bound `btnNext`, `btnPrev`, `btnMark` and `btnClear` with `document.getElementById` while every
  question card carried the same four ids, so those handlers attached only to Question 1's buttons and the footer
  buttons on cards 2–25 were inert.~~ **Fixed 2026-10-26, across all 15 papers that share the current shell.** The
  handlers are now delegated to the `#qhost` container and act on the card that owns the clicked button, so Save &
  Next, Previous, Mark for review and Clear response work on every question. Verified in a jsdom harness on the
  Operating Systems paper, the Databases paper and an archived Discrete Mathematics set. The two older
  `proof-techniques/archive/..._run1/_run2` files do not use this shell and were left untouched.
- `6.1` requires an archived paper to be rebuilt on the current shell. Fifteen of the seventeen papers now share one
  shell: the `<style>` block and the `<script>` block of every current and archived paper that uses the card layout are
  byte-identical to each other (confirmed after the button fix above). The exception remains
  `proof-techniques/archive/gate_dm_mock_16_2026-10-25_run1.html` and `..._run2.html`, which were produced before the
  shell was fixed and still use the earlier layout (no `.qcard` cards, different style block). Their content is frozen
  and correct; they need rebuilding on the current shell in the same one-pass re-issue as the raw-hex item above.
- `6.5` asks for an explicit `:focus-visible` ring on every interactive control. The shared shell never sets
  `outline:none` (so the browser's default ring survives on buttons, tabs, options and accordion summaries) and gives an
  explicit outline to the NAT input and the current palette button, but it defines no `:focus-visible` selector. The
  Digital Logic Unit 1 paper inherits the shell unchanged so that parity holds; adding the rule is a one-line CSS change
  that belongs to the same one-pass re-issue as the raw-hex item.
- `6.4` also asks for the palette fills to use the `-d` token variants so white numerals clear 4.5:1. The shipped shell
  fills `.pal button.ans/.na/.mrk` with `--green`/`--red`/`--violet` instead of `--green-d`/`--red-d`/`--violet-d`, which
  fails that ratio. The Operating Systems paper inherits the shell unchanged so that parity holds; the correction is a
  four-line CSS change and belongs to the same one-pass re-issue as the raw-hex item.
- The Engineering Mathematics Unit 1 Set 2 paper inherits the three open shell items above unchanged (literal hex
  outside `:root`, no explicit `:focus-visible` selector, palette fills on the `--green`/`--red`/`--violet` tokens
  rather than their `-d` variants), for the same reason: re-typing any of them in one paper would break shell parity.
- The Programming and Data Structures Unit 1 Set 2 paper inherits the three open shell items above unchanged
  (literal hex outside `:root`, no explicit `:focus-visible` selector, palette fills on the `--green`/`--red`/`--violet`
  tokens rather than their `-d` variants). Re-typing any of them in one paper would break shell parity, so they stay
  recorded here for the one-pass re-issue across every paper.
- Discrete Mathematics Unit 16 (Logic & Proof Techniques) still carries **75** questions — three sets, written
  before the 50-question cap existed. The rotation has already moved past it (Unit 5 was the most recent Discrete
  Mathematics unit), so the over-cap state is frozen history rather than an active breach; it is recorded here so the
  status table and the banks agree.
