# GATE CSE — Daily Mock Test Series

Daily self-contained HTML mock tests for the GATE CSE syllabus, generated for
**SRIHARI V B** (target: GATE CSE 2027).

**Scope.** The series covers all of GATE CSE. Only **Discrete Mathematics** has papers so
far; the other nine syllabus sections are reserved in the dashboard and have no papers yet.
One unit per day, in syllabus order, within each subject.

Open **[`index.html`](index.html)** first — it is the test-series dashboard (views by date, by
subject & unit, and by topic/subtopic, with an in-page launcher for any paper).

Each daily paper is one HTML file styled like the GATE exam interface: question palette, running
timer, MCQ radio buttons, MSQ checkboxes, NAT numeric inputs, and a submit button. It contains:

- **Today's 25-question mock test** — 15 MCQ + 5 MSQ + 5 NAT, difficulty split 10 Easy / 10 Moderate
  / 5 Difficult. No answer, option mark or hint is rendered until **Submit**; the answer payload is
  stored base64-encoded and decoded only on submission.
- **A separate answer key with detailed solutions** (concept, step-by-step reasoning, final answer,
  why the other options fail, common misconception, faster route, takeaway) that unlocks only after
  submission.
- **A preserved historical question bank** in the same file, organised by unit → topic →
  subtopic. Historical questions are a separate review interface, are append-only, and are never
  counted among the active 25.

## Unit rotation — Discrete Mathematics (live)
One unit per day. Day index = (today − 2026-10-26) days, mod 16 → index 0 = Unit 1.
Each subject will carry its own rotation once it has papers.

| # | Unit | # | Unit |
|---|------|---|------|
| 1 | Propositional Logic | 9 | Graph Theory Fundamentals |
| 2 | Predicate & First-Order Logic | 10 | Graph Theory Advanced |
| 3 | Set Theory | 11 | Boolean Algebra & Switching Logic |
| 4 | Relations | 12 | Algebraic Structures |
| 5 | Functions | 13 | Lattices & Posets |
| 6 | Mathematical Induction & Recursion | 14 | Number Theory |
| 7 | Counting & Combinatorics | 15 | Discrete Probability |
| 8 | Recurrence Relations & Generating Functions | 16 | Logic & Proof Techniques |

## Layout

```
index.html                                   dashboard
gate_dm_mock_<unit>_<YYYY-MM-DD>.html        latest paper (root copy)
discrete-mathematics/
  <unit-slug>/
    <subtopic-slug>/
      gate_dm_mock_<unit>_<YYYY-MM-DD>.html  canonical copy of the paper
bank/master_question_bank.json               append-only master bank
archive/                                     superseded files, kept intact
```

The top-level folder is a **subject** directory (`discrete-mathematics/`, and later
`operating-systems/`, `databases/` and so on). `design-tokens.css` holds the canonical
token block and component rules; it is **copied** into each paper's `<style>` rather than
linked, so every paper stays a self-contained single file.

## Provenance policy
A question is labelled an official GATE PYQ **only** when its year, paper and official answer key
are verified. Unverified or partially reconstructed records are marked as such. Nothing is invented.
Questions tagged *Original*, *Textbook-inspired*, *NPTEL-inspired* or *GateOverflow-inspired* are
practice material, not official GATE questions.

## Run log

| Date | Unit | Composition | Difficulty | Note |
|------|------|-------------|------------|------|
| 2026-10-25 (run 1) | 16 — Logic & Proof Techniques | 15 / 5 / 5 | 10 / 10 / 5 | Superseded; its 25 questions are preserved in the historical bank and in `archive/`. |
| 2026-10-25 (run 2) | 16 — Logic & Proof Techniques | 15 / 5 / 5 | 10 / 10 / 5 | Current paper. 25 new questions, no duplication with run 1. |
