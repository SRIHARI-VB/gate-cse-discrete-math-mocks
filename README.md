# gate-cse-mocks — GATE CSE 2027 mock test series

Daily, self-contained mock tests for **GATE CSE 2027**, one unit at a time on a per-subject unit rotation.
Five subjects are now in the series: Discrete Mathematics (16 units), Algorithms (7 units), Databases (5 units), Compiler Design (5 units) and Operating Systems (6 units). Every test is a single HTML file that opens in any browser, offline, in a TCS iON–style exam shell:
question palette with the standard status colours, a running countdown, radio MCQ, checkbox MSQ and typed NAT answers,
and no answer, option mark or hint visible until the test is submitted.

## Latest test

- **Compiler Design · Unit 1 — Lexical Analysis, Set 2 of 2**, 2026-10-26 → [`compiler-design/lexical-analysis/gate_cd_mock_1_2026-10-26.html`](compiler-design/lexical-analysis/gate_cd_mock_1_2026-10-26.html)
- 25 questions: 15 MCQ · 5 MSQ · 5 NAT · difficulty 10 easy / 10 medium / 5 hard · 60 minutes · 35 marks
- Subtopics: tokens, lexemes & patterns (7) · regular expressions to lexers (8) · Lex input structure (5) ·
  input buffering & lookahead (5)
- Rotation: `compiler-design/question-bank/master_bank.json` held 25 questions on Unit 1 with the most recent paper
  dated 2026-10-26, so Unit 1 was still under the 50-question cap and was generated again — Set 2 of 2. Unit 1 is now
  at the cap; the next Compiler Design run advances to `(0 + 1) mod 5` → Unit 2, Top-Down Parsing.
- Previous test: **Operating Systems · Unit 1 — Process Management & CPU Scheduling, Set 1 of 2**, 2026-10-26 → [`operating-systems/process-scheduling/gate_os_mock_1_2026-10-26.html`](operating-systems/process-scheduling/gate_os_mock_1_2026-10-26.html)

## Status

| Item | Value |
| --- | --- |
| Papers published | 18 (13 Discrete Mathematics, 1 Algorithms, 1 Databases, 2 Compiler Design, 1 Operating Systems) |
| Units covered | 6 of 16 in Discrete Mathematics; 1 of 7 in Algorithms; 1 of 5 in Databases; 1 of 5 in Compiler Design; 1 of 6 in Operating Systems |
| Questions in the subject banks | 450 (325 Discrete Mathematics, 25 Algorithms, 25 Databases, 50 Compiler Design, 25 Operating Systems) |
| Verified official PYQs | 3 (2 Discrete Mathematics, 1 Databases) |
| Archived sets (earlier runs) | 8 (7 Discrete Mathematics, 1 Compiler Design) |

## Rotation log

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
| 1 | Process Management & CPU Scheduling | `process-scheduling` | 25 | yes |
| 2 | Inter-Process Communication & Synchronization | `synchronization-ipc` | 0 | — |
| 3 | Deadlocks | `deadlocks` | 0 | — |
| 4 | Memory Management & Paging | `memory-paging` | 0 | — |
| 5 | Virtual Memory & Page Replacement | `virtual-memory` | 0 | — |
| 6 | File Systems & Disk Scheduling | `storage-file-systems` | 0 | — |

## Provenance rules used in every test

1. A question is called an official GATE PYQ **only** when its year, paper and official answer key have been verified;
   those records live in `master_bank.json` under `verified_pyqs`.
2. Questions built on a verified PYQ pattern are tagged `GATE_PYQ_VARIATION` and are explicitly *not* official questions.
   Discrete Mathematics Unit 1's single variation is built on the GATE CSE 2014 Set 1 Q53 pattern (formula true exactly
   when a stated number of p, q, r are TRUE; official key B). Databases Unit 1's single variation is built on the
   GATE CSE 2014 Set 3 Q30 pattern (difference of projections over a join; official key D). Operating Systems Unit 1's
   single variation is built on GATE CSE 2021 Set 1 Q25 (minimum achievable average waiting time under a non-preemptive
   scheduler for bursts 16, 20 and 10 arriving at time zero; value 12 ms, which follows from SJF optimality).
3. Everything else is tagged `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS` and is practice material written for this series.
4. Historical questions are never deleted, never counted towards an active test, and are always filed under their
   `data-subtopic` slug.

## Answer key policy

The active mock test reveals nothing before submission. On submit, the file grades itself, marks the correct options,
unlocks the answer-key tab and shows a detailed solution for every question (concept, steps, final answer, why the other
options fail, common misconception, faster method, takeaway). Banked historical questions use a separate expand-on-demand
review interface.

## Known deviations (to be fixed in one pass across every paper)

- `6.4 No raw hex outside :root` is not yet met (the Unit 5 paper carries exactly the same literal hex
  occurrences — 114 — as the shell it was built from, so nothing new was added): the shipped shell uses literal hex
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
- `6.4` also asks for the palette fills to use the `-d` token variants so white numerals clear 4.5:1. The shipped shell
  fills `.pal button.ans/.na/.mrk` with `--green`/`--red`/`--violet` instead of `--green-d`/`--red-d`/`--violet-d`, which
  fails that ratio. The Operating Systems paper inherits the shell unchanged so that parity holds; the correction is a
  four-line CSS change and belongs to the same one-pass re-issue as the raw-hex item.
