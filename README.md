# GATE CSE Discrete Mathematics — Daily Practice Mocks

Daily self-contained HTML mock tests for GATE CSE Discrete Mathematics, generated for
**SRIHARI V B** (target: GATE CSE 2027). Each file is a single HTML page styled like the
GATE exam interface (question palette, running timer, MCQ radio / MSQ checkbox / NAT numeric
inputs, submit button) and contains:

- **Today's 25-question mock test** — 15 MCQ + 5 MSQ + 5 NAT, difficulty split ~40% easy /
  40% moderate / 20% hard. No answer, option-mark or hint is shown until **Submit**.
- **A separate answer key with detailed solutions** (concept, step-by-step reasoning, final
  answer, common misconception, faster method) revealed only after submission.
- **A preserved historical question bank**, organised by all 16 units → topic → subtopic.
  Historical questions never count toward the active 25 and are kept append-only.

## Unit rotation
One unit per day. Day index = (today − 2026-10-26) days, mod 16 → index 0 = Unit 1.

| # | Unit |
|---|------|
| 1 | Propositional Logic |
| 2 | Predicate & First-Order Logic |
| 3 | Set Theory |
| 4 | Relations |
| 5 | Functions |
| 6 | Mathematical Induction & Recursion |
| 7 | Counting & Combinatorics |
| 8 | Recurrence Relations & Generating Functions |
| 9 | Graph Theory Fundamentals |
| 10 | Graph Theory Advanced |
| 11 | Boolean Algebra & Switching Logic |
| 12 | Algebraic Structures |
| 13 | Lattices & Posets |
| 14 | Number Theory |
| 15 | Discrete Probability |
| 16 | Logic & Proof Techniques |

## Files
- `gate_dm_mock_<unit>_<YYYY-MM-DD>.html` — that day's mock test + historical bank.
- `bank/master_question_bank.json` — append-only master question bank (all generated questions,
  detailed solutions, verified PYQ provenance).

## Provenance policy
A question is labelled an official GATE PYQ **only** when its year/paper provenance is verified.
Unverified or partially reconstructed records are clearly marked. Nothing is invented.
