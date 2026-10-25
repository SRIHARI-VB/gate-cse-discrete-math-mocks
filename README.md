# gate-cse-mocks — GATE CSE 2027 mock test series

Daily, self-contained mock tests for **GATE CSE 2027**, one unit per day on a 16-unit rotation of Discrete
Mathematics. Every test is a single HTML file that opens in any browser, offline, in a TCS iON–style exam shell:
question palette with the standard status colours, a running countdown, radio MCQ, checkbox MSQ and typed NAT answers,
and no answer, option mark or hint visible until the test is submitted.

## Latest test

- **Unit 16 — Logic & Proof Techniques**, 2026-10-25, Set 3 → [`discrete-mathematics/proof-techniques/gate_dm_mock_16_2026-10-25.html`](discrete-mathematics/proof-techniques/gate_dm_mock_16_2026-10-25.html)
- 25 questions: 15 MCQ · 5 MSQ · 5 NAT · difficulty 10 easy / 10 medium / 5 hard · 60 minutes · 35 marks
- Subtopics: direct proof, contradiction & contrapositive · counterexamples · biconditional (iff) proofs · necessity vs sufficiency
- Earlier sets for the same date are kept in `discrete-mathematics/proof-techniques/archive/`

## Status

| Item | Value |
| --- | --- |
| Mock tests published | 1 |
| Units covered | 1 of 16 |
| Questions in master_bank.json | 75 (50 archived for review, 25 in the active set) |
| Verified official PYQs | 2 |

## Repository layout

```
index.html                                   master portal (test list + topic/subtopic archive)
README.md
discrete-mathematics/
  <unit-slug>/gate_dm_mock_<unit>_<date>.html
  <unit-slug>/archive/                       earlier sets for the same date
  question-bank/master_bank.json             append-only master question bank
```

## Syllabus coverage checklist

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Propositional Logic | `propositional-logic` | 0 | — |
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
3. Everything else is tagged `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS` and is practice material written for this series.
4. Historical questions are never deleted, never counted towards an active test, and are always filed under their
   `data-subtopic` slug.

## Answer key policy

The active mock test reveals nothing before submission. On submit, the file grades itself, marks the correct options,
unlocks the answer-key tab and shows a detailed solution for every question (concept, steps, final answer, why the other
options fail, common misconception, faster method, takeaway). Banked historical questions use a separate expand-on-demand
review interface.
