# gate-cse-mocks — GATE CSE 2027 mock test series

Daily, self-contained mock tests for **GATE CSE 2027**, one unit at a time on a per-subject unit rotation.
All eleven subjects are now in the series: Discrete Mathematics (16 units), Algorithms (7 units), Databases (5 units), Compiler Design (5 units), Operating Systems (6 units), Engineering Mathematics (5 units), Programming and Data Structures (7 units), Computer Networks (6 units), Theory of Computation (4 units), Digital Logic (4 units) and Computer Architecture (6 units). Every test is a single HTML file that opens in any browser, offline, in a TCS iON–style exam shell:
question palette with the standard status colours, a running countdown, radio MCQ, checkbox MSQ and typed NAT answers,
and no answer, option mark or hint visible until the test is submitted.

## Latest test

- **Algorithms · Unit 3 — Greedy Algorithms, Set 2 of 2**, 2026-10-29 →
  [`algorithms/greedy-algorithms/gate_algo_mock_3_2026-10-29.html`](algorithms/greedy-algorithms/gate_algo_mock_3_2026-10-29.html)
- 25 questions: 15 MCQ · 5 MSQ · 5 NAT · difficulty 10 easy / 10 medium / 5 hard · 60 minutes · 35 marks
- Subtopics: fractional knapsack (6) · Huffman coding (6) · activity selection & interval scheduling (7) ·
  optimal merge patterns (6)
- Rotation: MODE A. One subject was drawn at random with an unseeded draw over all eleven subjects, giving
  **Algorithms**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-29, run 5, unit 3, greedy-algorithms, Set 1 of 2}`. Unit 3 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for 0 days, so step B3 held the rotation and step B4 was never
  reached: **Unit 3, Set 2 of 2**. Unit 3 now holds 50, exactly at the cap, so the next Algorithms run advances
  `(index_of(greedy-algorithms) = 2 + 1) mod 7 = 3` → **Unit 4, Dynamic Programming**.
  No override was used and no second pass has started for this subject.
- Previous test: **Programming and Data Structures · Unit 5 — Binary Search Trees & Balanced Trees, Set 2 of 2**, 2026-10-29 →
  [`programming-data-structures/search-trees/gate_ds_mock_5_2026-10-29.html`](programming-data-structures/search-trees/gate_ds_mock_5_2026-10-29.html)

## Status

| Item | Value |
| --- | --- |
| Papers published (current + archived) | 90 (18 Discrete Mathematics, 6 Algorithms, 6 Databases, 8 Compiler Design, 9 Operating Systems, 7 Engineering Mathematics, 10 Programming and Data Structures, 6 Computer Networks, 12 Theory of Computation, 6 Digital Logic, 2 Computer Architecture) |
| Current papers / archived sets | 45 current · 45 archived |
| Test cards on the portal | 54 |
| Units covered | 9 of 16 in Discrete Mathematics; 3 of 7 in Algorithms; 3 of 5 in Databases; 4 of 5 in Compiler Design; 5 of 6 in Operating Systems; 4 of 5 in Engineering Mathematics; 5 of 7 in Programming and Data Structures; 3 of 6 in Computer Networks; 4 of 4 in Theory of Computation; 3 of 4 in Digital Logic; 1 of 6 in Computer Architecture |
| Questions in the subject banks | 2250 (450 Discrete Mathematics, 150 Algorithms, 150 Databases, 200 Compiler Design, 225 Operating Systems, 175 Engineering Mathematics, 250 Programming and Data Structures, 150 Computer Networks, 300 Theory of Computation, 150 Digital Logic, 50 Computer Architecture) |
| Verified official PYQs | 6 (2 Discrete Mathematics, 1 Databases, 1 Operating Systems, 2 Digital Logic) |
| Archived sets (earlier runs) | 45 (9 Discrete Mathematics, 3 Algorithms, 3 Databases, 4 Compiler Design, 4 Operating Systems, 3 Engineering Mathematics, 5 Programming and Data Structures, 3 Computer Networks, 8 Theory of Computation, 2 Digital Logic, 1 Computer Architecture) |

### Portal data externalised (`data/questions-<subject>.js`)

`index.html` had grown to 3.64 MB because its `data` block carried all 1800 question records with their full
solutions. That file can no longer be delivered by the automation channel, which rejects request bodies above roughly
3 MB, so this run split the archive out of the portal and into one file per subject under `data/`:

- `index.html` keeps the `tests` and `units` tables inline (25 KB) and loads eleven
  `data/questions-<subject>.js` files, each of which registers its array on `window.GATE_BANK`; the portal script
  concatenates them into `D.questions` before rendering, so both views behave exactly as before.
- The portal was never standalone — every card links to a paper by relative path — so the extra files change nothing
  about how it is used, and plain `<script src>` tags load over `file://`, so it still works offline.
- Verified in headless Chromium 153 from `file://`: 44 test cards, 37 unit cards in the archive view, 1800 question
  cards, both tabs switching, no console or page errors. A paper opened the same way shows 25 cards, a 25-button
  palette, no solution text before submit, and reveals 25 solutions plus the answer key on submit.
- The same pass fixed a data-entry slip carried since 2026-10-27: 25 Operating Systems Unit 3 records stored `unit`
  as the string `"3"`, so the portal's `q.unit === u.n` test skipped them and the archive rendered 1775 of 1800
  questions. The values are now integers and the count matches the banks.

### Portal launch row for a unit whose current paper is the newest set

The topic-and-subtopic archive built its "Practise Set n" buttons from `tests[].archives` alone, so a unit whose
current paper carried the newest set showed only the superseded sets and no button for the questions held by the
current paper. The row now lists the archived sets first and then the current paper under its own `set` label, which
is what the Computer Networks Unit 3 card needs: `Practise Set 1` → `archive/gate_cn_mock_3_2026-10-28_run1.html`,
`Practise Set 2` → `gate_cn_mock_3_2026-10-28.html`. Checked in headless Chromium from `file://`: 47 test cards,
40 unit cards, 1975 question cards, every `href` on the page resolving to a file that exists, and no console or page
errors.

### Second pass

Theory of Computation is the first subject to enter a **second pass**: all four of its units (Regular Languages &
Finite Automata, Grammars & Context-Free Languages, Pushdown Automata, Turing Machines & Decidability) reached
`UNIT_QUESTION_CAP = 50`, so step B4 wrapped `(3 + 1) mod 4 = 0` and the series returned to Unit 1 instead of stopping.
Unit 1 therefore holds **75** questions, Unit 2 holds **75** as of 2026-10-28, Unit 3 holds **75** as of the
same date and Unit 4 holds **75** as of 2026-10-29 — the same over-cap state
Discrete Mathematics Unit 16 has carried since before the cap existed, and for the same reason: the rotation must keep
producing 25-question papers. A second pass is not a breach of the cap rule; it is what step B5 prescribes when every
unit of a subject is full. The second pass walks the units in order: run 9 generated Unit 1, run 10 Unit 2, run 11 Unit 3 and run 12 Unit 4,
so the next Theory of Computation run wraps `(3 + 1) mod 4 = 0` and returns to Unit 1, Regular Languages & Finite
Automata, on a third pass.

### Known deviation from the Section 6.4 token rule

The verification checklist item "no hex colour outside `:root`" **fails in the shared shell** and has done since the
first paper: the locked `<style>` block carries raw hex values outside `:root` — 114 occurrences in a paper and 704
in the portal (`#f8fafc`, `#9fb8cc`, `#eaf4fb` and others, mostly hover, focus and border shades that have no token
name yet). Because one shell serves all papers and `6.8` treats shell parity as the hard gate, the block was not
edited for this run — editing it would have changed all 42 current papers at once. The `:root` block itself is
byte-identical across `design-tokens.css`, `index.html` and every paper, which is the part the token contract actually
pins. Closing the deviation needs one coordinated pass: add the missing shades to `:root`, replace the literals, then
re-verify all 38 current papers and 33 archived sets together.

Three further shell-level items are open and are deliberately left to that same coordinated pass, because each of them
touches files this run did not create:

- Two archived Discrete Mathematics `proof-techniques` sets (`archive/gate_dm_mock_16_2026-10-25_run1.html` and
  `_run2.html`) still carry an older `:root` block, so Section 4.1's rule that an archived paper is rebuilt on the
  current interface when the interface changes is not yet satisfied for them. Every other paper, current and archived,
  matches `design-tokens.css` byte for byte.
- `digital-logic/number-systems` holds two "current" papers (`gate_dl_mock_1_2026-10-26.html` and
  `gate_dl_mock_1_2026-10-27.html`); one of them should have moved to `archive/` when the other superseded it.
- Two portal cards point at archived runs although a current paper exists for their unit: the Theory of Computation
  `cfl-grammars` card and the Computer Networks `network-fundamentals-framing` card. Both targets exist and open, so no
  link is broken; the card simply launches an earlier set.

## Rotation log

- **2026-10-29, Algorithms → Unit 3 (Greedy Algorithms), Set 2 of 2.**
  MODE A: one subject was drawn at random with an unseeded `random.choice` over all eleven GATE CSE subjects,
  giving **Algorithms**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-29, run 5, unit 3, greedy-algorithms, Set 1 of 2}`. Unit 3 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and its first paper is dated 2026-10-29, so it had been current for 0 days — well under
  `DAYS_PER_UNIT_MAX = 7`. Step B3 therefore held the rotation and step B4 was never reached: **Unit 3, Set 2 of
  2**, which closes Unit 3 at exactly 50 questions. The next Algorithms run finds the unit at the cap and advances
  `(index_of(greedy-algorithms) = 2 + 1) mod 7 = 3` → **Unit 4, Dynamic Programming**.
  No override was used and no second pass has started for this subject.
- Coverage this run: all four Unit 3 subtopics — fractional knapsack (6), Huffman coding (6), activity selection
  and interval scheduling (7), optimal merge patterns (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="algorithms"`,
  `data-unit="greedy-algorithms"`, `data-unit-number="3"`, its subtopic slug, its type, its lowercase difficulty and
  its source tag.
- All 25 items are new: ids `ALG-U3-Q26`..`ALG-U3-Q50` did not exist in the bank, and no stem repeats a Set 1
  question. Set 2 deliberately moves onto ground Set 1 left untouched — ratio ties and an exactly-full knapsack,
  the Huffman depth bound and merge-queue reinsertion, interval-graph colouring and weighted interval scheduling,
  and the structure of the merge tree.
- Every numeric answer was recomputed by script, not by hand: fractional fills 111, 71, 150 and 59 (subset and
  ratio enumerations), Huffman costs 28, 33, 228 and the six-symbol depth of 3, merge costs 90, 19 and 119,
  and the interval sweeps 3, 4 and 4.
- Shell: built from the same shell as every other paper. The head, palette, key view, JavaScript and footer are
  byte-identical to the superseded Set 1, which was archived as
  `archive/gate_algo_mock_3_2026-10-29_run1.html` with its questions, options, answers, solutions and duration frozen.

- **2026-10-29, Programming and Data Structures → Unit 5 (Binary Search Trees & Balanced Trees), Set 2 of 2.**
  MODE A: one subject was drawn at random with an unseeded `random.choice` over all eleven GATE CSE subjects,
  giving **Programming and Data Structures**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-29, run 9, unit 5, search-trees, Set 1 of 2}`. Unit 5 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and its first paper is dated 2026-10-29, so it had been current for 0 days — well under
  `DAYS_PER_UNIT_MAX = 7`. Step B3 therefore held the rotation and step B4 was never reached: **Unit 5, Set 2 of
  2**, which closes Unit 5 at exactly 50 questions. The next Programming and Data Structures run finds the unit at
  the cap and advances `(index_of(search-trees) = 4 + 1) mod 7 = 5` → **Unit 6, Heaps & Priority Queues**.
  No override was used and no second pass has started for this subject.
- Coverage this run: all four Unit 5 subtopics — BST insertion and deletion (7), AVL trees and rotations (6),
  B-trees and B+ trees (6), tries (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium /
  5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="programming-data-structures"`,
  `data-unit="search-trees"`, `data-unit-number="5"`, its subtopic slug, its type, its lowercase difficulty and its
  source tag.
- All 25 items are new: ids `DS-U5-Q26`..`DS-U5-Q50` did not exist in the bank, and the stem of every item was
  checked against the 225 Programming and Data Structures records already held (tags stripped, case and
  punctuation removed): zero id overlap, no duplicated stem, and no item is a numeric swap of a Set 1 question.
  The set deliberately moves onto ground Set 1 left untouched — one-child deletion, insertion orders that rebuild
  a given shape, the balance-factor sign convention, maximum-node counts, split cascades, and the memory cost of
  an array-based trie. No item is a `GATE_PYQ_VARIATION`: `verified_pyqs` is empty for this subject, so nothing on
  this paper is claimed as an official GATE question. Every item is `STANDARD_TEXTBOOK` (13) or
  `ORIGINAL_SYNTHESIS` (12).
- **Every countable answer was recomputed by script, not by hand.** A BST was built by insertion and every
  deletion performed by the stated rule: the seven-key balanced tree 40,20,60,10,30,50,70 has **0** nodes with
  exactly one child; the preorder of 15,10,25,5,20,30 is **15, 10, 5, 25, 20, 30**; the height of
  8,4,12,2,6,10,14 is **2**; splicing the one-child node 40 out of the ten-key tree makes **35** the right child
  of 30; deleting 30 by successor from 50,30,70,20,40,60,80,35,45,65 leaves **4** leaves. An AVL implementation
  with the four rotation cases confirmed the preorder of 15,10,20,5,12,25,30 as **15, 10, 5, 12, 25, 20, 30**
  (one single rotation), the root of 1..7 as **4** (four elementary rotations), and the rotation count of
  100,50,150,25,75,60,90,55,58 as **4** elementary rotations, two RL and one LR case, final preorder
  75, 50, 25, 58, 55, 60, 100, 90, 150. AVL node bounds: maximum nodes at height 3 is **15** = 2⁴ − 1 and the
  minimum-node sequence 1, 2, 4, 7, 12, 20 makes height 5 reachable with exactly 20 nodes, which is why the
  statement that it cannot be is FALSE. B-tree arithmetic: minimum keys in an order-4 tree of height 3 is
  **1 + 2 + 4 + 8 = 15**; minimum keys in an order-5 tree of height 1 is **1 + 2·2 = 5**; inserting
  10,20,30,40,50 into an order-3 tree was simulated split by split and leaves the root holding **20 and 40**.
  Trie node counts were produced by building the trie: banana → **7**, in/inn/int → **5**, and
  ant/ante/anti/bat/batch/ban/band → **13**.
- The correct option is spread 3 A / 4 B / 4 C / 4 D across the 15 MCQ, and the five MSQ answer sets are
  (A,B), (A,B,C), (A,B,C), (A,B,C) and (A,B,C) — checked by script.
- Shell parity: the paper was generated by replacing only the payload regions of the Unit 5 Set 1 shell — the
  `<style>` block, the `:root` block and the exam `<script>` are byte-identical to it, verified by direct
  comparison of the extracted blocks, and the palette markup is unchanged. The superseded Set 1 paper moved to
  `archive/gate_ds_mock_5_2026-10-29_run1.html` with its content frozen, and the portal card for 2026-10-29 now
  carries `set: "Set 2 of 2"` with `archives[0]` pointing at that file. The paper is filed only at
  `programming-data-structures/search-trees/`; nothing was written at the repository root.
- **2026-10-29, Algorithms → Unit 3 (Greedy Algorithms), Set 1 of 2.** MODE A: one subject was drawn uniformly at
  random with an unseeded `random.SystemRandom()` draw over the five subjects that had no paper dated 2026-10-29 —
  engineering-mathematics, digital-logic, computer-architecture, algorithms, computer-networks — at index 3 of 5 in
  that fixed list order, giving **Algorithms**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 4, unit 2, sorting-divide-conquer, Set 2 of 2}`. Unit 2 held **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(sorting-divide-conquer) = 1 + 1) mod 7 = 2` → **Unit 3, Greedy Algorithms** (`greedy-algorithms`).
  Unit 3 had no folder and no paper, so this is **Set 1 of 2**, nothing was archived, and no override was used.
  Unit 3 now holds 25 questions, below the cap, so the next Algorithms run re-selects Unit 3 as Set 2 of 2 before
  advancing to `(index_of(greedy-algorithms) = 2 + 1) mod 7 = 3` → Unit 4, Dynamic Programming.
- Coverage this run: all four Unit 3 subtopics — fractional knapsack (7), Huffman coding (6), activity selection and
  interval scheduling (6), optimal merge patterns (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="algorithms"`,
  `data-unit="greedy-algorithms"`, `data-unit-number="3"`, its subtopic slug, its type, its lowercase difficulty and
  its source tag.
- All 25 items are new: ids `ALG-U3-Q01`..`ALG-U3-Q25` did not exist in the bank, and every stem was checked against
  the 2175 records already held in the eleven subject banks (tags stripped, case and punctuation removed): zero id
  overlap and no duplicated stem. No item is a `GATE_PYQ_VARIATION` — `verified_pyqs` is empty for Algorithms, so
  nothing on this paper is claimed as an official GATE question. Every item is `STANDARD_TEXTBOOK` (15) or
  `ORIGINAL_SYNTHESIS` (10).
- **Every numeric answer was recomputed by script, not by hand.** Ratio-greedy fills: capacity 15 over (10,60),
  (5,25), (10,40) gives **85**; capacity 20 over (8,40), (6,36), (5,25), (4,16), (10,50) gives **106**, with the
  knapsack exactly full. Huffman merge-cost sums: frequencies 5, 9, 12, 13, 16, 45 give **224**; frequencies
  1, 1, 2, 3, 5 give **25**, cross-checked against the leaf depths (1, 2, 3, 4, 4). Activity selection on the
  eleven-interval instance gives **4**, confirmed by exhaustive search over all subsets; the five touching intervals
  give **5**. Optimal merge costs: 5, 10, 20, 30, 30 → **205**; 2, 3, 4, 5, 6 → **45**. Value per unit weight of a
  12 kg, ₹180 item is **15**. The 0/1 counterexample was checked by enumerating all subsets: ratio-greedy returns
  **30** while the optimum is **40**.
- Shell parity: the paper was generated from the same shell as every other current paper — the `<style>` block and
  the exam `<script>` are byte-identical to the 2026-10-29 Compiler Design paper (verified by direct comparison of
  the extracted blocks) — and only the payload regions were replaced. One defect in that shell was fixed here: the
  palette card had been emitted as a bare `<div class="card">` with a stray closing `</aside>` and no opening
  `<aside class="side">`, so the sticky-palette rule `aside.side` never applied. This paper emits the palette inside
  `<aside class="side">`; the other current papers still carry the old markup and should be rebuilt in one pass.

- **2026-10-29, Compiler Design → Unit 4 (Syntax-Directed Translation & Intermediate Code), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random with an unseeded `random.SystemRandom()` draw over all eleven subjects, giving
  **Compiler Design** — a subject that had no paper dated 2026-10-29, so the day's paper again lands where it has not
  already been served. `runs[]` sorted by `(date, run)` gives the most recent paper as `{date 2026-10-28, run 8,
  unit 4, sdt-intermediate-code, Set 1 of 2}`. Unit 4 held **25** questions, below `UNIT_QUESTION_CAP = 50`, and had
  been current for 1 day, so step B3 held the rotation and step B4 was not reached: **Unit 4, Set 2 of 2**. Unit 4
  now holds 50, at the cap, so the next Compiler Design run advances `(index_of(sdt-intermediate-code) = 3 + 1) mod 5
  = 4` → **Unit 5, Runtime Environments & Code Optimization**. No override was used and no second pass has started for
  this subject.
  The 25 questions were checked against all 175 banked Compiler Design items with a string-normalised comparison
  (tags stripped, case and punctuation removed): the highest stem similarity to any earlier question is **0.74** and the
  next highest **0.71**, so Set 2 does not repeat Set 1 — every item is a distinct question, not a swap of numbers. Coverage is all four subtopics — S-attributed/L-attributed (6),
  three-address code (7), syntax trees and DAGs (6), type checking (6) — with 15 MCQ, 5 MSQ, 5 NAT and a
  10/10/5 easy/medium/hard split. No question is an official GATE PYQ: `verified_pyqs` is empty for this subject and
  nothing in this paper is claimed as official.
  Shell parity: the paper was generated by replacing only the payload regions of the Unit 4 Set 1 shell, so the
  `<style>` block, the exam `<script>`, the palette and the meta strip are byte-identical to the previous paper —
  verified by direct comparison of the extracted `<style>` and `<script>` blocks and the palette markup. The
  superseded Set 1 paper moved to `archive/gate_cd_mock_4_2026-10-28_run1.html` with its content frozen, and the
  portal card for 2026-10-28 was repointed at that archive file.

- **2026-10-29, Programming and Data Structures → Unit 5 (Binary Search Trees & Balanced Trees), Set 1 of 2.**
  MODE A: one subject was drawn uniformly at random with an unseeded `random.SystemRandom()` draw over the seven
  subjects without a paper dated 2026-10-29, giving **Programming and Data Structures**.
  `runs[]` sorted by `(date, run)` gives the most recent paper as `{date 2026-10-28, run 8, unit 4,
  trees-traversals, Set 2 of 2}`. Unit 4 held **50** questions, at `UNIT_QUESTION_CAP`, so step B3 failed and step
  B4 advanced exactly one unit: `(index_of(trees-traversals) = 3 + 1) mod 7 = 4` → **Unit 5, Binary Search Trees &
  Balanced Trees**. Unit 5 held no questions, so this is **Set 1 of 2**. No override was used and no second pass has
  started for this subject. The next Programming and Data Structures run holds Unit 5 at 25 questions, under the cap
  and under `DAYS_PER_UNIT_MAX`, so it will generate Unit 5 again as Set 2 of 2.
- Coverage this run: all four Unit 5 subtopics — BST insertion and deletion (7), AVL trees and rotations (6),
  B-trees and B+ trees (6), tries (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard;
  marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="programming-data-structures"`,
  `data-unit="search-trees"`, `data-unit-number="5"`, its subtopic slug, its type, its lowercase difficulty and its
  source tag.
- All 25 items are new: ids `DS-U5-Q01`..`DS-U5-Q25` did not exist in the bank, and every stem was checked against
  the 2125 records already held in the eleven subject banks (tags stripped, case and punctuation removed): zero id
  overlap and no duplicated stem. No item is a `GATE_PYQ_VARIATION` — `verified_pyqs` is empty for this subject, so
  nothing on this paper is claimed as an official GATE question. Every item is `STANDARD_TEXTBOOK` (15) or
  `ORIGINAL_SYNTHESIS` (10).
- **Every countable answer was recomputed by script, not by hand.** A BST was built by insertion and every deletion
  performed by the stated rule: the root after deleting 50 by successor is **60**; the sum of depths of
  20,10,30,5,15,25,35,3,7,12,17 is **22**; after deleting 25 the left child of 45 is **35**; the postorder after
  deleting 2 from 4,2,6,1,3,5,7 is **1, 3, 5, 7, 6, 4**; after deleting 20 from the fifteen-key tree the root is 22
  and the sum of the fourteen remaining depths is **31**. An AVL implementation with the four rotation cases
  confirmed: 10,20,30 → root **20** with one single rotation; 30,20,10,25,28 → preorder **20, 10, 28, 25, 30**;
  30,10,20 → exactly **one double (LR) rotation and no single rotation** while 10,20,30 is a single rotation and
  20,10,30 needs none; 50,40,60,30,45,55,70,20 → **0** rotations, the deliberate trap. The AVL minimum-node
  recurrence gives **12** nodes at height 4 (1, 2, 4, 7, 12, 20, 33). B-tree arithmetic: the fan-out bound
  6n + 8(n−1) ≤ 4096 gives **293** (4094 bytes used) and 294 overflows at 4108; the maximum key count of an order-5
  B-tree of height 2 is **124** = 5³ − 1. Trie node counts were produced by building the trie: {cat, car, dog} →
  **8**, the eight-string set bear/bell/bid/bull/buy/sell/stock/stop → **22**, {do, dog, done, cat, car} → **10**.
  Every one of these reproduced the drafted answer, so no option or solution had to be rewritten.
- The correct option is spread 4 A / 4 B / 4 C / 3 D across the 15 MCQ, and the five MSQ answer sets are (B,D),
  (A,B,C), (A,B,C), (A,B,D) and (A,C,D) — checked by script.
- The paper is filed only at `programming-data-structures/search-trees/`; nothing was written at the repository
  root, and no paper was superseded, because Unit 5 had no previous paper — the Unit 4 paper stays current in its
  own folder.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it.
  With the ten payload regions normalised to placeholders (title, brand, sub-line, candidate ID, bank tab label,
  meta strip, `#qhost`, bank tab, About tab, payload), the remaining **27 640 bytes are byte-identical** to the
  shell extracted from the 2026-10-28 Unit 4 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view, the Question Bank tab, the About tab and the footer are unchanged. The `:root` block is
  byte-identical across the new paper, `index.html` and `design-tokens.css`.
- The paper was exercised in headless Chromium 153 from `file://` before shipping (**41 checks, all passing**):
  nothing is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the
  question pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card
  visible, every input enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering,
  marking and Clear response, `cur` follows the current question, and Save & Next / Previous move the selection;
  all four tabs open and the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25
  `ok` palette buttons, 25 key cards and a filled solution on every card; a paper whose five MSQ are each one
  option short scores **25 / 35** with 5 wrong; an all-wrong paper scores **0 / 35** and an empty paper **0 / 35**
  with 25 `skip` buttons, so the exact-set MSQ rule and the absence of negative marking both hold in code; every
  card carries all eight data attributes with lowercase difficulty values; the Question Bank tab renders **200**
  cards under four unit accordions with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **2150** questions. Its data block was updated in place: the new Unit 5 record was inserted
  at the head of `tests` with an empty `archives` list, and the 25 new records were appended to
  `data/questions-programming-data-structures.js`. The static header strings had drifted again — they still read
  2025 records and 48 test cards — and were recomputed from the data to read 65 units, **2150** solved questions
  banked, **51** test cards, 2150 records and 281 subtopics. A headless run of the portal renders the new paper
  first, every relative link resolving against the repository tree, and no console or page errors.
- Hygiene: the paper is filed at exactly one path, `programming-data-structures/search-trees/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (87 files, 44 current and 42 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the
  literal hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry
  an older `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an
  archived run while a current paper exists; the two pre-existing stem collisions inside Algorithms Unit 1; and the
  unclosed `#view-about` in the shared shell.

- **2026-10-29, Theory of Computation → Unit 4 (Turing Machines & Decidability), Set 1 of 2 (second pass).** MODE A:
  one subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()`
  draw (draw index 6 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Theory of Computation**. Operating Systems and
  Databases already had a paper dated 2026-10-29, so the draw ran over the remaining nine subjects. `runs[]` sorted
  by `(date, run)` gave the most recent paper as `{date 2026-10-28, run 11, unit 3, pushdown-automata, Set 1 of 2
  (second pass)}`. Unit 3 held **75** questions, above `UNIT_QUESTION_CAP = 50`, so step B4 advanced
  `(index_of(pushdown-automata) = 2 + 1) mod 4 = 3` → Unit 4. Unit 4 held **50** questions, at the cap, and every
  other unit of the subject is at or above it (75, 75, 75, 50), so the second pass continues (step B5) and Unit 4
  was generated as **Set 1 of 2 (second pass)**, taking it from 50 to 75 questions. No override was used.
- Coverage this run: all five Unit 4 subtopics, five questions each — standard TM models & variants, recursive vs
  recursively enumerable, the halting problem & undecidability, Rice's theorem & reductions, and the Chomsky
  hierarchy summary. Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks
  15 × 1 + 10 × 2 = 35. Every question carries `data-subject="theory-of-computation"`,
  `data-unit="turing-machines-decidability"`, `data-unit-number="4"`, its subtopic slug, its type, its lowercase
  difficulty and its source tag.
- All 25 items are new: ids `TOC-U4-Q51`..`TOC-U4-Q75` did not exist in the bank, and every stem was compared with
  the 2075 normalised stems already held in the eleven subject banks (tags stripped, case and punctuation removed):
  zero collisions and no id overlap. Three first drafts opened with a lead-in already used elsewhere — "Which of
  the following problems are decidable? Select all that apply" (identical to `TOC-U4-S2-Q14`), "Consider the
  following five languages, where M ranges over all Turing machines" (same opening as `TOC-U4-Q09`) and "Which of
  the following statements about the Chomsky hierarchy are TRUE" (same opening as `TOC-U4-Q23`) — so Q64, Q65 and
  Q74 were reworded to name their subject matter before the paper was built. No item is a `GATE_PYQ_VARIATION` —
  `verified_pyqs` is empty for this subject — so nothing on this paper is claimed as an official GATE question.
  Every item is `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10).
- **Every countable answer was recomputed by script, not by hand.** The step count of Q55 was produced by
  simulating the stated increment machine cell by cell: on `1011` it executes **8** transitions (four scans, one
  turnaround, two carries, one final write) and leaves `1100`, which is 12 = 11 + 1; the same simulator gives 10
  steps on `1111`, 6 on `1000` and 3 on `0`, so the counting convention is exercised on more than the shipped
  case. The gadget count of Q69 was settled by enumerating every string up to length 11 over `{0, 1}` and keeping
  those the stated `M′` accepts: exactly **7** (ε, 0, 1, 00, 01, 10, 11), because the budget `|x|` only fails to
  reach the halt at step 3 for lengths 0, 1 and 2. The two trivial languages of Q60 (∅ and Σ*, both recursive hence
  r.e.) and the finite-language argument of Q65(iv) were checked against the definitions rather than asserted.
- The correct option is spread 4 A / 4 B / 4 C / 3 D across the 15 MCQ, and the five MSQ answer sets are (A,B),
  (A,C), (B,D), (A,D) and (A,B,C) — checked by script.
- The new paper is filed only at `theory-of-computation/turing-machines-decidability/`; the superseded Set 2 paper
  moved into that unit's `archive/` as `gate_toc_mock_4_2026-10-28_run2.html` unchanged, so the unit folder holds
  exactly one current paper and nothing was written at the repository root.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it.
  With the eight payload regions normalised to placeholders (title, header sub-line, candidate ID, bank tab label,
  meta strip, `#qhost`, bank tab, About tab, payload), the remaining **27 968 bytes are byte-identical** to the
  shell extracted from the 2026-10-28 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view, the Question Bank tab, the About tab and the footer are unchanged. The `:root` block is
  byte-identical across the new paper, its archived predecessor, `index.html` and `design-tokens.css`.
- The paper was exercised in headless Chromium 153 from `file://` before shipping (**58 checks, all passing**):
  nothing is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the
  question pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card
  visible, every input enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering,
  marking and Clear response, `cur` follows the current question, and Save & Next / Previous move the selection;
  all four tabs open and the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25
  `ok` palette buttons, 25 key cards and a filled solution on every card; every card carries all eight data
  attributes with lowercase difficulty values and the correct subject/unit pair; the Question Bank tab renders
  **275** cards under four unit accordions with no active question repeated; the About tab carries its three
  sections; and the page shows no horizontal overflow at the 1200 px container. A separate scoring harness added
  **6 more checks**: an empty paper scores **0 / 35** with 25 `skip` buttons, a paper whose five MSQ are each one
  option short scores **25 / 35** with 5 wrong, and a paper answering every MCQ and NAT wrongly scores **0 / 35** —
  so the exact-set MSQ rule and the absence of negative marking both hold in code.
- `index.html` holds all **2100** questions. Its data block was updated in place: the new Unit 4 record replaced
  the 2026-10-28 record at the head of `tests`, with `archives` pointing at the frozen run2 file and at the
  2026-10-27 run1 file, and the 25 new records were appended to `data/questions-theory-of-computation.js`. The
  static header strings were recomputed from the data and now read 65 units, 2100 solved questions banked and 281
  subtopics. A headless run of the portal renders **49 test cards** with the new paper first, **41** unit cards in
  the archive view, **2100** archive question cards, three "Practise Set" buttons on the Theory of Computation
  Unit 4 card and no console or page errors; every relative link on the page resolves against the repository tree.
- Hygiene: the paper is filed at exactly one path, `theory-of-computation/turing-machines-decidability/`, and
  nowhere else; `find . -name "*.html"` returns `index.html` plus one file per paper (85 files, 42 current and 42
  archived); no temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the
  literal hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry
  an older `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an
  archived run while a current paper exists; the two pre-existing stem collisions inside Algorithms Unit 1; and the
  unclosed `#view-about` in the shared shell.

- **2026-10-29, Operating Systems → Unit 5 (Virtual Memory & Page Replacement), Set 1 of 2.** MODE A: one subject was
  drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 8
  of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic, computer-architecture,
  programming-data-structures, algorithms, theory-of-computation, compiler-design, operating-systems, databases,
  computer-networks), giving **Operating Systems**. `runs[]` sorted by `(date, run)` gave the most recent paper as
  `{date 2026-10-28, run 8, unit 4, memory-paging, Set 2 of 2}`. Unit 4 held **50** questions, at
  `UNIT_QUESTION_CAP`, so step B4 advanced `(3 + 1) mod 6 = 4` → Unit 5. Unit 5 held no questions, so this is
  **Set 1 of 2**; no override was used and no second pass has started for this subject.
- Coverage this run: all four Unit 5 subtopics — demand paging and the page-fault rate (7 questions), FIFO/OPT/LRU
  replacement (6), Belady's anomaly (6), thrashing and the working-set model (6). Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="operating-systems"`, `data-unit="virtual-memory"`, `data-unit-number="5"`, its subtopic slug, its
  type, its lowercase difficulty and its source tag.
- Nothing on this paper is claimed as an official GATE question. The bank holds one verified PYQ
  (`PYQ-GATE2021S1-Q25`, GATE CSE 2021 Set 1 Q25, NAT, official answer 12), and it belongs to Unit 1, not to this
  unit; no virtual-memory previous-year question has been verified against an official paper and key, so every item
  here is `STANDARD_TEXTBOOK` (10) or `ORIGINAL_SYNTHESIS` (15).
- Every number in this set was recomputed by script rather than by hand: the FIFO, LRU and OPT traces on both
  reference strings at 3 and 4 frames (giving FIFO 9 → 10 for the Belady pair, LRU 10 → 8, OPT 7 → 6 on
  `1,2,3,4,1,2,5,1,2,3,4,5`, and OPT 9 < LRU 12 < FIFO 15 on the twenty-reference string), the effective-access-time
  arithmetic (1099.9 → 1100 ns, 1120 ns, 429 ns), the fault-rate bound (11 per 10⁶ references) and the working-set
  window count (4). No Unit 5 id or stem collides with the 200 banked Operating Systems items: ids are
  `OS-U5-Q01`..`OS-U5-Q25`.
- **2026-10-29, Databases → Unit 3 (Database Normalization), Set 2 of 2.** MODE A: one subject was drawn from the
  11 GATE CSE subjects with a seeded `random.Random` draw (seed = `sha256("gate-mock-2026-10-29")`, draw index 9 of
  11 in the fixed list order), giving **Databases**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 4, unit 3, normalization, Set 1 of 2}`. Unit 3 held **25** questions — below
  `UNIT_QUESTION_CAP = 50` — and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and
  the unit was generated again rather than advanced. No override was used.
- Coverage this run: all five Unit 3 subtopics, five questions each — functional dependencies and Armstrong's
  axioms, closure of attribute sets and keys, 1NF/2NF/3NF/BCNF, lossless join and dependency preservation, and
  multivalued dependencies and 4NF. Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard;
  marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="databases"`, `data-unit="normalization"`,
  `data-unit-number="3"`, its subtopic slug, its type, its lowercase difficulty and its source tag.
- Set 2 repeats nothing from the 25 banked Unit 3 items: ids `DB-U3-Q26`..`DB-U3-Q50` are new and every stem was
  compared with all 125 banked Databases stems (tags stripped, case and punctuation removed): zero collisions and no
  id overlap. No item is a `GATE_PYQ_VARIATION` — no normalization previous-year question has been verified against
  an official paper and key — so nothing on this paper is claimed as an official GATE question. Every item is
  `STANDARD_TEXTBOOK` (9) or `ORIGINAL_SYNTHESIS` (16).
- **Every answer was recomputed by script, not by hand.** Closure and candidate-key enumeration for the key
  questions, superkey counting by subset enumeration, minimal-cover construction by the split-then-prune algorithm,
  projection-and-union tests for dependency preservation, and a chase (tableau) implementation for losslessness.
  **That pass corrected one first draft**: Q35 originally claimed 12 superkeys for
  `F = {AB → C, BC → D, CD → E, DE → A}` because a third candidate key `{B, D, E}` had been missed; the true count
  is 13, and both the options and the full solution were rewritten before the paper was built.
- The paper is filed only at `databases/normalization/`. Set 1 moved to
  `databases/normalization/archive/gate_db_mock_3_2026-10-28_run1.html` with its content frozen, so the unit folder
  holds exactly one current paper and nothing was written at the repository root.
- Set 2 is built from the same shell as every earlier paper: identical `<style>` block (hash `1ad7d3a6`), identical
  `<script>` block (hash `70fcdfcb`), identical structural markup; only the payload, the meta strip, the header and
  the tab contents differ. The Question Bank tab inside the paper lists the 125 banked items that are not in the
  active set, and the portal's `data/questions-databases.js` now carries all 150.
- Unit 3 now sits exactly at `UNIT_QUESTION_CAP = 50`, so the next Databases run advances to Unit 4,
  Transactions & Concurrency Control. Units 4–5 of Databases are still untouched.

- **2026-10-28, Theory of Computation → Unit 3 (Pushdown Automata), Set 1 of 2 (second pass).** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw
  index 6 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Theory of Computation** — the same subject as the
  previous run, which is what a uniform unseeded draw does one time in eleven. All eleven subjects already had a
  paper dated 2026-10-28, so the draw ran over the full list. `runs[]` sorted by `(date, run)` gives the most recent
  paper as `{date 2026-10-28, run 10, unit 2, cfl-grammars, Set 1 of 2 (second pass)}`. Unit 2 held **75**
  questions, above `UNIT_QUESTION_CAP = 50`, so step B3 failed and step B4 advanced exactly one unit:
  `(index_of(cfl-grammars) = 1 + 1) mod 4 = 2` → **Unit 3, Pushdown Automata**. Every Theory of Computation unit is
  at or above the cap (75, 75, 50, 50), so the second pass begun at run 9 continues (step B5) and Unit 3 was
  generated as **Set 1 of 2 (second pass)**, taking it from 50 to 75 questions. No override was used.
- Coverage this run: all four Unit 3 subtopics — deterministic PDA (7), nondeterministic PDA (6), acceptance by
  empty store against acceptance by final state (5), equivalence with context-free grammars (7). Composition
  15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question
  carries `data-subject="theory-of-computation"`, `data-unit="pushdown-automata"`, `data-unit-number="3"`, its
  subtopic slug, its type, its lowercase difficulty and its source tag.
- Set 1 of the second pass repeats nothing from the 50 banked Unit 3 items: ids `TOC-U3-Q51`..`TOC-U3-Q75` are new
  and every stem was compared with all 250 banked Theory of Computation stems (tags stripped, case and punctuation
  removed): zero collisions and no id overlap. Five first drafts did collide on their generic lead-in ("Select every
  statement that is TRUE"), so Q61, Q66, Q71, Q74 and Q75 were reworded to name their subject matter before the
  paper was built. No item is a `GATE_PYQ_VARIATION` — no theory-of-computation previous-year question on this unit
  has been verified against an official paper and key, so nothing on this paper is claimed as an official GATE
  question. Every item is `STANDARD_TEXTBOOK` (19) or `ORIGINAL_SYNTHESIS` (6).
- **Every machine-dependent answer was recomputed by simulation, not by hand.** A configuration-graph search was
  run over each machine in the paper: the DPDA of Q51 accepts exactly `{aⁿbⁿ : n ≥ 1}` on every word up to length 6
  (ε, b, ba, abb, aab rejected; ab, aabb, aaabbb accepted); the DPDA of Q57 with all three states final accepts
  exactly `{aⁱbʲ : i ≥ j ≥ 0}` up to length 6 and therefore **6** words of length ≤ 3 (ε, a, aa, ab, aaa, aab); the
  NPDA of Q60 accepts exactly the palindromes up to length 6 (checked word by word against `w == wᴿ`) and therefore
  **9** words of length ≤ 3 (ε, a, b, aa, bb, aaa, aba, bab, bbb); and the empty-stack PDA of Q65 accepts only `ab`
  among its four options, its language being `{aⁿbⁿ : n ≥ 1}` up to length 4. The grammar-to-NPDA stack height of
  Q73 was obtained by searching every accepting run of the construction on `aabb` and taking the maximum: **4**
  (`Z₀ b b a`). The two counting questions follow from definitions that were checked arithmetically (5 moves for a
  5-symbol input with no ε-moves; 9 steps for a GNF derivation of a 9-symbol word). **Two first drafts were wrong
  and were corrected by that pass**: Q57 originally claimed `{aⁱbʲ : i ≥ j}` for a machine that rejects `aab`, and
  Q60 originally counted 7 palindromes of length ≤ 3, overlooking `aaa` and `bbb`. Both were rewritten before the
  paper was built.
- The correct option is spread 4 A / 4 B / 4 C / 3 D across the 15 MCQ, and the five MSQ answer sets are (A,B,D),
  (A,C,D), (A,B,D), (A,B,C) and (A,C,D) — checked by script.
- The new paper is filed only at `theory-of-computation/pushdown-automata/`; the superseded Set 2 paper was moved
  into that unit's `archive/` as `gate_toc_mock_3_2026-10-27_run2.html` unchanged, so the unit folder never held two
  current papers and no root copy was written. The portal card now launches the 2026-10-28 paper and links both
  2026-10-27 sets from `archive/`.
- The Question Bank tab inside the paper lists the **250** banked items that are not part of the active set — 75 of
  Unit 1, 75 of Unit 2, the 50 of Unit 3 and the 50 of Unit 4 — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active questions do not appear there (verified: none of the ids `TOC-U3-Q51`..`TOC-U3-Q75`
  occurs in the bank tab), and no unit is reported as empty because all four have banked questions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions normalised to placeholders (title, header sub-line, candidate ID, bank tab label, meta
  strip, `#qhost`, bank tab, About tab, payload), the remaining **27 621 bytes are byte-identical** to the shell
  extracted from the previous Theory of Computation paper, so the `<style>` block, the exam `<script>`, the palette,
  the answer-key view, the Question Bank tab, the About tab and the footer are unchanged. The `:root` block is
  byte-identical across the new paper, `index.html` and `design-tokens.css`, and the paper carries the same 91
  literal hex values outside `:root` as its predecessor, so the known Section 6.4 deviation below is untouched and
  was not partially fixed for one paper.
- The paper was exercised in headless Chromium from `file://` before shipping (**44 checks, all passing**): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question
  pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible,
  every input enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and
  Clear response, `cur` follows the current question, and Save & Next / Previous move the selection; all four tabs
  open and the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25 `ok` palette
  buttons, 25 key cards and a filled solution on every card; a paper with one MSQ one option short scores
  **33 / 35**, confirming that an MSQ earns nothing unless the exact set is selected; an empty paper scores
  **0 / 35** with 25 `skip` buttons, confirming that there is no negative marking; every card carries all seven
  data attributes with lowercase difficulty values; the Question Bank tab renders 250 cards under four accordions
  with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **2025** questions. Its data block was updated in place: the Unit 3 record now carries the
  2026-10-28 paper and both 2026-10-27 sets as archives, and the 25 new records were appended to
  `data/questions-theory-of-computation.js`. The static header strings were recomputed from the data and now read
  65 units, 48 test cards, 2025 solved questions / records and 281 subtopics — the previous strings still read 1950
  after run 9 had already taken the banks to 2000, so this run corrected that drift. A headless run of the portal
  renders **48 test cards** with the new paper first, **2025** archive question cards, and no console or page
  errors.
- One inherited data gap was closed on the way: the 25 records of run 9 (`TOC-U2-Q51`..`TOC-U2-Q75`) had been
  written without `question_html` or `subtopic_label`, which the paper's Question Bank tab needs. Both fields were
  backfilled from `data/questions-theory-of-computation.js` and from the sibling records of the same subtopic; no
  question text, option, answer or solution was altered.
- Hygiene: the paper is filed at exactly one path, `theory-of-computation/pushdown-automata/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (82 files, 41 current and 40 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the
  literal hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry
  an older `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an
  archived run while a current paper exists; the two pre-existing stem collisions inside Algorithms Unit 1; and the
  unclosed `#view-about` in the shared shell.

- **2026-10-28, Theory of Computation → Unit 2 (Grammars & Context-Free Languages), Set 1 of 2 (second pass).** MODE A:
  one subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()`
  draw (draw index 6 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Theory of Computation**. All eleven subjects already had a
  paper dated 2026-10-28, so the draw ran over the full list. `runs[]` sorted by `(date, run)` gives the most recent
  paper as `{date 2026-10-28, run 9, unit 1, regular-languages-fa, Set 1 of 2 (second pass)}`. Unit 1 held **75**
  questions, above `UNIT_QUESTION_CAP = 50`, so step B3 failed and step B4 advanced `(index_of(regular-languages-fa) =
  0 + 1) mod 4 = 1` → Unit 2, Grammars & Context-Free Languages. Every Theory of Computation unit is at or above the
  cap (75, 50, 50, 50), so the second pass continues (step B5) and this is **Set 1 of 2 (second pass)** for Unit 2,
  taking it from 50 to 75 questions. No override was used.
- Coverage this run: all four Unit 2 subtopics — CFG derivation trees (7), ambiguity in grammars (6), CNF & GNF normal
  forms (6), closure properties of CFLs (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium /
  5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="theory-of-computation"`,
  `data-unit="cfl-grammars"`, `data-unit-number="2"` and its subtopic slug.
- Set 1 of the second pass repeats nothing from the 50 banked Unit 2 items: ids `TOC-U2-Q51`..`TOC-U2-Q75` are new and
  every stem was compared with the banked stems. No item is a `GATE_PYQ_VARIATION` — no theory-of-computation
  previous-year question on this unit has been verified against an official paper and key, so nothing on this paper is
  claimed as an official GATE question. Every item is `STANDARD_TEXTBOOK` (18) or `ORIGINAL_SYNTHESIS` (7).
- **Every countable answer was recomputed by script, not by hand.** The number of derivation trees for
  `S → aSb | bSa | SS | ε` on `aabb` (1) and for `S → SS | a | b` on `aab` (2) came from a substring dynamic program
  over the grammar, not from inspection; the two node counts (7 for the tree of `aabb`, 6 for the tree of `aacbbb`)
  from tree arithmetic (2L − 1 for a full binary tree, and one internal node per production when every production
  emits exactly one terminal); the CYK table size from n(n+1)/2 = 21; the CNF production count (5) by writing the
  converted grammar out; and the closure count (7 of 9 operations) by enumerating the nine operations.
- The correct option is spread 3 A / 4 B / 5 C / 3 D across the 15 MCQ, checked by script.
- The new paper is filed only at `theory-of-computation/cfl-grammars/`; the superseded Set 2 paper was moved into that
  unit's `archive/` as `gate_toc_mock_2_2026-10-27_run2.html` unchanged, so the unit folder never held two current
  papers and no root copy was written.

- **2026-10-28, Computer Networks → Unit 3 (Network Layer: IP Addressing & Subnetting), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (draw index 10 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Computer Networks**. `runs[]` sorted by `(date, run)`
  gives the most recent paper as `{date 2026-10-28, run 5, unit 3, ipv4-subnetting, Set 1 of 2}`. Unit 3 held **25**
  questions, below `UNIT_QUESTION_CAP = 50`, and had been current for 0 days, below `DAYS_PER_UNIT_MAX = 7`, so step
  B3 held and step B4 was not reached: Unit 3 was generated again as **Set 2 of 2** and now holds exactly 50 questions,
  the cap. No override was used and no second pass has started for this subject. The next Computer Networks run
  advances `(index_of(ipv4-subnetting) = 2 + 1) mod 6 = 3` → Unit 4, Network Layer: Routing & Protocols.
- Coverage this run: all four Unit 3 subtopics — IPv4 header & fragmentation (7), classful vs classless & CIDR (6),
  subnet masking & supernetting (6), IPv6 basics & differences (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="computer-networks"`, `data-unit="ipv4-subnetting"`, `data-unit-number="3"` and its subtopic slug.
  Every numeric answer was re-derived in code: fragment counts and last-fragment offsets by simulation
  (`MTU &minus; 20` rounded down to a multiple of 8), usable-host counts and subnet addresses with `ipaddress`,
  and the prefix/subnet arithmetic for the /12, /16, /22 and /29 cases.
- Set 2 repeats nothing from Set 1: the two sets share no id, no stem and no numeric answer. Its four subtopics are
  all represented, and no item is a `GATE_PYQ_VARIATION` — no computer-networks previous-year question on this unit has
  been verified against an official paper and key, so nothing on this paper is claimed as an official GATE question.
- The correct option is spread 4 A / 4 B / 4 C / 3 D across the 15 MCQ, and each numeric option list stays in
  ascending order where the values allow it. Both were checked by script, not by eye.
- The new paper is filed only at `computer-networks/ipv4-subnetting/`; the superseded Set 1 paper was moved into that
  unit's `archive/` as `gate_cn_mock_3_2026-10-28_run1.html` unchanged, so the unit folder never held two current papers.

- **2026-10-28, Discrete Mathematics → Unit 7 (Counting & Combinatorics), Set 2 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 0 of 11 in
  the fixed list order discrete-mathematics, engineering-mathematics, digital-logic, computer-architecture,
  programming-data-structures, algorithms, theory-of-computation, compiler-design, operating-systems, databases,
  computer-networks), giving **Discrete Mathematics**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 6, unit 7, combinatorics, Set 1 of 2}`. Unit 7 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for 0 days, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and step B4
  was not reached: Unit 7 was generated again as **Set 2 of 2** and now holds exactly 50 questions, the cap. No override
  was used. The next Discrete Mathematics run advances `(index_of(combinatorics) = 6 + 1) mod 16 = 7` → Unit 8,
  Recurrence Relations & Generating Functions.
- Coverage this run: all five Unit 7 subtopics — permutations & combinations (5), stars and bars (5), binomial &
  multinomial coefficients (5), inclusion-exclusion counting (5), double counting (5). Composition 15 MCQ / 5 MSQ /
  5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="discrete-mathematics"`, `data-unit="combinatorics"`, `data-unit-number="7"` and its subtopic slug.
  Every numeric answer was re-derived independently in code (brute-force enumeration for the stars-and-bars, derangement,
  onto-function, adjacency and divisibility counts; closed forms for the multinomial and multiset counts).
- No verified previous-year question exists for Unit 7, so nothing on this paper is labelled an official GATE question;
  the two source tags used are standard textbook and original synthesis, plus one GATE-PYQ-variation pattern item that
  claims no year.
- The correct option is spread across A–D (2 A, 5 B, 6 C, 2 D) rather than always being option (A), which is a defect in
  several earlier papers of this series that has not yet been swept.

- **2026-10-28, Programming and Data Structures → Unit 4 (Binary Trees & Tree Traversals), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (draw index 4 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Programming and Data Structures**. All eleven subjects
  already had a paper dated 2026-10-28, so the draw ran over the full list. `runs[]` sorted by `(date, run)` gives the
  most recent paper as `{date 2026-10-28, run 7, unit 4, trees-traversals, Set 1 of 2}`. Unit 4 held **25** questions,
  below `UNIT_QUESTION_CAP = 50`, and had been current for 0 days, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and
  step B4 was not reached: Unit 4 was generated again as **Set 2 of 2** and now holds exactly 50 questions, the cap. No
  override was used and no second pass has started for this subject. The next Programming and Data Structures run
  advances `(index_of(trees-traversals) = 3 + 1) mod 7 = 4` → Unit 5, Binary Search Trees & Balanced Trees.
- Coverage this run: all four Unit 4 subtopics — binary tree properties (7), inorder/preorder/postorder traversals and
  reconstruction (6), threaded binary trees (6), expression trees (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="programming-data-structures"`, `data-unit="trees-traversals"`, `data-unit-number="4"`, its subtopic
  slug, its type, its lowercase difficulty and its source tag.
- All 25 items are new: `DS-U4-S2-Q01`..`DS-U4-S2-Q25` did not exist in the bank, and every stem was compared with the
  1986 normalised stems already held in the eleven subject banks and the eleven portal data files (tags stripped, case
  and punctuation removed): zero collisions and no id overlap. No question is an official GATE PYQ — `verified_pyqs`
  is empty for this subject — so nothing on this paper is claimed as official and no item is tagged
  `GATE_PYQ_VARIATION`. Every item is `STANDARD_TEXTBOOK` (17) or `ORIGINAL_SYNTHESIS` (8).
- **Every countable answer was recomputed by script, not by hand (15 independent checks, 0 disagreements).** The
  traversals were produced by building each tree in code and printing all three orders: inorder `A B C D E F` with
  postorder `B A D F E C` gives preorder `C A B E D F` (Q08); preorder `1 2 4 8 9 5 3 6 7` with inorder
  `8 4 9 2 5 1 6 3 7` gives postorder `8 9 4 5 2 6 7 3 1` (Q09); the tree rebuilt from preorder `A B C D E F G H` and
  inorder `C B D A F E H G` has 4 leaves (Q10); and preorder `A B C D E F G` with postorder `C B E G F D A` gives
  inorder `C B A E D G F` (Q13). Counting questions were settled by exhaustive enumeration or closed form: 32 chains of
  6 nodes at height 5 (Q07, brute force over all binary trees on 6 nodes), 8 trees with preorder `P Q R S` and
  postorder `S R Q P` (Q12, same enumeration), 10 leaves from `20 − 6 − 4` (Q01), 43 nodes for a strictly binary tree
  with 21 internal nodes (Q03), 41 one-child nodes from 100 nodes and 30 leaves (Q04), 489 nodes on the deepest level of
  a complete tree of 1000 (Q05), 31 NULL pointers in a 30-node tree (Q02), 5 right threads in the 9-node threaded
  example (Q19), 20 for the postfix evaluation (Q22), 11 nodes for the 5-operator expression tree (Q24) and height 4
  for `a b + c d e + * * f −` (Q25, built with a stack). **Every count, traversal and height reproduced.** One hand
  slip was caught by that pass: the first draft of Q19 counted four right threads by overlooking that node 14 has a
  left child only, and the script's count of five replaced it before the paper was built.
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B), (A,C), (A,B,C), (B,C) and (A,B,C).
- The previously current paper was moved to
  `programming-data-structures/trees-traversals/archive/gate_ds_mock_4_2026-10-28_run1.html` with its content frozen
  (same questions, options, answers, solutions and duration), and the new paper took the canonical filename
  `gate_ds_mock_4_2026-10-28.html`, so the unit folder holds exactly one current paper and no root copy was written.
  The portal card for the unit now launches the Set 2 paper and links Set 1 to the archived run1 file.
- The Question Bank tab inside the paper lists the **175** banked items that are not part of the active set — the 50
  questions of Unit 1, the 50 of Unit 2, the 50 of Unit 3 and the 25 of Unit 4 Set 1 — under one accordion per unit and
  one heading per subtopic, every solution collapsed. The 25 active questions do not appear there (verified: the string
  `DS-U4-S2-Q` occurs nowhere in the bank tab), and Units 5–7 are reported on one line rather than as empty accordions.
  The tab was regenerated from `master_bank.json` and reproduces the shipped tab byte-for-byte for the 150 Unit 1–3
  cards, which is how the generator was validated before it was trusted with the new unit.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions normalised to placeholders (title, header sub-line, set chip, bank tab label, `#qhost`,
  bank tab, About tab, payload), the remaining **28 299 bytes are byte-identical** to the shell extracted from the Set 1
  paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key view, the Question Bank tab, the About
  tab and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html`,
  `design-tokens.css` and the archived run1 file, and the paper carries the same literal hex values outside `:root` as
  its predecessor (the only extra `#` matches are the `&#8322;` subscript entities in two solutions), so the known
  Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**58 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no mark text, no `ansline` markup in the question
  pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every
  input enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear
  response, `cur` follows the current question, and Save & Next / Previous move the selection; all four tabs open and
  the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25 `ok` palette buttons, 25 key
  cards and a filled solution on every card; every MSQ one option short scores **25 / 35**, confirming that an MSQ
  earns nothing unless the exact set is selected; an all-wrong paper scores **0 / 35** and an empty paper **0 / 35**
  with 25 `skip` buttons, confirming there is no negative marking; every card carries all seven data attributes with
  lowercase difficulty values; the Question Bank tab renders 175 cards with no active question repeated; and the About
  tab carries its three sections.
- `index.html` holds all **1925** questions. Its data block was updated in place: the new Unit 4 record replaced the
  Set 1 record at the head of `tests` (with `archives` pointing at the frozen run1 file), and the 25 new records were
  appended to `data/questions-programming-data-structures.js`. The static header strings were recomputed from the data
  and now read 65 units, 47 sets published and 1925 solved questions / records, with 281 subtopics. A jsdom run of the
  portal renders **47 test cards** with the new paper first, **1925** archive question cards, and every relative link in
  the rendered page resolves against the repository tree (0 broken).
- Hygiene: the paper is filed at exactly one path, `programming-data-structures/trees-traversals/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (78 files, 41 current and 36 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; and the two pre-existing stem collisions inside Algorithms Unit 1.

- **2026-10-28, Operating Systems → Unit 4 (Memory Management & Paging), Set 2 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 8 of 11
  in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic, computer-architecture,
  programming-data-structures, algorithms, theory-of-computation, compiler-design, operating-systems, databases,
  computer-networks), giving **Operating Systems**. All eleven subjects already had a paper dated 2026-10-28, so the
  draw ran over the full list. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 7, unit 4, memory-paging, Set 1 of 2}`. Unit 4 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for 0 days, so step B3 held and step B4 was not reached: Unit 4 was
  generated again as **Set 2 of 2** and now holds exactly 50 questions, the cap. No override was used and no second
  pass has started. The next Operating Systems run advances
  `(index_of(memory-paging) = 3 + 1) mod 6 = 4` → Unit 5, Virtual Memory & Page Replacement.
- Coverage this run: all four Unit 4 subtopics — contiguous allocation under first, best and worst fit (6), paging and
  page-table structures (7), inverted page tables (6), segmentation and paged segmentation (6). Composition
  15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="operating-systems"`, `data-unit="memory-paging"`, `data-unit-number="4"`, its subtopic slug, its type,
  its lowercase difficulty and its source tag.
- All 25 items are new: `OS-U4-S2-Q01`..`OS-U4-S2-Q25` did not exist in the bank, and every stem was compared with the
  2049 normalised stems already held in the eleven subject banks and the eleven portal data files (tags stripped, case
  and punctuation removed): zero collisions and no id overlap. One stem was **reworded** during that check — the first
  draft of Q17 opened with the same generic sentence as a Set 1 MSQ, so it was rewritten as a scenario question before
  the paper was built. No question is an official GATE PYQ: `verified_pyqs` still holds only `PYQ-GATE2021S1-Q25`
  (Unit 1), so nothing on this paper is claimed as official and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (12) or `ORIGINAL_SYNTHESIS` (13).
- **Every countable answer was recomputed by script, not by hand (24 independent checks, 0 disagreements).** First fit
  over the holes 500/200/700/300 KB for the requests 450 and 260 KB leaves 50/200/440/300, so the largest hole is 440
  (Q02); worst fit over 400/250/550/300 KB for 200, 350, 150 KB leaves 50/250/200/300, largest 300 (Q03); first fit over
  200/600/150/400 KB for 500 and 250 KB leaves 200/100/150/150, largest 200 (Q05); best fit over 300/150/500/250 KB for
  140, 480, 200, 260 KB leaves 40/10/20/50, largest 50 (Q06); and best fit over 250/600/400/300 KB for a 380 KB request
  selects the 400 KB hole (Q01). Address arithmetic: 2⁴⁸/2¹³ = 2³⁵ entries (Q07), 40 − 12 = 28 page-number bits (Q08),
  2³¹/2¹² = 2¹⁹ = 524 288 entries (Q09), EAT `205 − 100h = 125` gives h = 0.80 (Q10), 2¹⁰ = 1024 second-level entries
  (Q11), 2¹⁰ × 4 B = 4 KB outer table (Q13), 2³²/2¹³ = 2¹⁹ inverted entries (Q14), (2²⁸/2¹²) × 16 B = 1 MB (Q18),
  8000 + 500 = 8500 (Q20), the limit test 1500 ≥ 1200 traps (Q21), the segment table traps only on (1, 20) (Q22),
  (2²⁰/2¹²) × 8 B = 2048 bytes (Q24) and segment table → page table → data = 3 accesses (Q25). **Every count, size,
  address and access reproduced.**
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,C), (B,C,D), (A,C), (A,B,C) and (A,B,D).
- The previously current paper was moved to
  `operating-systems/memory-paging/archive/gate_os_mock_4_2026-10-28_run1.html` with its content frozen (same
  questions, options, answers, solutions and duration), and the new paper took the canonical filename
  `gate_os_mock_4_2026-10-28.html`, so the unit folder holds exactly one current paper and no root copy was written.
  The portal card for the unit now launches the Set 2 paper and links Set 1 to the archived run1 file.
- The Question Bank tab inside the paper lists the **150** banked items that are not part of the active set — the 50
  questions of Unit 1, the 50 of Unit 2 and the 50 of Unit 3 — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active questions do not appear there (verified: the string `OS-U4-S2-Q`
  occurs nowhere in the bank tab), and Units 5–6 are reported on one line rather than as empty accordions. The tab
  block is byte-identical to the one shipped in Set 1, because the 150 questions it lists are exactly the same 150.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions normalised to placeholders (title, header sub-line, meta strip, `#qhost`, payload), the
  remaining **379 375 bytes are byte-identical** to the shell extracted from the Set 1 paper, so the `<style>` block,
  the exam `<script>`, the palette, the answer-key view, the Question Bank tab, the About tab and the footer are
  unchanged. The `:root` block is byte-identical across the new paper, `index.html`, `design-tokens.css` and the
  archived run1 file, and the paper carries exactly the same 89 literal hex values outside `:root` as its
  predecessor, so the known Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**47 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question pane, key tab
  disabled, key pane empty, summary hidden, timer at 60:00, one card visible, every input enabled); the palette reaches
  `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response, `cur` follows the current
  question, and Save & Next / Previous move the selection; all four tabs open and the key tab stays locked until
  submit; a fully correct paper scores **35 / 35** with 25 `ok` palette buttons, 25 key cards and a filled solution on
  every card; a paper with all five MSQs one option short scores **25 / 35** with 5 wrong, confirming that an MSQ earns
  nothing unless the exact set is selected; an all-wrong paper scores **0 / 35** and an empty paper **0 / 35** with 25
  `skip` buttons, confirming there is no negative marking; every card carries all seven data attributes with lowercase
  difficulty values; the Question Bank tab renders 150 cards with no active question repeated; and the About tab
  carries its three sections.
- `index.html` holds all **1900** questions. Its data block was updated in place: the new Unit 4 Set 2 record replaced
  the Set 1 record at the head of `tests` (with `archives` pointing at the frozen run1 file), and the 25 new records
  were appended to `data/questions-operating-systems.js`. The static header strings were recomputed from the data and
  now read 65 units, 47 sets published and 1900 solved questions / records, with 281 subtopics. A jsdom run of the
  portal renders **47 test cards** with the new paper first, **1900** archive question cards, and all **146** relative
  links in the rendered page resolve against the repository tree (0 broken).
- Hygiene: the paper is filed at exactly one path, `operating-systems/memory-paging/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (77 files, 41 current and 35 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; the two pre-existing stem collisions inside Algorithms Unit 1; and the unclosed
  `#view-about` in the shared shell.


- **2026-10-28, Compiler Design → Unit 4 (Syntax-Directed Translation & Intermediate Code), Set 1 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (draw index 7 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Compiler Design**. All eleven subjects already had a paper
  dated 2026-10-28, so the draw ran over the full list. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 7, unit 3, bottom-up-parsing, Set 2 of 2}`. Unit 3 held **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(bottom-up-parsing) = 2 + 1) mod 5 = 3` → **Unit 4, Syntax-Directed Translation & Intermediate Code**
  (`sdt-intermediate-code`), Set 1 of 2. Unit 4 had no folder and no paper, so nothing was archived and the unit folder
  holds exactly one current paper. No override was used, no unit exceeded 50 questions and no second pass has started.
  The next Compiler Design run re-selects Unit 4 (25 < 50) before advancing to `(3 + 1) mod 5 = 4`, Unit 5, Runtime
  Environments & Code Optimization.
- Coverage this run: all four Unit 4 subtopics — S-attributed against L-attributed definitions (7), three-address
  code with quadruples and triples (7), syntax trees and DAGs (6), type checking (5). Composition 15 MCQ / 5 MSQ /
  5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="compiler-design"`, `data-unit="sdt-intermediate-code"`, `data-unit-number="4"`, its subtopic slug,
  its type, its lowercase difficulty and its source tag.
- All 25 items are new: `CD-U4-Q01`..`CD-U4-Q25` did not exist in the bank, and every stem was compared with the 150
  banked Compiler Design questions with a string-normalised check (tags stripped, case and punctuation removed):
  zero collisions and no id overlap. No question is an official GATE PYQ — `verified_pyqs` is empty for this subject —
  so nothing is claimed as official and no item is tagged `GATE_PYQ_VARIATION`. Every item is `STANDARD_TEXTBOOK` (19)
  or `ORIGINAL_SYNTHESIS` (6).
- **Every countable answer was recomputed by script, not by hand (6 independent checks, 0 disagreements).** The
  annotated parse tree for `x + y * z` was built by a recursive-descent parser over the grammar
  `E → E + T | T`, `T → T * F | F`, `F → ( E ) | id` and its `val` instances counted by walking it: 2 `E` nodes,
  3 `T` nodes and 3 `F` nodes give 8 (Q07). The DAG for `a + a * (b - c) + (b - c) * d` was constructed with a
  hash-consing builder that merges nodes on identical operator and identical children: 5 interior nodes and 4 distinct
  leaves give 9 (Q17). The three-address counts were read off explicit instruction sequences — `a = b * -c + d` gives
  `t1 = -c`, `t2 = b * t1`, `t3 = t2 + d`, `a = t3`, so 4 instructions (Q11), and `a = b*c + d*e + f*g` with no reuse
  gives 5 temporaries in 6 instructions (Q14). The type expression `array(2, array(3, integer → integer))` contains
  3 constructors: two `array` nodes and one `→` (Q24). **Every count reproduced.**
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 3, (C) 4 and
  (D) 4, and the five MSQ answer sets are (A,B,D,E), (A,C,D,E), (A,B,C,D), (A,B,C,D) and (A,B,C,D).
- The conceptual items were settled against the standard rather than by taste: S-attributed ⊂ L-attributed is strict,
  with the identifier-list definition `D → T L { L.inh = T.type }` as the witness for the missing direction (Q02,
  Q04); an inherited attribute reading a right sibling is the one rule that breaks L-attributedness (Q05); a
  dependency cycle among inherited attributes admits no evaluation order at all, while an acyclic graph always admits
  a topological one (Q06); soundness is the one-sided guarantee that nothing accepted goes wrong, and no sound static
  checker can also be complete for a Turing-complete language (Q23, Q25); and `SSA` forbids a second definition of the
  same name, which is what separates it from ordinary three-address code (Q12).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab shows
  **125 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`.
- The Question Bank tab inside the paper lists the **125** banked items that are not part of the active set — the 50
  questions of Unit 1, the 50 of Unit 2 and the 25 of Unit 3 that remain after its own Set 2 — under one accordion per
  unit and one heading per subtopic, every solution collapsed. The 25 active questions do not appear there (verified:
  the string `CD-U4-Q` occurs nowhere in the bank tab), and Unit 5 is reported on one line rather than as an empty
  accordion. The tab block is the shipped one with its trailing empty-units line edited from `Units 4–5` to `Unit 5`;
  nothing else in it changed, because the 125 cards it lists are exactly the same 125 questions as last run.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With the
  nine payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining bytes are **byte-identical** to the shell extracted from the
  Compiler Design Unit 3 Set 2 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key view and
  the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html` and
  `design-tokens.css`, and the paper carries the same literal hex values outside `:root` as its predecessor, so the
  known Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in headless Chromium 153 from `file://` before shipping (**54 checks, all passing**): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question
  pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every
  input enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear
  response, `cur` follows the current question, and Save & Next / Previous move the selection; all four tabs open and
  the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25 `ok` palette buttons, 25 key
  cards and a filled solution on every card; one wrong MCQ, one MSQ one option short, one wrong NAT and one skipped MCQ
  score **29 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that an MSQ earns nothing unless the exact
  set is selected and that there is no negative marking; an MSQ with one extra option ticked scores **33 / 35**; an
  empty paper scores **0 / 35** with 25 `skip` buttons; every card carries all seven data attributes with lowercase
  difficulty values; the Question Bank tab renders 125 cards with no active question repeated; the About tab carries
  its three sections and states the practice marking scheme; and no page error or console error is raised.
- `index.html` holds all **1875** questions. Its data block was updated in place: the new Unit 4 record was inserted at
  the head of `tests` with `archives: []`, and the 25 new records were appended to `data/questions-compiler-design.js`.
  No unit had to be registered — Compiler Design Unit 4 (`sdt-intermediate-code`) was already in the portal's `units`
  table. The static header strings were recomputed from the data and now read 65 units, 47 sets published and 1875
  solved questions / records, with 281 subtopics.
- Hygiene: the paper is filed at exactly one path, `compiler-design/sdt-intermediate-code/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper; no temporary or loose file was left at the
  repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; the two pre-existing stem collisions inside Algorithms Unit 1; and the unclosed
  `#view-about` in the shared shell.

- **2026-10-28, Operating Systems → Unit 4 (Memory Management & Paging), Set 1 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 8 of 11
  in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic, computer-architecture,
  programming-data-structures, algorithms, theory-of-computation, compiler-design, operating-systems, databases,
  computer-networks), giving **Operating Systems**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 6, unit 3, deadlocks, Set 2 of 2}`. Unit 3 held **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(deadlocks) = 2 + 1) mod 6 = 3` → **Unit 4, Memory Management & Paging** (`memory-paging`), Set 1 of 2.
  Unit 4 had no folder and no paper, so nothing was archived and the unit folder holds exactly one current paper. No
  override was used, no unit exceeded 50 questions and no second pass has started. The next Operating Systems run
  re-selects Unit 4 (25 < 50) before advancing to `(3 + 1) mod 6 = 4`, Unit 5, Virtual Memory & Page Replacement.
- Coverage this run: all four Unit 4 subtopics — contiguous allocation under first, best and worst fit (7), paging and
  page-table structures (6), inverted page tables (6), segmentation and paged segmentation (6). Composition
  15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="operating-systems"`, `data-unit="memory-paging"`, `data-unit-number="4"`, its subtopic slug, its type,
  its lowercase difficulty and its source tag.
- All 25 items are new: `OS-U4-Q01`..`OS-U4-Q25` did not exist in the bank, and every stem was compared with the 150
  banked Operating Systems questions with a string-normalised check (tags stripped, case and punctuation removed) and
  with the 1769 stems already in the portal data files: zero collisions and no id overlap. No question is an official
  GATE PYQ for this unit:
  `verified_pyqs` still holds only `PYQ-GATE2021S1-Q25` (Unit 1), so nothing on this paper is claimed as official and
  no item is tagged `GATE_PYQ_VARIATION`. Every item is `STANDARD_TEXTBOOK` (12) or `ORIGINAL_SYNTHESIS` (13).
- **Every countable answer was recomputed by script, not by hand (11 independent checks, 0 disagreements).** First fit
  over the holes 100/500/200/300/600 KB was simulated for the request sequence 212, 417, 112, 426 KB: the free list
  after each placement is 100/288/200/300/600 → 100/288/200/300/183 → 100/176/200/300/183, so only the 426 KB request
  fails (Q04). Worst fit over 300/600/350/200/450 KB with requests 250, 400, 200 KB leaves holes 300/150/350/200/50, so
  the largest remaining hole is 350 KB (Q07). Effective access time 0.9 × 110 + 0.1 × 210 = 120 ns (Q10) and
  `301 − 200h = 141` gives h = 0.80 for the two-level walk (Q11). Table sizes: 2³⁰/2¹² frames × 8 B = 2 MB (Q17),
  2¹⁴ frames × 8 B = 128 KB (Q19), 2¹² pages × 4 B = 16 KB (Q24). Field widths and address arithmetic: 32 − 13 = 19
  page-number bits (Q13) and 3000 + 400 = 3400 (Q25). **Every count, size and address reproduced.**
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,D), (A,B,C), (A,B,D), (A,B,C) and (B,C,D).
- The Question Bank tab inside the paper lists the **150** banked items that are not part of the active set — the 50
  questions of Unit 1, the 50 of Unit 2 and the 50 of Unit 3 — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active questions do not appear there (verified: the string `OS-U4-Q`
  occurs nowhere in the bank tab).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the nine payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining **27 969 bytes are byte-identical** to the shell extracted from
  the Operating Systems Unit 3 Set 2 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key
  view and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html` and
  `design-tokens.css`.
- The paper was exercised in a jsdom harness before shipping (**33 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no mark text, key tab disabled, key pane empty,
  summary hidden, timer at 60:00, one card visible, every input enabled); the palette reaches `na`, `ans`, `amr` and
  `mrk` through visiting, answering, marking and Clear response, and the `cur` outline follows the current question;
  all four tabs open and the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25 `ok`
  palette buttons, 25 key cards and a filled solution on every card; a paper with one MSQ one option short, one wrong
  MCQ, one wrong NAT and one skipped MCQ scores **29 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that
  an MSQ earns nothing unless the exact set is selected and that there is no negative marking; every card carries
  `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`
  with lowercase difficulty values; the Question Bank tab renders 150 cards with no active question repeated; and the
  About tab carries its three sections.
- `index.html` holds all **1850** questions. Its data block was updated in place: the new Unit 4 record was inserted at
  the head of `tests` with `archives: []`, and the 25 new records were appended to `data/questions-operating-systems.js`.
  No unit had to be registered — Operating Systems Units 1–6 were already in the portal's `units` table. The static
  header strings were recomputed from the data and now read 46 sets published and 1850 solved questions / records. A
  jsdom run of the portal renders **46 test cards** with the new paper first, and all **143** relative links in the
  rendered page resolve against the repository tree (0 broken).
- Hygiene: the paper is filed at exactly one path, `operating-systems/memory-paging/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (75 files, 40 current and 34 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; the two pre-existing stem collisions inside Algorithms Unit 1; and the unclosed
  `#view-about` in the shared shell.

- **2026-10-28, Computer Networks → Unit 3 (Network Layer: IP Addressing & Subnetting), Set 1 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (draw index 10 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Computer Networks**. All eleven subjects already had a
  paper dated 2026-10-28, so the draw ran over the full list. `runs[]` sorted by `(date, run)` gives the most recent
  paper as `{date 2026-10-28, run 4, unit 2, data-link-mac, Set 2 of 2}`. Unit 2 held **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(data-link-mac) = 1 + 1) mod 6 = 2` → **Unit 3, Network Layer: IP Addressing & Subnetting**
  (`ipv4-subnetting`). Unit 3 had no folder and no paper, so nothing was archived and the unit folder holds exactly
  one current paper. No override was used, no unit exceeded 50 questions and no second pass has started. The next
  Computer Networks run re-selects Unit 3 (25 < 50) before advancing to `(2 + 1) mod 6 = 3`, Unit 4, Routing &
  Protocols.
- **A data-entry slip in this subject's bank was corrected before the rotation was computed.** 25 Unit 2 records
  (`CN-DL2-Q01`..`CN-DL2-Q25`, the Set 2 items) stored `unit` and `unit_number` as the strings `"2"` rather than the
  integers `2`, so a count of `q["unit"] == 2` returned 25 instead of 50 and step B3 would have held Unit 2 for a third
  set. Both fields are now integers; Unit 2 reads 50 and the cap applies. The same class of slip was still present in
  `operating-systems/question-bank/master_bank.json` (25 Unit 3 records, `OS-U3B-Q01`..`OS-U3B-Q25`), which an earlier
  entry had reported as already fixed; those 50 fields were corrected in the same pass, so Operating Systems Unit 3
  now reads 50 in the bank as it already did in the portal. No question content, id or answer changed in either file.
- Coverage this run: all four Unit 3 subtopics — IPv4 header and fragmentation (7), classful against classless and
  CIDR (6), subnet masking and supernetting (7), IPv6 basics and differences (5). Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="computer-networks"`, `data-unit="ipv4-subnetting"`, `data-unit-number="3"`, its subtopic slug, its
  type, its lowercase difficulty and its source tag.
- All 25 items are new: `CN-U3-Q01`..`CN-U3-Q25` did not exist in the bank, and every stem was compared with the 125
  question records in the portal data with a string-normalised check (tags stripped, case and punctuation removed):
  zero collisions and no id overlap. No question is an official GATE PYQ — `verified_pyqs` is empty for this subject —
  so nothing is claimed as official and no item is tagged `GATE_PYQ_VARIATION`. Every item is `STANDARD_TEXTBOOK` (12)
  or `ORIGINAL_SYNTHESIS` (13).
- **Every countable answer was recomputed by script, not by hand (23 independent checks, 0 disagreements).** The
  fragmentation figures were produced by an explicit fragmenting routine rather than by quoting a formula: 3000 bytes
  at MTU 1500 gives 3 fragments (Q03); 4000 bytes gives offsets 0, 185, 370, so the last offset is 370 (Q04) and the
  Total Length fields are 1500, 1500, 1060 (Q05); the two-hop case cuts 5000 bytes into 1480/1480/1480/560 and then
  each piece again at MTU 576 into 552-byte payloads, giving 9 + 2 = 11 fragments (Q07). All prefix arithmetic ran
  through `ipaddress`: /27 gives 30 usable hosts (Q09); 192.168.10.130/26 lies in 192.168.10.128/26 (Q10); the four
  candidate hosts in 10.20.30.0/23 were tested for membership and for the network/broadcast exclusion, confirming that
  10.20.30.255 and 10.20.31.0 are ordinary hosts while 10.20.31.255 is the broadcast (Q11); /18 holds 64 /24s (Q12);
  longest-prefix match over the four-route table selects the /24 (Q13); 192.168.1.64/26 broadcasts at .127 (Q14); /28
  is 255.255.255.240 (Q15); /16 to /26 is 1024 subnets (Q16); the only prefix whose /24 list equals 192.168.0.0/24
  through 192.168.7.0/24 is /21, found by enumerating candidates rather than by asserting it (Q17); /20 subnets of
  172.16.0.0/16 number 16 with 4094 usable hosts, and 172.16.32.0 is a boundary while 172.16.40.0 is not (Q18);
  10.1.2.3/22 and 10.1.6.5/22 mask to 10.1.0.0 and 10.1.4.0 (Q19); VLSM leaves 256 − 60 = 196 addresses (Q20); and a
  /48 delegates 2¹⁶ = 65536 /64s (Q25). **Every fragment count, offset, prefix and address reproduced.**
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,C), (B,D), (A,B,D), (A,D) and (B,C,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab shows
  **100 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the 50
  questions of Unit 1 and the 50 of Unit 2 — under one accordion per unit and one heading per subtopic, every solution
  collapsed. The 25 active questions do not appear there (verified: the string `CN-U3-Q` occurs nowhere in the bank
  tab), and Units 3–6 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the nine payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining **27 851 bytes are byte-identical** to the shell extracted
  from the Computer Networks Unit 2 Set 2 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html`
  and `design-tokens.css`.
- The paper was exercised in a jsdom harness before shipping (**35 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty, no option mark, no `ansline` markup in the question pane, key tab disabled
  and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input enabled); the
  palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response, and the `cur`
  outline follows the current question; all four tabs open and the key tab stays locked until submit; a fully correct
  paper scores **35 / 35** with 25 `ok` palette buttons, 25 key cards and a filled solution on every card; one wrong
  MCQ, one MSQ one option short, one wrong NAT and one skipped MCQ score **29 / 35** with 21 correct, 3 wrong and 1
  unattempted, confirming that an MSQ earns nothing unless the exact set is selected and that there is no negative
  marking; an empty paper scores **0 / 35** with 25 `skip` buttons; every card carries `data-subject`, `data-unit`,
  `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source` with lowercase difficulty
  values; the Question Bank tab renders 100 cards with no active question repeated.
- `index.html` holds all **1825** questions. Its data block was updated in place: the new Unit 3 record was inserted at
  the head of `tests` with `archives: []`, and the 25 new records were appended to `data/questions-computer-networks.js`.
  No unit had to be registered — Computer Networks Units 1–6 were already in the portal's `units` table. The static
  header strings were recomputed from the data and now read 65 units, 45 sets published and 1825 solved questions /
  records, with 281 subtopics. Every path in the data block resolves against the repository tree (85 links, 0 broken),
  and a jsdom run of the portal renders 45 test cards and 1825 archive question cards with the new paper first.
- Hygiene: the paper is filed at exactly one path, `computer-networks/ipv4-subnetting/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (74 files, 39 current and 34 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell (measured 135 occurrences in the new paper, 85 in the portal); the two legacy
  `proof-techniques` archive files that still carry an older `:root`; the two current papers in
  `digital-logic/number-systems`; the two portal cards that launch an archived run while a current paper exists; and
  the two pre-existing stem collisions inside Algorithms Unit 1. One further shell defect was found this run and is
  added to the list below: `#view-about` is never closed in the shared shell, so `<footer class="foot">` and both
  `<script>` elements sit inside the hidden About view and the provenance footer is therefore never visible.


- **2026-10-28, Theory of Computation → Unit 1 (Regular Languages & Finite Automata), Set 1 of 2 (second pass).**
  MODE A: one subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded
  `random.SystemRandom()` draw (draw index 6 of 11 in the fixed list order discrete-mathematics,
  engineering-mathematics, digital-logic, computer-architecture, programming-data-structures, algorithms,
  theory-of-computation, compiler-design, operating-systems, databases, computer-networks), giving **Theory of
  Computation**. All eleven subjects already had a paper dated 2026-10-28, so the draw ran over the full list.
  `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 8, unit 4, turing-machines-decidability, Set 2 of 2}`. Unit 4 held **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(turing-machines-decidability) = 3 + 1) mod 4 = 0` → **Unit 1, Regular Languages & Finite Automata**
  (`regular-languages-fa`). Every Theory of Computation unit is at the cap, so the modulo wrapped and a **second pass
  has started** (step B5). No override was used.
- Coverage this run: all four Unit 1 subtopics — DFA construction & minimisation (11), regular expressions (6), NFA to
  DFA and the subset construction (4), pumping lemma for regular languages (4). Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="theory-of-computation"`, `data-unit="regular-languages-fa"`, `data-unit-number="1"`, its subtopic
  slug, its type, its lowercase difficulty and its source tag.
- All 25 items are new: `TOC-U1-Q51`..`TOC-U1-Q75` did not exist in the bank, and every stem was compared with the 50
  banked Unit 1 items with a string-normalised check (tags stripped, case folded) — zero collisions. The active set is
  not repeated in the paper's Question Bank tab, which shows the other **200** banked Theory of Computation questions.
- Answer verification: every numeric answer was recomputed by script. Three minimal-state items were **corrected**
  during verification — Q61 (even 0s and ends in 1) and Q68 (even length and ends in b) are 3 states, not the 4 the
  product construction suggests, because the two "odd" states are equivalent; Q71 (divisible by 6) is 4 states, not 6,
  because 2 is not invertible modulo 6 and residues 1 ≡ 4, 2 ≡ 5. A Myhill–Nerode signature check over all words up to
  length 7 confirmed each count, and Q75 (mod 7) confirmed 7 states, where 2 *is* invertible.
- The previously current paper `gate_toc_mock_1_2026-10-26.html` was moved to
  `archive/gate_toc_mock_1_2026-10-26_run2.html` with its content frozen, and the new paper took the canonical
  filename, so the unit folder holds exactly one current paper and no root copy was written. The portal card for that
  date now launches the archived run2 file and links Set 1 to `archive/…_run1.html`.
- Shell: the paper was built by injecting only the payload, the 25 question cards, the palette (unchanged), the
  Question Bank tab and the About tab into the Theory of Computation Unit 4 Set 2 shell. With those content regions
  normalised away, the remaining bytes are identical to that paper's (verified by script), so shell parity holds.
- Bank: `master_bank.json` grew to **225** questions and **9** runs; the portal now carries **44** test cards and
  **1800** question records, both matching the banks exactly. No verified PYQ was added — Theory of Computation still
  has none, so nothing in this paper is claimed as official.

- **2026-10-28, Programming and Data Structures → Unit 4 (Binary Trees & Tree Traversals), Set 1 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (draw index 4 of 11 in the fixed list order discrete-mathematics, engineering-mathematics, digital-logic,
  computer-architecture, programming-data-structures, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases, computer-networks), giving **Programming and Data Structures**. All eleven subjects
  already had a paper dated 2026-10-28, so the draw ran over the full list. `runs[]` sorted by `(date, run)` gives the
  most recent paper as `{date 2026-10-28, run 6, unit 3, linear-data-structures, Set 2 of 2}`. Unit 3 held **50**
  questions, exactly `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(linear-data-structures) = 2 + 1) mod 7 = 3` → **Unit 4, Binary Trees & Tree Traversals**
  (`trees-traversals`). Unit 4 had no folder and no paper, so nothing was archived and the unit folder holds exactly
  one current paper. No override was used, no unit exceeded 50 questions and no second pass has started. The next
  Programming and Data Structures run re-selects Unit 4 (25 < 50) before advancing to
  `(3 + 1) mod 7 = 4`, Binary Search Trees & Balanced Trees.
- Coverage this run: all four Unit 4 subtopics — binary tree properties (7), inorder/preorder/postorder and
  reconstruction (6), threaded binary trees (6), expression trees (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="programming-data-structures"`, `data-unit="trees-traversals"`, `data-unit-number="4"`, its subtopic
  slug, its type, its lowercase difficulty and its source tag.
- All 25 items are new: `DS-U4-Q01`..`DS-U4-Q25` did not exist in the bank, and every stem was compared with the 1750
  question records already in the portal data block with a string-normalised check (tags stripped, case and
  punctuation removed): zero collisions and no id overlap. No question is an official GATE PYQ — `verified_pyqs` is
  empty for this subject — so nothing is claimed as official and no item is tagged `GATE_PYQ_VARIATION`.
- **Every countable answer was recomputed by script, not by hand (83 checks, 0 disagreements).** Tree shapes were
  enumerated exhaustively up to 7 nodes and every labelled tree up to 4 nodes: `n0 = n2 + 1`, `n = n0 + n1 + n2` and
  the height bound `h ≥ ⌈log2(n+1)⌉ − 1` were tested on every shape rather than asserted (Q05); the NULL-field count
  `n + 2` for a record with a parent link was tested on every shape (Q07); the 42 shapes of 5 nodes were counted by
  enumeration, not by quoting a Catalan table (Q06); `A B D E C F` + `D B E A C F` was rebuilt and re-traversed to
  confirm `D E B F C A` (Q08); the level-order + inorder pair was rebuilt to `A B D E C F G` and the level order
  re-read from the rebuilt tree (Q09); the four trees with preorder `A B C` and postorder `C B A` were found by
  enumerating every labelled tree, and preorder+postorder was confirmed non-unique while preorder+inorder,
  postorder+inorder and level-order+inorder were confirmed unique (Q10, Q12); the 9-node reconstruction gives exactly
  two single-child nodes, `B` and `F` (Q13); 21 threads for 20 nodes follows from the `n + 1` NULL-pointer identity
  tested above (Q15); the stated 8-node tree has 5 nodes without a right child and 4 without a left child, which is
  the trap in Q19; `a b c * + d −` was produced by a shunting-yard implementation (Q20); `5 3 + 8 2 − * 4 /` evaluates
  to 12 and its operand-swapped variant to −12 (Q22); the left subtree of the `a + b*c − d` tree holds 5 of the 7
  nodes (Q24); and all three notations of a 9-operator tree carry 19 tokens (Q25). **Every traversal round-trip,
  every enumeration and every arithmetic answer reproduced.**
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,C), (A,B,D), (A,C,D), (B,C,D) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **150 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (12) or `ORIGINAL_SYNTHESIS` (13), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **150** banked items that are not part of the active set — the 50
  questions of Unit 1, the 50 of Unit 2 and the 50 of Unit 3 — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active questions do not appear there (verified: the string `DS-U4-Q`
  occurs nowhere in the bank tab), and Units 5–7 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the ten payload regions replaced by placeholders (title, brand line, header sub-line, candidate ID, bank tab label,
  meta strip, `#qhost`, bank tab, About tab, payload), the remaining **27 320 bytes are byte-identical** to the shell
  extracted from the Programming and Data Structures Unit 3 Set 2 paper, so the `<style>` block, the exam `<script>`,
  the palette, the answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new
  paper, `index.html` and `design-tokens.css`, and the paper carries exactly the same 111 literal hex values outside
  `:root` as its predecessor, so the known Section 6.4 deviation below is untouched and was not partially fixed for
  one paper. The Question Bank tab generator was validated against the shipped paper: rebuilding the 125-card tab of
  the Unit 3 Set 2 paper from `master_bank.json` reproduces it **byte for byte** (259 441 bytes).
- The paper was exercised in a jsdom harness before shipping (**49 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response,
  and the `cur` outline follows the current question; all four tabs open and the key tab stays locked until submit; a
  fully correct paper scores **35 / 35** with 25 `ok` palette buttons, 25 key cards and a filled solution on every
  card; one wrong MCQ, one MSQ one option short, one wrong NAT and one skipped MCQ score **29 / 35** with 21 correct,
  3 wrong and 1 unattempted, confirming that an MSQ earns nothing unless the exact set is selected and that there is
  no negative marking; an MSQ with one extra option ticked takes the paper to **25 / 35** with 5 wrong; an empty paper
  scores **0 / 35** with 25 `skip` buttons; every card carries `data-subject`, `data-unit`, `data-unit-number`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty values; the Question
  Bank tab renders 150 cards with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1775** questions. Its data block was updated in place: the new Unit 4 record was inserted
  at the head of `tests` with `archives: []`, and the 25 new question records were appended; every existing byte of
  the data block was preserved by splicing rather than re-serialising. No unit had to be registered — Programming and
  Data Structures Units 1–7 were already in the portal's `units` table. The static header strings were recomputed
  from the data block and now read 65 units, 43 sets published and 1775 solved questions / records, with 281
  subtopics. Every path in the data block resolves against the repository tree (71 links, 0 broken).
- Hygiene: the paper is filed at exactly one path, `programming-data-structures/trees-traversals/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (72 files, 38 current and 33 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; and the two pre-existing stem collisions inside Algorithms Unit 1.

- **2026-10-28, Programming and Data Structures → Unit 3 (Linear Data Structures), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index
  4 of 11), giving **Programming and Data Structures**. All eleven subjects already had a paper dated 2026-10-28, so the
  draw ran over the full list rather than over the subjects still missing from today. `runs[]` sorted by
  `(date, run)` gives the most recent paper as `{date 2026-10-28, run 5, unit 3, linear-data-structures, Set 1 of 2}`.
  Unit 3 held **25** questions, below `UNIT_QUESTION_CAP = 50`, and had been current for 0 days, below
  `DAYS_PER_UNIT_MAX = 7`, so step B3 held and step B4 was not reached: the current unit was generated again as
  **Set 2 of 2**, which closes Unit 3 at exactly 50 questions. The next Programming and Data Structures run advances
  `(index_of(linear-data-structures) = 2 + 1) mod 7 = 3` → **Unit 4, Binary Trees & Tree Traversals**. No override was
  used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — arrays and multidimensional arrays (6), singly/doubly/circular linked
  lists (6), stacks: infix, postfix and applications (7), queues, circular queues and deques (6). Composition
  15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="programming-data-structures"`, `data-unit="linear-data-structures"`, `data-unit-number="3"` and its
  subtopic slug.
- All 25 items are new: `DS-U3-Q26`..`DS-U3-Q50` did not exist in the bank, and every stem was compared with the 25
  banked Unit 3 Set 1 items. No question is an official GATE PYQ — `verified_pyqs` is empty for this subject — so
  nothing is claimed as official and no item is tagged `GATE_PYQ_VARIATION`.
- **Every numeric answer was recomputed by script.** Address arithmetic for the four layout questions (168, 556, and
  the element count 160); the two-pointer trace of the count loop gives 5 for `n = 10`; the shared-array gap gives 1
  free slot; the postfix-depth trace peaks at 5; the deque trace leaves `6, 3`; the circular-queue rear is
  `(3 + 5) mod 8 = 0`; the symmetric-matrix packing gives 55 and 5050; the circular-list predecessor is 11 steps away;
  the infix-to-postfix conversion performs exactly 5 operator pops; the stack-permutation count is `C(4) = 14`,
  confirmed by exhaustive enumeration; and the two-stack queue leaves 1 element. **7 of 7 numeric answers and 1 of 1
  enumeration reproduced; 0 disagreements.**
- Shell note: the Set 1 paper for this unit had lost the opening `<aside class="side">` and two closing `</div>` tags,
  so its Answer Key, Question Bank and About views were nested inside `#view-test` and the tab switch hid them. This
  paper takes the palette block from the balanced shell and its four views are siblings inside `.wrap`, verified with
  a DOM parse and a jsdom tab test. The archived Set 1 file keeps its 25 questions, options, answers, solutions and
  duration unchanged; only those two shell tags were repaired, so its tabs work as well.

- **2026-10-28, Databases → Unit 3 (Database Normalization), Set 1 of 2.** MODE A: one subject was drawn uniformly at
  random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 9 of 11), giving
  **Databases**. All eleven subjects already had a paper dated 2026-10-28, so the draw ran over the full list rather
  than over the subjects still missing from today. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-28, run 3, unit 2, sql-querying, Set 2 of 2}`. Unit 2 held **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so step B3 failed on the cap and step B4 advanced exactly one unit:
  `(index_of(sql-querying) = 1 + 1) mod 5 = 2` → **Unit 3, Database Normalization** (`normalization`), Set 1 of 2.
  Unit 3 had no folder and no paper, so nothing was archived and the unit folder holds exactly one current paper.
  No override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all five Unit 3 subtopics, five questions each — functional dependencies and Armstrong's axioms,
  closure of attribute sets and keys, 1NF/2NF/3NF/BCNF, lossless join and dependency preservation, multivalued
  dependencies and 4NF. Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks
  15 × 1 + 10 × 2 = 35. Every question carries `data-subject="databases"`, `data-unit="normalization"`,
  `data-unit-number="3"` and its subtopic slug.
- All 25 items are new: `DB-U3-Q01`..`DB-U3-Q25` did not exist in the bank, and every stem was compared against the
  100 banked Databases items with a string-normalised check (tags stripped, case and punctuation removed): zero
  collisions and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** Attribute closures, candidate keys and superkey
  counts were enumerated exhaustively over all attribute subsets: `AB`, `BC` and `BD` are the three candidate keys of
  `{AB → C, C → D, D → A}` (Q08); `AB`, `BC`, `BD` and `BE` are the four of `{AB → C, C → D, D → E, E → A}` (Q18);
  `A⁺` covers 4 attributes (Q13) and the superkey count is `2³ = 8` (Q23) for the chain `A → B → C → D`; the minimal
  cover of `{A → B, B → C, A → C}` keeps 2 dependencies (Q14). Losslessness was decided by a chase-test
  implementation rather than by inspection: of the four decompositions offered in Q17 only `(A, C)|(B, D)` is lossy,
  and in Q22 the split `(A, B)|(A, C, D)` is lossless but loses `BC → D`, which is the answer keyed. **5 of 5
  numeric answers and 2 of 2 chase verdicts reproduced; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: triviality for FDs is `Y ⊆ X`, while
  MVDs need the second clause `X ∪ Y = R` as well, which is why `A →→ BC` is trivial and `A →→ B` is not (Q24);
  pseudotransitivity is sound but is not one of Armstrong's three axioms (Q10); 2NF needs *both* a proper subset of a
  key and a non-prime right-hand side (Q07); `R(A, B, C, D)` with `{AB → C, C → D}` is in 2NF and not 3NF (Q11); a
  relation with `A →→ B` and `A →→ C` and no FD is in BCNF yet not in 4NF, and its lossless 4NF split is
  `(A, B)|(A, C)` (Q15, Q20); and `{AB → C, C → B}` is the standard witness that a BCNF decomposition need not
  preserve dependencies (Q21).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,C,D), (A,B,D), (B,C,D), (A,B,C) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 1 for the subject (the 2014 Set 3 Q30
  variation banked under Unit 1), the Question Bank tab shows **100 solved** and **1 verified GATE PYQ**, and no item
  in this set is tagged `GATE_PYQ_VARIATION`. Every item is `STANDARD_TEXTBOOK` (10) or `ORIGINAL_SYNTHESIS` (15), so
  nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the 50
  questions of Unit 1 and the 50 of Unit 2 — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active questions do not appear there (verified: the string `DB-U3-Q` occurs nowhere in
  the bank tab), and Units 4–5 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining **27 854 bytes are byte-identical** to the shell extracted
  from the Databases Unit 2 Set 2 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key view
  and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html` and
  `design-tokens.css`, and the paper carries exactly the same 89 literal hex values outside `:root` as its
  predecessor, so the known Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**47 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response;
  all four tabs open and the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25 `ok`
  palette buttons, 25 key cards and a filled solution on every card; one wrong MCQ, one MSQ one option short and one
  skipped NAT score **30 / 35** with 22 correct, 2 wrong and 1 unattempted, confirming that an MSQ earns nothing
  unless the exact set is selected and that there is no negative marking; an empty paper scores **0 / 35** with 25
  `skip` buttons; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`, with lowercase difficulty values; the Question Bank tab renders 100 cards with
  no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1725** questions. Its data block was updated in place: the new Databases Unit 3 record was
  inserted at the head of `tests` with `archives: []`, and the 25 new question records were appended. No unit had to
  be registered — Databases Units 1–5 were already in the portal's `units` table. The static header strings were
  recomputed from the data block and now read 65 units, 42 sets published and 1725 solved questions / records, with
  281 subtopics; the earlier 1675-vs-1700 mismatch between the two "solved questions" chips is gone, both now count
  the full `questions` array. Every path in the data block resolves against the repository tree (136 links, 0 broken).
- Hygiene: the paper is filed at exactly one path, `databases/normalization/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (70 files, 37 current and 32 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; and the two pre-existing stem collisions inside Algorithms Unit 1.

- **2026-10-28, Engineering Mathematics → Unit 4 (Calculus: Maxima, Minima & Integrals), Set 1 of 2.** MODE A: at the
  time of the draw only Engineering Mathematics had no paper dated 2026-10-28, so the uniform draw over that
  one-element list gave **Engineering Mathematics**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-27, run 6, unit 3, calculus-limits-derivatives, Set 2 of 2}`. Unit 3 held **50** questions, so it was
  not under `UNIT_QUESTION_CAP = 50` and step B3 failed; step B4 advanced
  `(index_of(calculus-limits-derivatives) + 1) mod 5 = (2 + 1) mod 5 = 3` → **Unit 4, Set 1 of 2**. Units 1–3 are all
  at the cap, so the subject has begun a second sweep. No archive move was needed: Unit 4 had no earlier paper, and
  the Unit 3 folder keeps its own current paper. No override was used and no unit exceeded 50 questions.

- **2026-10-28, Operating Systems → Unit 3 (Deadlocks), Set 2 of 2.** MODE A: one subject was drawn uniformly at
  random with an unseeded `random.SystemRandom()` draw over the 2 subjects that had no paper dated 2026-10-28 (draw
  index 1 of 2), giving **Operating Systems**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-27, run 5, unit 3, deadlocks, Set 1 of 2}`. Unit 3 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and
  step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 3 now holds exactly 50
  questions — the cap — and the next Operating Systems run advances
  `(index_of(deadlocks) + 1) mod 6 = (2 + 1) mod 6 = 3` → **Unit 4, Memory Management & Paging**. The Set 1 paper
  was moved to `operating-systems/deadlocks/archive/gate_os_mock_3_2026-10-27_run1.html` with its content frozen, and
  the Set 2 paper took the canonical filename. No override was used, no unit exceeded 50 questions and no second
  pass has started.
- Coverage this run: all four Unit 3 subtopics — four conditions and the resource-allocation graph (7), prevention,
  avoidance and the banker's algorithm (6), detection and recovery (6), starvation versus deadlock (6). Composition
  15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question
  carries `data-subject="operating-systems"`, `data-unit="deadlocks"`, `data-unit-number="3"` and its subtopic slug.
- No question in this set is claimed as an official GATE previous-year question. No deadlock PYQ has been verified
  against an official paper and answer key, so none is marked `GATE_PYQ_VARIATION` as an official item; that tag here
  means the question follows a previously asked pattern with new resources and numbers.
- **2026-10-28, Algorithms → Unit 2 (Divide and Conquer & Sorting), Set 2 of 2.** MODE A: one subject was drawn
  uniformly at random with an unseeded `random.SystemRandom()` draw over the 3 subjects that had no paper dated
  2026-10-28 (draw index 0 of 3), giving **Algorithms**. `runs[]` sorted by `(date, run)` gives the most recent paper
  as `{date 2026-10-27, run 3, unit 2, sorting-divide-conquer, Set 1 of 2}`. Unit 2 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and
  step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 2 now holds exactly 50
  questions — the cap — and the next Algorithms run advances
  `(index_of(sorting-divide-conquer) + 1) mod 7 = (1 + 1) mod 7 = 2` → **Unit 3, Greedy Algorithms**. The Set 1 paper
  was moved to `algorithms/sorting-divide-conquer/archive/gate_algo_mock_2_2026-10-27_run1.html` with its content
  frozen, and the Set 2 paper took the canonical filename. No override was used, no unit exceeded 50 questions and no
  second pass has started.
- Coverage this run: all four Unit 2 subtopics — merge sort and quicksort (7), counting and radix sort (6), selection
  and the k-th element (6), inversion counting (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10
  medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="algorithms"`,
  `data-unit="sorting-divide-conquer"`, `data-unit-number="2"` and its subtopic slug.
- All 25 items are new: `ALG-U2-Q26`..`ALG-U2-Q50` did not exist in the bank, and every stem was compared against all
  1625 questions already in the portal data block with a string-normalised check (tags stripped, case and punctuation
  removed): zero stem collisions and no id overlap for this run's items.
- **Every countable answer was recomputed by script, not by hand.** The merge of runs of 5 and 8 has a maximum of
  `5 + 8 − 1 = 12` comparisons (Q30); the full Lomuto quicksort of `[7,3,9,4,2,8,5]` performs **9** exchanges, two of
  them self-exchanges in the last partition (Q32); base 16 over 32 bits needs `32/4 = 8` passes (Q38);
  median-of-medians on 60 keys guarantees `3·60/10 − 6 = 12` keys on each side (Q43); and `[5,2,4,1,3,2,6,1]` holds
  **16** inversions, counted position by position with strict inequality (Q49). The inversion count, the exchange
  count and the partition trace were each produced by a script that simulates the algorithm, not by hand.
  **5 of 5 computed answers reproduced; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: merging linked lists rewires pointers,
  so the Θ(n) buffer of the array merge disappears and only the Θ(log n) stack remains (Q26); one partition fixes the
  pivot's final index (Q27); a two-way partition is Θ(n²) on equal keys while a three-way partition is Θ(n) (Q28);
  randomisation gives an expected bound, smaller-side-first recursion gives a worst-case stack bound (Q29); a
  1 : 9 split is still Θ(n log n) because 1/10 + 9/10 = 1 and the level cost is Θ(n) (Q31); counting sort uses no
  comparison at all (Q33); the k term, not n, dominates when the key range is 10⁶ wide (Q34); radix base n sorts
  n keys below n² in two passes (Q35); the optimal radix base is b ≈ n (Q36); LSD radix sort is stable overall and
  its pass count is data-independent (Q37); quickselect discards the side that cannot contain the rank (Q39); the
  maximum needs n − 1 comparisons because every other key must lose once (Q40); the median is Ω(n) and Θ(n), not
  Ω(n log n) (Q41); blocks of 3 destroy the median-of-medians guarantee because 1/3 + 2/3 = 1 (Q42); 9/10 < 1 is
  why the recurrence is linear (Q44); a permutation plus its reverse always sums to n(n−1)/2 inversions (Q45); an
  adjacent exchange changes the count by exactly ±1 (Q46); inversions measure adjacent-swap distance while n − cycles
  measures arbitrary-swap distance (Q47); the merge counter counts each pair at exactly one level (Q48); and the
  Lehmer code has position-dependent bounds 0 ≤ dᵢ ≤ n − i (Q50).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,C), (A,B,D), (A,C,D), (B,C,D) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **75 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **75** banked items that are not part of the active set — the 50
  questions of Unit 1 and the 25 of Unit 2 Set 1 — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Set 2 questions do not appear there (verified: no `ALG-U2-Q26`..`Q50` id occurs
  in the bank tab). Units 3–7 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions replaced by placeholders (title, header sub-line, bank tab label, meta strip, `#qhost`, bank
  tab, About tab, payload), the remaining bytes are byte-identical to the shell extracted from the Algorithms Unit 2
  Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key view and the footer are
  unchanged. The `:root` block is byte-identical to the shell it was spliced from and to `design-tokens.css`, and no
  new literal hex value was introduced (89 literal hex values outside `:root` in both the new paper and its Set 1
  predecessor), so the known Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**56 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response;
  all four tabs open and the key tab stays locked until submit; a fully correct paper scores **35 / 35** with 25 `ok`
  palette buttons, 25 key cards and 25 filled solutions; one skipped MCQ, one wrong MCQ, an MSQ one option short and
  a wrong NAT score **29 / 35** with 21 correct, 3 wrong and 1 unattempted; an MSQ with one extra option ticked loses
  its 2 marks (**33 / 35**), confirming that an MSQ earns nothing unless the exact set is selected and that there is
  no negative marking; an empty paper scores **0 / 35** with 25 `skip` buttons; every card carries `data-subject`,
  `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`, with lowercase
  difficulty values; the Question Bank tab renders 75 cards with no active question repeated; and the About tab
  carries its three sections.
- `index.html` holds all **1650** questions. Its data block was updated in place: the new Algorithms Unit 2 record was
  inserted at the head of `tests` with an `archives` entry pointing at the frozen Set 1 copy, and the superseded
  2026-10-27 record was retargeted at the archived copy so its link still resolves. The 25 new question records were
  appended. No unit had to be registered — Algorithms Units 1–7 were already in the portal's `units` table. The static
  header strings were recomputed from the data block and now read 65 units, 40 sets published and 1650 solved
  questions / records, with 281 subtopics. Every path in the data block resolves against the repository tree.
- Hygiene: the paper is filed at exactly one path, `algorithms/sorting-divide-conquer/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (66 papers, 35 current and 31 archived); no
  temporary or loose file was left at the repository root.
- Open items inherited unchanged, and not fixed by this run because each touches files it did not create: the literal
  hex outside `:root` in the shared shell; the two legacy `proof-techniques` archive files that still carry an older
  `:root`; the two current papers in `digital-logic/number-systems`; the two portal cards that launch an archived run
  while a current paper exists; and two pre-existing stem collisions inside Unit 1 of this subject
  (`ALG-U1-Q29`/`ALG-U1-Q04` and `ALG-U1-Q45`/`ALG-U1-Q16`), found by this run's portal-wide duplicate check and left
  untouched because the bank is append-only.

- **2026-10-28, Computer Networks → Unit 2 (Data Link Protocols & MAC), Set 2 of 2.** MODE A: one subject was
  drawn uniformly at random with an unseeded `random.SystemRandom()` choice over the 4 subjects that had no paper
  dated 2026-10-28 (draw index 3 of 4), giving **Computer Networks**. `runs[]` sorted by `(date, run)` gives the most
  recent paper as `{date 2026-10-27, run 3, unit 2, data-link-mac, Set 1 of 2}`. Unit 2 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and
  step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 2 now holds exactly 50
  questions — the cap — and the next Computer Networks run advances
  `(index_of(data-link-mac) + 1) mod 6 = (1 + 1) mod 6 = 2` → **Unit 3, Network Layer: IP Addressing & Subnetting**.
  The Set 1 paper was moved to
  `computer-networks/data-link-mac/archive/gate_cn_mock_2_2026-10-27_run1.html` with its content frozen, and the Set 2
  paper took the canonical filename. No override was used, no unit exceeded 50 questions and no second pass has
  started.
- Coverage this run: all five Unit 2 subtopics — stop-and-wait ARQ (5), Go-back-N and selective repeat (5), pure and
  slotted ALOHA (5), CSMA/CD, CSMA/CA and backoff (5), Ethernet, switches and bridges (5). Composition 15 MCQ / 5 MSQ
  / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="computer-networks"`, `data-unit="data-link-mac"`, `data-unit-number="2"` and its subtopic slug.
- All 25 items are new: `CN-U2-Q26`..`CN-U2-Q50` did not exist in the bank, and every stem was compared against the
  75 banked Computer Networks items with a string-normalised check (tags stripped, case and punctuation removed).
  That check caught one collision — this run's stop-and-wait MSQ opened with the same sentence as `CN-DL2-Q04` — and
  the stem was rewritten to name the receiver and the timer before shipping. After the rewrite: zero stem collisions
  and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** Utilisation after halving the propagation delay:
  `U = 0.2` implies `2Tp = 4Tt`, so the new figure is `1/3 = 33.3%` (Q02); the 100 Mbps / 1 ms link gives
  `80 µs / 2080 µs = 3.85%` (Q03); the frame count for a full pipe is `(1 + 100)/1 = 101` (Q05) and `(1 + 60)/1 = 61`
  (Q10); the Go-Back-N window of 10 gives `10/101 = 9.9%` (Q08); pure ALOHA at `G = 0.5` gives
  `0.5·e⁻¹ = 0.1839` (Q13); eight slotted stations give `(7/8)⁷ = 39.27%`, rounded to **39** (Q15); the 51.2 µs slot
  gives `2 × 10⁸ × 25.6 µs = 5120 m` (Q18); the backoff expectation is `(0 + … + 15)/16 = 7.5` (Q20); and the
  spanning tree of `K₄` blocks `6 − 3 = 3` links (Q25). **10 of 10 computed answers reproduced; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: a timeout must cover the frame time
  plus one round trip plus the acknowledgement plus a margin (Q01); one outstanding frame means one buffer, one
  sequence bit and a timeout above the round trip (Q04); selective repeat takes `2^(m−1) = 4` numbers from a 3-bit
  field while Go-Back-N may take 7 (Q06); a Go-Back-N receiver has a window of one and re-acknowledges the last
  in-order frame (Q07); a single loss costs a whole window (Q09); slotted ALOHA halves the vulnerable period to `T`
  and doubles the ceiling to `1/e` (Q11, Q12); the two ALOHA curves meet only at `G = 0` (Q14); collision `i` gives
  `2^i` slots numbered from 0, so `i = 3` means `0..7` (Q16); the jam signal exists because stations are spread along
  the cable (Q17); CSMA/CA acknowledges every data frame because detection is impossible in radio, and `SIFS` is
  shorter than `DIFS` (Q19); a bridge learns from the source and forwards by the destination (Q21); a hub repeats
  everything (Q22); a switch filters a frame whose destination is on the incoming port (Q23); and 802.3 has no
  link-layer acknowledgement at all (Q24).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 3, (C) 4 and
  (D) 4, and the five MSQ answer sets are (A,B,D), (A,B,C), (B,C,D), (A,B,C) and (A,C,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **75 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (10) or `ORIGINAL_SYNTHESIS` (15), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **75** banked items that are not part of the active set — the 50
  questions of Unit 1 and the 25 of Unit 2 Set 1 — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Set 2 questions do not appear there (verified: `CN-U2-Q26` occurs nowhere in the
  bank tab). Units 3–6 are not shown as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions replaced by placeholders (title, header sub-line, bank tab label, meta strip, `#qhost`, bank
  tab, About tab set label, payload), the remaining bytes are byte-identical to the shell extracted from the
  Computer Networks Unit 2 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key view
  and the footer are unchanged. The `:root` block is byte-identical to the shell it was spliced from and to
  `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4 deviation below is
  untouched and was not partially fixed for one paper. The paper also inherits, unchanged, the other open
  shell-level items recorded below.
- The paper was exercised in a jsdom harness before shipping (**80 structural checks and 30 behavioural checks, all
  passing**): nothing is
  revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question
  pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00); the palette reaches
  `na`, `ans`, `amr` and `mrk`; all four tabs open and the key tab stays locked until submit; a fully correct paper
  scores **35 / 35** with 25 `ok` palette buttons and 25 key cards; one wrong MCQ, one skipped MCQ, an MSQ one option
  short and a wrong NAT score **29 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that an MSQ earns
  nothing unless the exact set is selected and that there is no negative marking; an empty paper scores **0 / 35**
  with 25 `skip` buttons; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`,
  `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty values; and the About tab carries its
  three sections.
- `index.html` holds all **1625** questions. Its data block was updated in place: the new Computer Networks Unit 2
  record was inserted at the head of `tests`, and the superseded 2026-10-27 record was retargeted at the archived copy
  so its link still resolves. The 25 new question records were appended. No unit had to be registered — Computer
  Networks Units 1–6 were already in the portal's `units` table. The static header strings were recomputed from the
  data block and now read 65 units, 39 sets published and 1625 solved questions / records, with 281 subtopics. Every
  path in the data block resolves against the repository tree.
- Hygiene: the paper is filed at exactly one path, `computer-networks/data-link-mac/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper; no temporary or loose file was left at the
  repository root.

- **2026-10-28, Computer Architecture → Unit 2 (CPU Control Design & Data Path), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random with an unseeded `random.SystemRandom()` draw over the 5 subjects that had no paper
  dated 2026-10-28 (draw index 1 of 5), giving **Computer Architecture**. `runs[]` sorted by `(date, run)` gives the
  most recent paper as `{date 2026-10-27, run 1, unit 2, datapath-control-unit, Set 1 of 2}`. Unit 2 held **25**
  questions, below `UNIT_QUESTION_CAP = 50`, and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so
  step B3 held and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 2 now
  holds exactly 50 questions — the cap — and the next Computer Architecture run advances
  `(index_of(datapath-control-unit) + 1) mod 6 = (1 + 1) mod 6 = 2` → **Unit 3, Memory Hierarchy & Cache Memory**.
  The Set 1 paper was moved to
  `computer-architecture/datapath-control-unit/archive/gate_co_mock_2_2026-10-27_run1.html` with its content frozen,
  and the Set 2 paper took the canonical filename. No override was used, no unit exceeded 50 questions and no second
  pass has started.
- Coverage this run: all four Unit 2 subtopics — hardwired control (6), microprogrammed control (6), ALU & datapath
  timing (7) and bus architectures (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard;
  marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="computer-architecture"`,
  `data-unit="datapath-control-unit"`, `data-unit-number="2"` and its subtopic slug.
- All 25 items are new: `CO-U2-Q26`..`CO-U2-Q50` did not exist in the bank, and every stem and every option set was
  compared against the 25 banked Computer Architecture items with a string-normalised check (tags stripped, case and
  punctuation removed): zero collisions, and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** The PLA connection count of Q03 is
  `12 × 8 + 8 × 10 = 176`; the one-hot sequencer of Q02 needs one flip-flop per state, so **11**; the microprogram
  timing of Q08 is `6 × 5 ns × 10⁶ = 30 ms`; the block-ripple adder of Q16 needs `15 × 5 + 2 = 77 ns`, fifteen
  inter-block carries and not sixteen; the address space of Q22 is `2²⁴ = 16 777 216`; the bus bandwidth of Q23 is
  `(8 bytes / 2 clocks) × 100 MHz = 400 MB/s`; and the datapath of Q18 gives `2 + 7 + 1.5 + 1 = 11.5 ns`, a maximum
  frequency of `86.96 MHz`, a pipelined period of `max(10, 4.5) = 10 ns`, and `54.05 MHz` when the ALU doubles —
  a factor of 0.62, not 0.5. **6 of 6 computed answers reproduced; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: the control step matrix has one row
  per T-state and one column per control signal (Q01); a don't-care entry lets the minimiser choose either value, so
  the minimised network may assert a signal for an undefined opcode — safe only because no correct program fetches
  one (Q05); an unconditional clause is a single term ORed with the conditional one, `T0 + T3 · MR` (Q06); the
  sequencing field, not the condition-select field, supplies a branch target (Q07); the mapping ROM turns an opcode
  into a microprogram address (Q09); the mapping ROM is a table, so two opcodes may share one microprogram, and a
  microcoded call needs a return-address stack because one counter cannot remember where to return (Q10); vertical microcode pays extra clocks for decoding, so 2 microinstructions × 3 clocks lose
  to 4 horizontal clocks (Q11); a conditional microinstruction multiplexes the microprogram counter between the
  next-address field and the incrementer (Q12); the ALU's function-select inputs are driven by the control unit (Q13);
  overflow is the XOR of the carries into and out of the sign bit, while the carry flag is the unsigned carry out
  (Q17); one read port delivers one value per cycle (Q15); and a non-burst transfer must serialise the address and data phases
  because the address is needed before the data can be selected, so the two phases cannot overlap (Q25).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 3, (C) 4 and
  (D) 4, and the five MSQ answer sets are (A,B,C), (A,C,D), (A,B,D), (A,C,D) and (A,B,C).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **25 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (10) or `ORIGINAL_SYNTHESIS` (15), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **25** banked items that are not part of the active set — the 25
  questions of Unit 2 Set 1 — under one Unit 2 accordion and one heading per subtopic, every solution collapsed. The
  25 active Set 2 questions do not appear there (verified: `CO-U2-Q26` and `CO-U2-Q50` occur nowhere in the bank
  tab). Units 1 and 3–6 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the ten payload regions replaced by placeholders (title, brand line, header sub-line, candidate ID, bank tab label,
  meta strip, `#qhost`, bank tab, About tab, payload), the remaining **27 615 bytes are byte-identical** to the shell
  extracted from the Programming and Data Structures Unit 3 Set 1 paper, so the `<style>` block, the exam `<script>`,
  the palette, the answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new
  paper, `index.html` and `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4
  deviation below is untouched and was not partially fixed for one paper. The paper also inherits, unchanged, the
  other open shell-level items recorded below.
- The paper was exercised in a jsdom harness before shipping (**49 structural checks plus the behavioural run, all
  passing**): nothing is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline`
  markup in the question pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00,
  one card visible, every input enabled); the palette reaches `na`, `ans`, `amr` and `mrk`; all four tabs open and
  the key tab stays locked until submit; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong and
  25 `ok` palette buttons; one skipped MCQ, one wrong MCQ, an MSQ one option short and a wrong NAT score **31 / 35**
  with 21 correct, 3 wrong and 1 unattempted; an empty paper scores **0 / 35** with 25 `skip` buttons; an MSQ with
  one extra option ticked scores **0 / 35**, confirming that an MSQ earns nothing unless the exact set is selected;
  every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty`
  and `data-source`, with lowercase difficulty values; the Question Bank tab renders 25 cards with no active question
  repeated; and the About tab carries its three sections.
- `index.html` holds all **1600** questions. Its data block was updated in place: the new Computer Architecture Unit 2
  record was inserted at the head of `tests`, and the superseded 2026-10-27 record was retargeted at the archived copy
  so its link still resolves. The 25 new question records were appended. No unit had to be registered — Computer
  Architecture Units 1–6 were already in the portal's `units` table. The static header strings were recomputed from
  the data block and now read 65 units, 38 sets published and 1600 solved questions / records, with 281 subtopics.
  Every path in the data block resolves against the repository tree.
- Hygiene: the paper is filed at exactly one path, `computer-architecture/datapath-control-unit/`, and nowhere else;
  `find . -name "*.html"` returns `index.html` plus one file per paper (65 files, 35 current and 29 archived); no
  temporary or loose file was left at the repository root.

- **2026-10-28, Programming and Data Structures → Unit 3 (Linear Data Structures), Set 1 of 2.** MODE A: one subject
  was drawn uniformly at random with an unseeded `random.SystemRandom()` draw over the 6 subjects that had no paper
  dated 2026-10-28 (draw index 5 of 6), giving **Programming and Data Structures**. `runs[]` sorted by `(date, run)`
  gives the most recent paper as `{date 2026-10-27, run 4, unit 2, pointers-memory, Set 2 of 2}`. Unit 2 held **50**
  questions — exactly `UNIT_QUESTION_CAP = 50` — so step B3 failed on the cap and step B4 advanced one unit:
  `(index_of(pointers-memory) = 1 + 1) mod 7 = 2` → **Unit 3, Linear Data Structures**. The modulo applied to the
  advance, not to the day offset. Unit 3 had no folder and no paper, so no file was moved to `archive/`; the new paper
  is Set 1 of 2 and the unit now stands at 25 questions. The next Programming and Data Structures run re-selects Unit 3
  (25 < 50, 0 days current) and closes it at exactly 50. No override was used and no unit exceeded 50 questions.
- Coverage this run: all four Unit 3 subtopics — arrays and multidimensional arrays (7), singly, doubly and circular
  linked lists (6), stacks, infix and postfix (6), queues, circular queues and deques (6). Composition 15 MCQ / 5 MSQ /
  5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="programming-data-structures"`, `data-unit="linear-data-structures"`, `data-unit-number="3"` and its
  subtopic slug.
- All 25 items are new: `DS-U3-Q01`..`DS-U3-Q25` did not exist in the bank, and every stem was compared against all
  1550 questions already in the portal data block with a string-normalised check (tags stripped, case and punctuation
  removed): zero stem collisions and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** Address arithmetic Q1–Q5:
  `1000 + (3·8 + 2)·4 = 1104`, `2000 + (1·3 + 2)·4 = 2020`, `|12 − 5|·4 = 28`, `(1+2+…+7) + 3 = 31`,
  `((1·3 + 2)·4 + 3)·4 = 92`. Linked lists: the reversal loop executes 6 times for 6 nodes; the Floyd walk on
  1→…→7 with 7→4 first meets after 4 steps at node 5; the Josephus run with `k = 2` eliminates 2, 4, 6, 1, 5, 3 and
  leaves 7. Stacks: `6 2 / 1 + 3 *` evaluates to 12, `5 3 + 8 2 - *` to 48, the converter returns `A B C * +` and
  `A B + C D - * E +`, and of the four offered permutations only `3 1 2 5 4` is unreachable (the full enumeration of
  the 5! orders confirms 42 producible sequences, the Catalan number `C₅`). Queues: `rear = 5` after 5 enqueues,
  `rear = 1` after 5 enqueues / 3 dequeues / 4 enqueues, capacity 9 in a 10-slot buffer, 8 pushes through the
  two-stack queue, and the print-and-rotate order `1 3 5 2 6 4` with 2 in fourth place. **All recomputations
  reproduced the keyed answers; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: decay peels one dimension per
  subscript, and `sizeof` suppresses it, so `sizeof(A[0])` is the whole row and not a pointer (Q06, Q07); a singly
  linked list with a head pointer alone gives Θ(1) only at the front, and a tail pointer does not make tail deletion
  constant (Q08, Q12); a stack can only ever emit what is on top, which is why `3 1 2 …` is impossible (Q19); a
  circular queue with all `n` slots usable cannot distinguish full from empty without a counter (Q24); and a deque
  restricted at one end is a stack, restricted at both is a queue (Q24).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B), (A,C), (A,B,C), (A,C) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **100 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the 50
  questions of Unit 1 and the 50 of Unit 2 — under one accordion per unit and one heading per subtopic, every solution
  collapsed. Unit 3 has no banked items outside the active set, so the tab closes with "Units 3–7 have no banked
  questions yet". The 25 active questions do not appear there (verified: the string `DS-U3-Q` occurs nowhere in the
  bank tab).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the ten payload regions replaced by placeholders (title, brand line, header sub-line, candidate ID, bank tab label,
  meta strip, `#qhost`, bank tab, About tab, payload), the remaining **27 707 bytes are byte-identical** to the shell
  extracted from the Programming and Data Structures Unit 2 Set 2 paper, so the `<style>` block, the exam `<script>`,
  the palette, the answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new
  paper, `index.html` and `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4
  deviation below is untouched and was not partially fixed for one paper. The paper also inherits, unchanged, the
  three other open shell-level items recorded below.
- The paper was exercised in a jsdom harness before shipping (**43 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the question pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response;
  all four tabs open and the key tab stays locked until submit; all 25 answered correctly scores **35 / 35** with 25
  correct, 0 wrong, 25 `ok` palette buttons and 25 key cards; one skipped MCQ, one wrong MCQ and an MSQ one option
  short score **31 / 35** with 22 correct, 2 wrong and 1 unattempted; an empty paper scores **0 / 35** with 25 `skip`
  buttons; an MSQ with one extra option ticked scores **0 / 35**, confirming that an MSQ earns nothing unless the exact
  set is selected; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`, with lowercase difficulty values; the Question Bank tab renders 100 cards with
  no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1575** questions. Its data block was updated in place: the new Programming and Data
  Structures Unit 3 record was inserted at the head of `tests` so it renders first for 2026-10-28 with
  `archives: []`, and the 25 new question records were appended. No unit had to be registered — Programming and Data
  Structures Units 1–7 were already in the portal's `units` table. The static header strings were recomputed from the
  data block and now read 65 units, 37 sets published and 1575 solved questions / records, with 281 subtopics. Every
  path in the data block resolves against the repository tree.
- Hygiene: the paper is filed at exactly one path, `programming-data-structures/linear-data-structures/`, and nowhere
  else; `find . -name "*.html"` returns `index.html` plus one file per paper (64 files, 35 current and 28 archived);
  no temporary or loose file was left at the repository root; and the pre-existing `digital-logic/number-systems`
  duplicate noted below was not touched by this run.

- **2026-10-28, Theory of Computation → Unit 4 (Turing Machines & Decidability), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random with an unseeded `random.SystemRandom()` draw over the 7 subjects that had no paper
  dated 2026-10-28 (draw index 6 of 7), giving **Theory of Computation**. `runs[]` sorted by `(date, run)` gives the
  most recent paper as `{date 2026-10-27, run 7, unit 4, turing-machines-decidability, Set 1 of 2}`. Unit 4 held **25**
  questions, below `UNIT_QUESTION_CAP = 50`, and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so step
  B3 held and step B4 was not reached: Unit 4 was generated again, closing it at exactly 50. The next Theory of
  Computation run advances `(index_of(turing-machines-decidability) + 1) mod 4 = 0` → **Unit 1, Regular Languages &
  Finite Automata**, and every unit of the subject will then be at the cap, so a second pass starts there; it is
  recorded here as the first such wrap. No override was used and no unit exceeded 50 questions.
- Coverage this run: all five Unit 4 subtopics — standard TM models and variants (5), recursive vs recursively
  enumerable (5), halting problem and undecidability (5), Rice's theorem and reductions (5), Chomsky hierarchy
  summary (5). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 =
  35. Every question carries `data-subject="theory-of-computation"`, `data-unit="turing-machines-decidability"`,
  `data-unit-number="4"` and its subtopic slug.
- All 25 items are new: `TOC-U4-S2-Q01`..`TOC-U4-S2-Q25` did not exist in the bank, and every stem was compared
  against the 175 banked Theory of Computation items with a string-normalised check (tags stripped, case and
  punctuation removed): zero stem collisions, and no id overlap. Two stems that opened with the bare words "Which of
  the following statements is TRUE?" were rewritten to name their subject matter before shipping, for exactly that
  reason.
- **Every countable answer was recomputed by script, not by hand.** The configuration count of Q15 is
  `5 × 6 × 2⁶ = 1920`; the input count of Q25 is `1 + 2 + 4 + 8 = 15` strings over `{0, 1}` of length at most 3; the
  recursive count of Q10 is `1 + 0 + 0 + 1 = 2` over `L₁` recursive, `L₂` r.e. non-recursive, `L₃ = L̄₂` and
  `L₄ = L₂ ∪ L₃ = Σ*`; the union-closure count of Q05 is 4 of 4; and the r.e. count of Q20 is 3 — items (ii), (iii) and
  (v), with (i) `L(M) = ∅` and (iv) "does not halt on ε" both outside the r.e. class. **5 of 5 answers reproduced;
  0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: halting states are exactly the states
  where δ is undefined, so a loop is the absence of an answer rather than a rejection (Q01); a universal machine is a
  recogniser and never a decider, because it inherits the loop (Q02); the r.e. languages are the ranges of total
  computable functions (Q03); an enumerator semi-decides but does not decide (Q04); the r.e. class is closed under
  union and intersection and not under complement (Q16); a short input does not bound a computation, so `HALT_ε` is
  undecidable while still r.e. (Q13); a bound that is a function of the input is a clock, so bounded halting is
  decidable (Q14); `K` is complete for the r.e. languages (Q21); the universal halting question reduces to the
  existential one and not the reverse, and `{⟨M⟩ : M halts on every input}` is not r.e. (Q22); the multi-tape
  simulation costs a square while the two-way-tape fold costs a factor of `n`, so (B) of Q23 is the false one;
  context-free languages are closed under complement and not under intersection (Q24); and Rice's theorem reaches
  neither the number of states nor space usage (Q09, Q19).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 3 times, (B) 4, (C) 4 and
  (D) 4, and the five MSQ answer sets are (A,C), (B,D), (A,D), (A,B) and (A,C,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **175 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **175** banked items that are not part of the active set — the 50
  questions of each of Units 1, 2 and 3 and the 25 of Unit 4 Set 1 — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active Set 2 questions do not appear there (verified: the string
  `TOC-U4-S2` occurs nowhere in the bank tab). The Units 1–3 accordions are carried over byte for byte from the
  shipped Set 1 paper; the Unit 4 Set 1 accordion is generated from `master_bank.json`.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the nine payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining **27 926 bytes are byte-identical** to the shell extracted
  from the Theory of Computation Unit 4 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html`
  and `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4 deviation below is
  untouched and was not partially fixed for one paper. The paper also inherits, unchanged, the three other open
  shell-level items recorded below (no explicit `:focus-visible` selector, palette fills on the `--green`/`--red`/
  `--violet` tokens rather than their `-d` variants, and the two legacy `proof-techniques` archive files).
- The paper was exercised in a jsdom harness before shipping (**49 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response;
  all four tabs open and the key tab stays locked until submit; all 25 answered correctly scores **35 / 35** with 25
  correct, 0 wrong, 25 `ok` palette buttons and 25 key cards; one skipped MCQ, one wrong MCQ and an MSQ one option
  short score **31 / 35** with 22 correct, 2 wrong and 1 unattempted; an empty paper scores **0 / 35** with 25 `skip`
  buttons; an MSQ with one extra option ticked scores **0 / 35**, confirming that an MSQ earns nothing unless the
  exact set is selected; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`,
  `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty values; the Question Bank tab renders
  175 cards with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1550** questions. Its data block was updated in place: the existing Theory of Computation
  Unit 4 record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1 copy (so
  the card reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No unit had to
  be registered — Theory of Computation Units 1–4 were already in the portal's `units` table. The static header
  strings were recomputed from the data block and now read 65 units, 36 sets published and 1550 solved questions /
  records, with 281 subtopics. Every path in the data block resolves against the repository tree.

- **2026-10-28, Discrete Mathematics → Unit 7 (Counting & Combinatorics), Set 1 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 0 of 11),
  giving **Discrete Mathematics**. `runs[]` sorted by `(date, run)` gives the most recent paper as `{date 2026-10-27,
  run 5, unit 6, induction-recursion, Set 2 of 2}`. Unit 6 held **50** questions — exactly `UNIT_QUESTION_CAP = 50` —
  and had been current for 1 day, so step B3 failed on the cap and step B4 advanced one unit:
  `(index_of(induction-recursion) = 5 + 1) mod 16 = 6` → **Unit 7, Counting & Combinatorics**. The modulo applied to
  the advance, not to the day offset. Unit 7 had no folder and no papers, so no paper was moved to `archive/`; the new
  paper took the canonical filename and the unit folder holds exactly one current paper. No override was used, no unit
  exceeded 50 questions and no second pass has started.
- Coverage this run: all five Unit 7 subtopics — permutations and combinations (5), stars and bars (5), binomial and
  multinomial coefficients (5), inclusion-exclusion counting (5) and double counting (5). Composition 15 MCQ / 5 MSQ /
  5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="discrete-mathematics"`, `data-unit="combinatorics"`, `data-unit-number="7"` and its subtopic slug.
- All 25 items are new: `DM-CB7-Q01`..`DM-CB7-Q25` did not exist in the bank, and every stem and every option set was
  compared against the 375 previously banked Discrete Mathematics items with a string-normalised check (tags stripped,
  case and punctuation removed): zero collisions, and no id overlap.
- The Question Bank tab of this paper lists 375 solved questions: Units 1–5 (50 each), Unit 6 (50, now that Set 2 is
  superseded and its 25 items moved from the active test into the tab) and Unit 16 (75). The 25 active Unit 7 items are
  banked in `master_bank.json` but deliberately not repeated in the tab, so the tab holds 400 − 25 = 375.
- This paper inherits the four open shell items recorded below unchanged (literal hex outside `:root`, no explicit
  `:focus-visible` selector, palette fills on the `--green`/`--red`/`--violet` tokens rather than their `-d` variants,
  and the two legacy `proof-techniques` archive files). Its `<style>` and `<script>` blocks are byte-identical to the
  paper it was generated from, so shell parity holds.

- **2026-10-28, Digital Logic → Unit 3 (Sequential Circuits: Flip-Flops & Registers), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index
  2 of 11), giving **Digital Logic**. `runs[]` sorted by `(date, run)` gives the most recent paper as `{date 2026-10-27,
  run 5, unit 3, sequential-flipflops, Set 1 of 2}`. Unit 3 held **25** questions, below `UNIT_QUESTION_CAP = 50`, and
  had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held and step B4 was not reached: the
  current unit was generated again. This is Set 2 of 2, so Unit 3 now holds exactly 50 questions — the cap — and the
  next Digital Logic run advances `(index_of(sequential-flipflops) + 1) mod 4 = (2 + 1) mod 4 = 3` → **Unit 4,
  Sequential Circuits: Counters & State Machines**. No override was used, no unit exceeded 50 questions and no second
  pass has started.
- Coverage this run: all four Unit 3 subtopics — latches and flip-flops (5), setup and hold times (7), characteristic
  equations (6) and shift registers (7). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard;
  marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="digital-logic"`,
  `data-unit="sequential-flipflops"`, `data-unit-number="3"` and its subtopic slug.
- All 25 items are new: `DL-U3B-Q01`..`DL-U3B-Q25` did not exist in the bank, and every stem and every option set was
  compared against the 150 banked Digital Logic items with a string-normalised check (tags stripped, case and
  punctuation removed): zero collisions, and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** The maximum clock frequency of Q06 is
  `1 / (2 + 5.5 + 0.5 ns) = 125 MHz`; the two-flip-flop circuit of Q15 was iterated to the sequence
  `00, 01, 10, 11, 00`; the 3-bit Johnson counter of Q12 has a 6-state main cycle, leaving **2** unused states, and the
  5-bit counter of Q23 leaves **22** of its 32; the right shift of Q11 takes `1101` to `0011` in two clocks and the
  left shift of Q13 takes `1011` to `0110`; the minimum period of Q22 is `1.5 + 6.5 + 2.0 = 10 ns`; the hold slack of
  Q24 is `1.2 + 0.5 − 1.4 − 0.2 = 0.1 ns`; the race-around count of Q25 is **2** toggles inside a 10 ns high phase with
  a 4 ns settling delay; and the feedback register of Q20 was iterated in code — the cycle from `1000` closes after
  **15** steps, visits every non-zero state, and `0000` is a lock-up. The three conversions of Q18 were checked over
  both present states and every input pair, and `S = J, R = K` was confirmed to fail as an SR-to-JK conversion.
  **25 of 25 answers reproduced; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: the master–slave output moves when the
  slave opens, not when the master samples (Q01); `(0, 0)` is the memory condition of a NOR latch, not the forbidden
  one (Q02); edge-triggering is created by non-overlapping enables (Q03); setup contains the clock period and hold does
  not (Q05); positive skew relaxes setup and tightens hold by the same amount (Q07, Q17); `J = 1, K = 0` is a set
  (Q08); `J = Q, K = Q̄` holds and `T = Q` forces 0 (Q09, Q10); a gated latch is level-sensitive, so it can change
  several times per clock period (Q16); a maximal 4-stage LFSR has period `2⁴ − 1 = 15` (Q14); and a ring counter has
  `n` states while a Johnson counter has `2n`, neither being self-starting (Q19).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,C,D), (A,B,D), (A,B,C), (A,B,D) and (B,C,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 2 for this subject (both Unit 1), the Question
  Bank tab shows **125 solved** and **2 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (11) or `ORIGINAL_SYNTHESIS` (14), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **125** banked items that are not part of the active set — the 50
  questions of Unit 1, the 50 of Unit 2 and the 25 of Unit 3 Set 1 — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active Set 2 questions do not appear there (verified: `DL-U3B-Q` occurs
  nowhere in the bank tab). Unit 4 is reported on one line rather than as an empty accordion.
- Bank repair this run: the Unit 3 Set 1 records had been banked without `question_html`, and the 25 Unit 2 Set 2
  records carried only the question number in that field. Both sets were recovered from the papers that hold them and
  written back into `digital-logic/question-bank/master_bank.json`, so every banked Digital Logic record now carries
  its card markup. No paper was altered by the repair.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining **27 516 bytes are byte-identical** to the shell extracted
  from the Digital Logic Unit 3 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key
  view and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html` and
  `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4 deviation below is
  untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**44 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` and returns through Unmark review and Clear response;
  all four tabs open and the key tab stays locked until submit; all 25 answered correctly scores **35 / 35** with
  25 correct, 0 wrong, 25 `ok` palette buttons and 25 key cards; one wrong MCQ, one skipped MCQ, an MSQ one option
  short and a wrong NAT score **29 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that an MSQ earns
  nothing unless the exact set is selected and that there is no negative marking; an empty paper scores **0 / 35**
  with 25 `skip` buttons; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`,
  `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty values; the Question Bank tab renders
  125 cards with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1475** questions. Its data block was updated in place: the existing Digital Logic Unit 3
  record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1 copy (so the card
  reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No unit had to be
  registered — Digital Logic Units 1–4 were already in the portal's `units` table. The static header strings were
  recomputed from the data block and now read 65 units and 1475 solved questions / records, with 281 subtopics. Every
  path in the data block resolves against the repository tree.

- **2026-10-28, Databases → Unit 2 (SQL & Advanced Querying), Set 2 of 2.** MODE A: one subject was drawn uniformly
  at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 9 of 11), giving
  **Databases**. `runs[]` sorted by `(date, run)` gives the most recent paper as `{date 2026-10-26, run 2, unit 1,
  er-relational-algebra, Set 2 of 2}`. Unit 1 held **50** questions, exactly `UNIT_QUESTION_CAP = 50`, so step B3's
  cap test failed and step B4 advanced exactly one unit: `(index_of(er-relational-algebra) + 1) mod 5 = (0 + 1) mod
  5 = 1` → **Unit 2, SQL & Advanced Querying** (`sql-querying`). Unit 2 already held 25 questions from Set 1, so
  this set closes it at the cap and the next Databases run advances `(1 + 1) mod 5 = 2` → **Unit 3, Database
  Normalization**. No override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all five Unit 2 subtopics — DDL, DML and DCL (5), nested and correlated subqueries (5),
  aggregates with GROUP BY and HAVING (5), joins and outer joins (5), views, triggers and constraints (5).
  Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every
  question carries `data-subject="databases"`, `data-unit="sql-querying"`, `data-unit-number="2"` and its subtopic
  slug.
- All 25 items are new: `DB-U2-Q26`..`DB-U2-Q50` did not exist in the bank, and every stem and every option set was
  compared against the 75 banked Databases items (Units 1 and 2 Set 1) with a string-normalised check (tags stripped,
  case and punctuation removed): zero collisions, and no id overlap. The five stems that open "With the schema and
  data below" are distinguished by their query blocks, which is why the comparison is made over the full card text
  rather than the stem alone.
- **Every countable answer was recomputed by script, not by hand.** The one shared dataset
  (6 students, 3 courses, 10 enrollments, one unenrolled student and one ungraded enrollment) was replayed in Python
  against SQL semantics: the cascade chain `dept → emp → dependent` gave **4** rows removed by
  `DELETE FROM dept WHERE dno = 1` (Q04); the doubly nested correlated query gave **3** students above their own
  course's average, rolls 11, 13 and 16, with course averages 82.6, 79.667 and 68 (Q10); `COUNT(cid)`,
  `COUNT(DISTINCT cid)` and `COUNT(*)` gave **10, 3, 10** (Q11); the NULL-keyed table gave **3** groups with the
  NULL group holding **2** (Q13); the `HAVING AVG(cgpa) > 8.0` subquery left **1** department, CSE at 25.7/3 = 8.567
  against ECE 7.7 and MECH 6.8 (Q14); `NATURAL JOIN` gave **10** rows over **6** merged columns (Q16); the self-join
  with `a.roll < b.roll` gave **4** pairs, C(3,2) + C(2,2) + 0 (Q18); the `LEFT JOIN` with `e.marks > 80` in `ON`
  gave **8** rows, 5 matching pairs plus 3 NULL-extended students (Q20); and the updatable view over CSE gave **3**
  rows changed (Q24). The `NOT EXISTS` query of Q08 was re-evaluated row by row and returns rolls 12, 14 and 15, and
  the `UPDATE ... WHERE cid = 'C3'` of Q02 was traced to 73 and NULL. **25 of 25 answers reproduced; 0
  disagreements.**
- The conceptual items were settled against the standard rather than by taste: an omitted column takes its
  `DEFAULT`, so a `NOT NULL` column with a default accepts the row (Q01); NULL propagates through `marks + 5` but
  the row is still updated (Q02); `REVOKE ... RESTRICT` fails when the grantee has passed the privilege on, and
  `CASCADE` follows the dependency (Q03); one DML statement is atomic, so a `CHECK` violation on any row leaves the
  table unchanged, and dropping a table drops the grants on it (Q05); `COUNT(*)` over no rows is 0 while `SUM` and
  `MAX` are NULL (Q06); a scalar subquery returning five rows is a cardinality error, not a set comparison (Q07);
  the condition that defines what is being searched for belongs inside `EXISTS` (Q08); `EXISTS` counts rows and `IN`
  compares values, and a derived table cannot see a sibling table's columns without a lateral construct (Q09);
  `HAVING` without `GROUP BY` tests the single implicit group (Q12); grouped `SELECT` and `HAVING` may use only
  grouped columns and aggregates (Q15); `NATURAL JOIN` merges the shared column and is an inner join (Q16); `ON` and
  `WHERE` are interchangeable for an inner join and not for an outer one (Q17); an outer join preserves the
  preserved side even when nothing matches (Q19); `WITH CHECK OPTION` rejects a write that would fall outside the
  view (Q21); `INSTEAD OF` replaces the statement and is defined on views only (Q22); a `CHECK` condition may
  reference only the row being tested, so no subquery (Q23); and grouping destroys the one-to-one mapping that makes
  a view updatable (Q25).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 3 times, (B) 5, (C) 5
  and (D) 2, and the five MSQ answer sets are (A,C,D), (A,B), (A,C,D), (A,B,C) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 1 for this subject (Unit 1), the Question
  Bank tab shows **75 solved** and **1 verified GATE PYQ**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **75** banked items that are not part of the active set — the 50
  Unit 1 questions and the 25 Unit 2 Set 1 questions — under one accordion per unit and one heading per subtopic,
  every solution collapsed. The 25 active Set 2 questions do not appear there (verified: `DB-U2-Q26` and
  `DB-U2-Q50` occur nowhere in the bank tab). The Unit 1 accordion is carried over byte for byte from the shipped
  Set 1 paper; the Unit 2 Set 1 accordion is generated from `master_bank.json`.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta
  strip, `#qhost`, bank tab, About tab, payload), the remaining **27 707 bytes are byte-identical** to the shell
  extracted from the Databases Unit 2 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper,
  `index.html` and `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4
  deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**53 checks, all passing**, across five runs): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` or solution markup in
  the test pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card
  visible, every input enabled); the palette reaches `na`, `ans`, `amr`, `mrk` and back through Unmark review and
  Clear response; all four tabs open and the key tab stays locked until submit; all 25 answered correctly scores
  **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette buttons and 25 key cards; one wrong MCQ, one skipped MCQ, an
  MSQ one option short and a wrong NAT score **29 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that
  an MSQ earns nothing unless the exact set is selected and that there is no negative marking; an empty paper scores
  **0 / 35** with 25 `skip` buttons; every card carries `data-subject`, `data-unit`, `data-unit-number`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty values; the Question
  Bank tab renders 75 cards with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1450** questions. Its data block was updated in place: the existing Databases Unit 2
  record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1 copy (so the
  card reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No unit had to be
  registered — Databases Units 1–5 were already in the portal's `units` table. The static header strings were
  recomputed from the data block and now read 65 units, 35 sets published and 1450 solved questions / records, with
  281 subtopics. Every path in the data block resolves against the repository tree.

- **2026-10-27, Discrete Mathematics → Unit 6 (Mathematical Induction & Recursion), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index
  6 of 11), giving **Discrete Mathematics**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-27, run 4, unit 6, induction-recursion, Set 1 of 2}`. Unit 6 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **0** days, below `DAYS_PER_UNIT_MAX = 7`, so the cap test in
  step B3 held and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 6 now
  holds exactly 50 questions — the cap — and the next Discrete Mathematics run advances
  `(index_of(induction-recursion) + 1) mod 16 = (5 + 1) mod 16 = 6` → **Unit 7, Counting & Combinatorics**. The Set 1
  paper was moved to `discrete-mathematics/induction-recursion/archive/gate_dm_mock_6_2026-10-27_run1.html` with its
  content frozen, and the Set 2 paper took the canonical filename. No override was used, no unit exceeded 50
  questions and no second pass has started.
- Coverage this run: all four Unit 6 subtopics — weak and strong induction (7), structural induction (6), the
  well-ordering principle (6) and proof techniques and errors (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="discrete-mathematics"`, `data-unit="induction-recursion"`, `data-unit-number="6"` and its subtopic
  slug.
- All 25 items are new: `DM-IR6B-Q01`..`DM-IR6B-Q25` did not exist in the bank, and every stem and every option set was
  compared against the 350 banked Discrete Mathematics items with a string-normalised check (tags stripped, case and
  punctuation removed): zero collisions, and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** The sequence `a₁ = 3`, `a_{n+1} = a_n + 2n` was
  iterated to `a₁₂ = 135`, matching `n² − n + 3` (Q02); `∑_{i=1}^{20} i(i+1) = 20·21·22/3 = 3080` (Q07); the closure
  `2 ∈ S`, `x ∈ S ⇒ x+3 ∈ S` was generated by fixed point to give 98 as the largest element ≤ 100 (Q09); the least
  `n` with `n² > 50` is 8 (Q15); the 4- and 7-paise amounts were enumerated, giving exactly nine unmakeable values
  `{1, 2, 3, 5, 6, 9, 10, 13, 17}` and largest 17 (Q19); `n² + n + 41` was tested for primality, prime on
  `n = 1..39` and `1681 = 41²` at `n = 40` (Q22); and the identity `4^{k+1} − 1 = 4(4^k − 1) + 3` was checked for
  `k = 1..11` (Q05). The structural-induction claim of Q12 was settled by exhaustive generation: the closure of
  `ε` under `0x` and `x1` equals, for every length up to 9, exactly the set of binary strings avoiding `10` (55
  strings on each side). **25 of 25 answers reproduced; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: the step must be
  `∀k, P(k) ⇒ P(k+1)` for an arbitrary `k` (Q01); a stride-2 step from `P(1)` reaches only odd indices (Q03); a step
  of the form `P(k) ⇒ P(k−1)` establishes nothing above its base case (Q06); strong induction may be weakened to
  `P(k)` when the step uses only `P(k)`, but never strengthened to `P(k+1)` (Q04); structural induction grants the
  property for a rule's inputs only, not for every shorter formula (Q08, Q13); the well-ordering principle is
  equivalent to ordinary induction, not to the axiom of choice (Q14); minimality supplies every smaller case, not
  `P(m+1)` (Q16); `{1/n}` has no least element (Q17); the least counterexample in the prime-divisor proof must be
  composite (Q18); sufficiency is `P ⇒ Q` (Q21); the converse never substitutes for the contrapositive (Q23); and
  `4 | n²` does not force `4 | n`, with `n = 2` as the witness and `n = 3` not a counterexample at all (Q25).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 3 times, (B) 3, (C) 5 and
  (D) 4, and the five MSQ answer sets are (A,B,D), (A,B,C), (A,B,C), (A,C,D) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 2 for this subject (both Unit 1), the Question
  Bank tab shows **350 solved** and **2 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item
  is `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **350** banked items that are not part of the active set — the 50
  questions of each of Units 1–5, the 25 of Unit 6 Set 1 and the 75 of Unit 16 — under one accordion per unit and one
  heading per subtopic, every solution collapsed. The 25 active Set 2 questions do not appear there (verified: the
  string `DM-IR6B` occurs nowhere in the bank tab). Units 7–15 are reported on one line rather than as empty
  accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions replaced by placeholders (title, header sub-line, tab label, meta set chip, `#qhost`, palette,
  bank tab, About tab, payload), the remaining **26 519 bytes are byte-identical** to the shell extracted from the
  Discrete Mathematics Unit 6 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the answer-key
  view and the footer are unchanged. The `:root` block is byte-identical across the new paper, `index.html` and
  `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4 deviation below is
  untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**38 checks, all passing**, across four runs): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane,
  key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response;
  all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette buttons and 25 key cards; one
  wrong MCQ, one skipped MCQ, an MSQ one option short and a wrong NAT score **29 / 35** with 21 correct, 3 wrong and
  1 unattempted, confirming that an MSQ earns nothing unless the exact set is selected and that there is no negative
  marking; an empty paper scores **0 / 35** with 25 `skip` buttons; every card carries `data-subject`, `data-unit`,
  `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty
  values; all four subtopics appear; the Question Bank tab renders 350 cards with no active question repeated; the
  About tab carries its three sections; and all four tabs open.
- `index.html` holds all **1425** questions. Its data block was updated in place: the existing 2026-10-27 Discrete
  Mathematics Unit 6 record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1
  copy (so the card reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No unit
  had to be registered — Discrete Mathematics Units 1–16 were already in the portal's `units` table. The static
  header strings were recomputed from the data block and now read 65 units, 35 sets published and 1425 solved
  questions / records, with 281 subtopics. Every path in the data block resolves against the repository tree.

- **2026-10-28, Compiler Design → Unit 3 (Syntax Analysis: Bottom-Up Parsing), Set 2 of 2.** MODE A: one subject
  was drawn uniformly at random from the 8 subjects that had no paper dated 2026-10-28, with an unseeded
  `random.SystemRandom()` draw (draw index 1 of 8), giving **Compiler Design**. `runs[]` sorted by `(date, run)` gives
  the most recent paper as `{date 2026-10-27, run 5, unit 3, bottom-up-parsing, Set 1 of 2}`. Unit 3 held **25**
  questions — below `UNIT_QUESTION_CAP = 50` — and had been current for 1 day, below `DAYS_PER_UNIT_MAX = 7`, so step
  B3 held and step B4 was not reached: Unit 3 was generated again, closing it at exactly 50 questions. The next
  Compiler Design run advances `(index_of(bottom-up-parsing) + 1) mod 5 = 3` → Unit 4, Syntax-Directed Translation &
  Intermediate Code. No override was used and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — LR(0) items and the canonical collection (7), SLR(1) parsing and
  conflicts (5), LR(1) and LALR(1) parsers (7), operator-precedence parsing (6). Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="compiler-design"`, `data-unit="bottom-up-parsing"`, `data-unit-number="3"` and its subtopic slug.
- All 25 items are new: `CD-U3-S2-Q01`..`CD-U3-S2-Q25` did not exist in the bank, and no stem or option set repeats a
  banked Compiler Design item (Units 1, 2 and Unit 3 Set 1). No question is an official GATE PYQ: `verified_pyqs` is
  empty for this subject and nothing on the paper is claimed as official.
- **Every countable answer was recomputed by an LR engine written for this run, not by hand.** A closure/GOTO
  implementation built the canonical LR(0) collection, the SLR(1) table with FOLLOW-based reductions, the canonical
  LR(1) collection, the LALR(1) merge and the operator-precedence relations from FIRST and LAST. It returned: 20 LR(0)
  items for the expression grammar `E → E + T | T`, `T → T * F | F`, `F → ( E ) | id` (Q03); 7 LR(0) states for
  `S → C C`, `C → c C | d`, with `GOTO(I₀, C)` listed item by item (Q04, Q05); 10 canonical LR(1) states for the same
  grammar against 7 LALR(1) states, the three extra states being the split kernels (Q15); 2 conflicting cells, both
  shift/reduce, for `S → A a | b A c | d c | b d a`, `A → d` with `FOLLOW(A) = {a, c}` (Q12); one shift/reduce
  conflict on `=` for `S → L = R | R`, `L → * R | id`, `R → L` (Q10); and, for `E → E + E | E * E | ( E ) | id`,
  6 pairs satisfying `<·`, 6 satisfying `·>`, 1 satisfying `≌` and 12 pairs with no relation at all (Q23, Q24, Q25).
  The engine reproduces the shipped Set 1 answers (6 for the `·>` count, `( ≌ )` for the parenthesis pair), which is
  an independent cross-check of both papers. Grammar classes were checked mechanically rather than asserted:
  `S → a S b | ε` conflicts in LR(0) on `a` in the initial state but is SLR(1) (Q04); `S → C C`, `C → c C | d` and
  `S → a S | b S | a` are SLR(1); `S → A a | b A c | d c | b d a` has 2 SLR conflicts and none in LALR(1) (Q18);
  `S → a A d | b B d | a B e | b A e` has no canonical LR(1) conflict, 2 reduce/reduce conflicts after the merge on
  `d` and `e`, 14 LR(1) states against 13 LALR(1) states (Q19); and `S → A a | b A c | d c | b d a` has no conflict
  in its canonical LR(1) table (Q18). No grammar class claimed anywhere on the paper was left unchecked.
- The Question Bank tab inside the paper lists the **125** banked items that are not part of the active set — the 50
  of Unit 1, the 50 of Unit 2 and the 25 of Unit 3 Set 1 — under one accordion per unit and one heading per subtopic,
  every solution collapsed. The 25 active Set 2 questions do not appear there (verified: the string `CD-U3-S2` occurs
  nowhere in the bank tab). Units 4–5 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block and the exam `<script>` are byte-identical to the Set 1 paper, and the `:root` block is
  byte-identical across the new paper, `index.html` and `design-tokens.css`. The set of literal hex values outside
  `:root` is identical to the Set 1 paper's (40 values, none added), so the known Section 6.4 deviation below is
  untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**45 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and `mrk` through visiting, answering, marking and Clear response;
  all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette buttons and 25 key cards;
  every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty`
  and `data-source`, with lowercase difficulty values; 15 MCQ / 5 MSQ / 5 NAT and all four subtopics are present; the
  Question Bank tab renders 125 cards with no active question repeated; the About tab carries its three sections; and
  all four tabs open.
- `index.html` holds all **1525** questions. Its data block was updated in place: the existing 2026-10-27 Compiler
  Design Unit 3 record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1 copy
  (so the card reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No unit had
  to be registered — Compiler Design Units 1–5 were already in the portal's `units` table. The static header strings
  were recomputed from the data block and now read 65 units, 36 sets published and 1525 solved questions / records,
  with 281 subtopics. Every path in the data block resolves against the repository tree.

- **2026-10-27, Compiler Design → Unit 3 (Syntax Analysis: Bottom-Up Parsing), Set 1 of 2.** MODE A: one subject was
  drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 8
  of 11), giving **Compiler Design**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-27, run 4, unit 2, top-down-parsing, Set 2 of 2}`. Unit 2 held **50** questions — exactly
  `UNIT_QUESTION_CAP = 50` — so the cap test in step B3 failed and step B4 advanced exactly one unit:
  `(index_of(top-down-parsing) + 1) mod 5 = (1 + 1) mod 5 = 2` → **Unit 3, Syntax Analysis: Bottom-Up Parsing**
  (`bottom-up-parsing`). No override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — LR(0) items and the canonical collection (7), SLR(1) parsing and
  conflicts (7), LR(1) and LALR(1) parsers (6), operator-precedence parsing (5). Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="compiler-design"`, `data-unit="bottom-up-parsing"`, `data-unit-number="3"` and its subtopic slug.
- All 25 items are new: `CD-U3-Q01`..`CD-U3-Q25` did not exist in the bank, and every stem and every option set was
  compared against the 100 banked Compiler Design items (Units 1 and 2) with a string-normalised check (tags
  stripped, case and punctuation removed): zero collisions, and no id overlap.
- **Every countable answer was recomputed by an LR engine written for this run, not by hand.** A closure/GOTO
  implementation built the canonical LR(0) collection, the SLR(1) table with FOLLOW-based reductions, the canonical
  LR(1) collection and the LALR(1) merge for each grammar quoted on the paper. It returned: 10 LR(0) items for
  `S → A A`, `A → a A | b` (Q03); 7 states in its canonical LR(0) collection, with `I0`…`I6` listed item by item
  (Q09); 4 of those states holding a completed item (Q16); 10 LALR(1) states for `S → L = R | R`, `L → * R | id`,
  `R → L` against 14 canonical LR(1) states (Q12); 12 LALR(1) states for the expression grammar, against 22 canonical
  LR(1) states (Q23); 14 canonical LR(1) states with no conflict and 13 LALR(1) states with a reduce/reduce conflict
  for `S → a A d | b B d | a B e | b A e`, `A → c`, `B → c` (Q15); one SLR(1) conflict, a reduce/reduce conflict in
  column `a`, for `S → A a | B a`, `A → c`, `B → c` (Q18); and no SLR(1) conflict for `S → a S b | a`, whose only
  LR(0) conflict is the shift/reduce pair in the state holding `S → a ·` (Q10). The operator-precedence relations for
  `E → E + E | E * E | ( E ) | id` were computed from `FIRST` and `LAST`: `( ≐ )` is the only `≐` pair (Q06),
  `id ·> +` holds because `LAST(E) = {id, )}` (Q13), and exactly **6** ordered pairs satisfy `·>` (Q20).
  **Every one of the 25 answers was reproduced by an independent computation; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: an LR(0) item records progress
  through one production and never permutes the right side (Q01, Q02); closure adds the productions of the
  nonterminal after the dot and nothing else (Q08); SLR(1) reduces on `FOLLOW(A)` while LR(1) carries one lookahead
  per item (Q04, Q05); merging states with equal cores can create reduce/reduce conflicts only, because shifts depend
  on the core alone (Q11); the class nesting is LR(0) ⊂ SLR(1) ⊂ LALR(1) ⊂ LR(1) as grammars, while LALR(1) and
  LR(1) accept the same languages (Q17, Q19); and the dangling-else conflict is shift/reduce, resolved by shifting
  (Q14).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,D), (A,B), (A,B,D), (A,B,C) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **100 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the 50
  Unit 1 questions and the 50 Unit 2 questions — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Unit 3 questions do not appear there (verified: `CD-U3` occurs nowhere in the
  bank tab). Units 4–5 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the nine payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta
  strip, `#qhost`, palette, bank tab, About tab, payload), the remaining **25 940 bytes are byte-identical** to the
  shell extracted from the Compiler Design Unit 2 Set 2 paper, so the `<style>` block, the exam `<script>`, the
  palette markup, the answer-key view and the footer are unchanged. The `:root` block is byte-identical across the
  new paper, `index.html` and `design-tokens.css`, and no new literal hex value was introduced, so the known
  Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**34 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `ans`, `amr` and `na` through mark, unmark and Clear response; all four tabs open and
  the key tab stays locked until submit; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25
  `ok` palette buttons and 25 key cards; one wrong MCQ, an MSQ one option short, a wrong NAT and one skipped MCQ
  score **28 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that an MSQ earns nothing unless the exact
  set is selected and that there is no negative marking; an empty paper scores **0 / 35** with 25 `skip` buttons;
  every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`, with lowercase difficulty values; and all four subtopics appear.
- `index.html` holds all **1400** questions. Its data block was updated in place: the new test record was inserted at
  the head of `tests`, the 25 new question records were appended, and the static header strings were recomputed from
  the data block and now read 65 units, 35 sets published, 1400 solved questions / records and 281 subtopics. No unit
  had to be registered — Compiler Design Units 1–5 were already in the portal's `units` table. Every path in the data
  block resolves against the repository tree.

- **2026-10-27, Programming and Data Structures → Unit 2 (Pointers, Memory & Preprocessors), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw,
  giving **Programming and Data Structures**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-27, run 3, unit 2, pointers-memory, Set 1 of 2}`. Unit 2 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **0** days, below `DAYS_PER_UNIT_MAX = 7`, so the cap test in
  step B3 held and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 2 now
  holds exactly 50 questions — the cap — and the next Programming and Data Structures run advances
  `(index_of(pointers-memory) + 1) mod 7 = (1 + 1) mod 7 = 2` → **Unit 3, Linear Data Structures**. The Set 1 paper
  was moved to `programming-data-structures/pointers-memory/archive/gate_ds_mock_2_2026-10-27_run1.html` with its
  content frozen, and the Set 2 paper took the canonical filename, so the unit folder holds exactly one current paper
  and no root copy was written. No override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 2 subtopics — pointer arithmetic (7), pointers to functions (6), dynamic memory
  allocation (6) and macro expansion, scope and lifetime (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="programming-data-structures"`, `data-unit="pointers-memory"`, `data-unit-number="2"` and its
  subtopic slug.
- All 25 items are new: `DS-U2B-Q01`..`DS-U2B-Q25` did not exist in the bank, and every stem and every option set was
  compared against the 75 banked Programming and Data Structures items (Unit 1 and Unit 2 Set 1) with a
  string-normalised check over the whole card (tags stripped, case and punctuation removed): zero collisions, and no
  id overlap. The five stems that read "What does this program print?" are distinguished by their code blocks, which
  is why the comparison is made over the full card text rather than the stem alone.
- **Every countable answer was recomputed independently, not by hand.** No C compiler exists in the build sandbox, so
  each fragment was simulated in Python against C semantics rather than compiled: the pointer trace
  `*p, p[-1]` from `a + 2` gives `6 4` (Q02); `(char *)(a + 1) - (char *)a` on `int a[4][3]` gives **12** (Q03);
  `(*q)[1] += 10` through `int **` writes `a[2]` and leaves `a[1]` alone, giving `8 19` (Q04); `sizeof(b)` for
  `int *b[3]` is **24** and `sizeof(*c)` for `int (*c)[4]` is **16** (Q06); the converging-pointer loop makes **2**
  increments on `{3, 1, 4, 1, 5, 9, 2}` with the trace `(3,2) false, (1,9) true, (4,5) true` (Q07); the function
  pointer chain `inc` then `dbl` from 3 accumulates **12** (Q09); `apply(p, 2 + 3, 4)` through `mul` is **20** (Q10);
  the nested dispatch `a(b(2, 3), 4)` is `add(mul(2,3),4)` = **10** (Q12); the pointer swap gives `6 4` (Q13);
  `calloc(12, sizeof(struct pt))` requests **96** bytes (Q15); the two-level allocation makes **4** calls totalling
  **72** bytes (Q19); `3 * DOUBLE(4)` with `#define DOUBLE(x) (x) + (x)` is `12 + 4` = **16** (Q20); and
  `B * 2` with `#define B A + 2`, `A = 3` is `3 + 2 * 2` = **7** (Q23). **25 of 25 answers reproduced; 0
  disagreements.**
- The conceptual items were settled against the standard rather than by taste: `&a` for `int a[10]` has type
  `int (*)[10]` because the operand of unary `&` does not decay (Q01); `r[0] + 5` on a row of 5 ints is a
  one-past-the-end pointer whose dereference is undefined even though the byte is physically inside the next row
  (Q05); only `==` and `!=` are defined between function pointers, and function pointers are not guaranteed to survive
  a round trip through `void *` (Q11); a failed `realloc` leaves the original block allocated, while a successful
  moving `realloc` frees it, which is what makes the temporary-variable idiom necessary (Q16, Q17); `free` invalidates
  every pointer into the block, not only the one passed to it (Q18); and `#define SIZE 5` followed by
  `int SIZE = 3;` is a syntax error because a macro cannot be shadowed by a declaration (Q24).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4
  and (D) 3, and the five MSQ answer sets are (A,B,C), (A,B), (A,B,C), (A,C,D) and (A,B,C).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 0 for this subject, the Question Bank tab
  shows **75 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **75** banked items that are not part of the active set — the 50
  Unit 1 questions and the 25 Unit 2 Set 1 questions — under one accordion per unit and one heading per subtopic,
  every solution collapsed. The 25 active Set 2 questions do not appear there (verified: zero overlap between the 25
  active cards and the 75 bank-tab cards). Units 3–7 are reported on one line rather than as empty accordions.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions replaced by placeholders (title, header sub-line, tab label, meta set chip, `#qhost`,
  bank tab, About tab, payload), the remaining **28 414 bytes are byte-identical** to the shell extracted from the
  Programming and Data Structures Unit 2 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper,
  `index.html` and `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4
  deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**53 checks, all passing**, across five runs): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, key tab disabled and labelled locked,
  key pane empty, summary hidden, timer at 60:00, one card visible, every input enabled); the palette reaches `ans`,
  `amr` and back, falls back to `na` on Clear response, and the palette button opens its question; all four tabs open;
  all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette buttons and 25 key cards;
  one wrong MCQ, one skipped MCQ, an MSQ one option short and a wrong NAT score **29 / 35** with 21 correct, 3 wrong
  and 1 unattempted, confirming that an MSQ earns nothing unless the exact set is selected and that there is no
  negative marking; an empty paper scores **0 / 35** with 25 `skip` buttons; every card carries `data-subject`,
  `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`, with lowercase
  difficulty values; and all four subtopics appear.
- `index.html` holds all **1375** questions. Its data block was updated in place: the existing 2026-10-27 Programming
  and Data Structures Unit 2 record was retargeted at the new paper and given an `archives` entry pointing at the
  frozen Set 1 copy (so the card reads "Earlier sets for this date: Set 1"), and the 25 new question records were
  appended. No unit had to be registered — Programming and Data Structures Units 1–7 were already in the portal's
  `units` table. The static header strings were recomputed from the data block and now read 65 units, 34 sets
  published, 1375 solved questions / records and 281 subtopics. Every path in the data block resolves against the
  repository tree.

- **2026-10-27, Operating Systems → Unit 3 (Deadlocks), Set 1 of 2.** MODE A: one subject was drawn uniformly at
  random from all 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw, giving **Operating Systems**.
  `runs[-1]` for the subject is `{date 2026-10-26, run 4, unit 2, synchronization-ipc, Set 2 of 2}`. Unit 2 held
  **50** questions, exactly `UNIT_QUESTION_CAP = 50`, so step B3's cap test failed and step B4 advanced exactly one
  unit: `(index_of(synchronization-ipc) + 1) mod 6 = (1 + 1) mod 6 = 2` → **Unit 3, Deadlocks** (`deadlocks`). No
  override was used, no unit exceeded 50 questions, and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — four conditions & the resource-allocation graph (6), prevention,
  avoidance & the banker's algorithm (10), detection & recovery (5), starvation vs deadlock (4). Composition
  15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries
  `data-subject="operating-systems"`, `data-unit="deadlocks"`, `data-unit-number="3"` and its subtopic slug.
- All 25 items are new: `OS-U3-Q01`..`OS-U3-Q25` did not exist in the bank, and no stem or option set repeats a
  Unit 1 or Unit 2 item. Every numeric answer was recomputed in code before shipping: the safety test for the
  classic 5-process state (safe sequence P1, P3, P4, P0, P2 and no other among the four options), the four candidate
  grants of the hard MCQ (only P0's request for (1 2 2) destroys every safe sequence), the minimum addition of B in
  Q22 (3, with b = 2 unsafe), the maximum grantable k in the classic state (k = 2 safe, k = 3 unsafe), and the
  safe-sequence count of Q25 (4, obtained by exhaustive enumeration of all 3! orders; P2 can never open a sequence
  because it needs two units of B when one is free).
- The set contains no `GATE_PYQ_VARIATION` item: no deadlock previous-year question has been verified against an
  official paper and answer key for this run, so none is claimed. Every question is `STANDARD_TEXTBOOK` (15) or
  `ORIGINAL_SYNTHESIS` (10), and the About tab and the paper's Question Bank tab both say so.
- Filed only at `operating-systems/deadlocks/gate_os_mock_3_2026-10-27.html`. Unit 3 had no earlier paper, so nothing
  was archived, the unit folder holds exactly one current paper and nothing was written at the repository root. The
  portal card carries no "Earlier sets" line because no set has been superseded yet.
- Shell parity checked this run: the `<style>` block and the `<script>` block are byte-identical to the paper the
  shell was copied from, the `:root` block still matches `design-tokens.css` byte for byte, and the changed bytes
  outside the payload are confined to the title, header, meta strip, question host, palette, bank tab and About tab.
- Structural checks this run (no browser harness): 25 `.qcard` elements, 25 palette buttons, a payload that decodes
  to 25 answers and 25 solutions, zero solution HTML inside the active test cards, 100 `.hcard` items in the Question
  Bank tab, a tag-balance baseline no worse than the existing shell (the shell's own unclosed `</head>` remains, as
  in every other paper), and a marks total of 35 from the `Marks:` labels.
- The Question Bank tab inside the paper lists the 100 solved questions of Units 1 and 2 and nothing else, generated
  from `master_bank.json`. Unit 3's 25 are the active test and are not repeated in the tab, so the tab and the paper
  share no question. `index.html` now holds 1325 banked questions and 34 test cards.

- **2026-10-27, Algorithms → Unit 2 (Divide and Conquer & Sorting), Set 1 of 2.** MODE A: the subject was drawn with
  an unseeded draw among the subjects that had no paper dated 2026-10-27 — Algorithms and Databases, both last served
  on 2026-10-26 — and the draw gave **Algorithms**. `runs[-1]` for the subject is `{date 2026-10-26, run 1, unit 1,
  asymptotic-analysis, Set 2 of 2}`. Unit 1 held **50** questions, exactly `UNIT_QUESTION_CAP = 50`, so step B3's cap
  test failed and step B4 advanced exactly one unit: `(index_of(asymptotic-analysis) + 1) mod 7 = (0 + 1) mod 7 = 1`
  → **Unit 2, Divide and Conquer & Sorting** (`sorting-divide-conquer`). No override was used, no unit exceeded 50
  questions, and no second pass has started.
- Coverage this run: all four Unit 2 subtopics — merge sort & quicksort (7), counting & radix sort (6), selection &
  the k-th element (6) and inversion counting (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="algorithms"`,
  `data-unit="sorting-divide-conquer"`, `data-unit-number="2"` and its subtopic slug.
- All 25 items are new: `ALG-U2-Q01`..`ALG-U2-Q25` did not exist in the bank, and no stem or option set repeats a
  Unit 1 item. Every numeric answer was recomputed independently in code before shipping: the merge-sort worst case
  for n = 8 by exhaustive enumeration of all 40,320 input orders (17), the duplicate-key inversion count by direct
  pair counting ([3, 1, 2, 3, 1, 2] → 7), the expected inversion count n(n − 1)/4 against all 24 permutations for
  n = 4 (mean 3), and the comparison-count identities (⌈3n/2⌉ − 2 = 13 for n = 10, n + ⌈log₂n⌉ − 2 = 18 for
  n = 16, d(n + b) = 3 × 1,001,000 = 3,003,000 for the radix pass).
- The set contains no `GATE_PYQ_VARIATION` item: no sorting, selection or inversion-counting previous-year question
  has been verified against an official paper and answer key, so none is claimed; every question is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10) and the About tab says so.
- Filed only at `algorithms/sorting-divide-conquer/gate_algo_mock_2_2026-10-27.html`. Unit 2 had no earlier paper, so
  nothing was archived, the unit folder holds exactly one current paper and nothing was written at the repository
  root. The portal card carries no "Earlier sets" line because no set has been superseded yet.
- Shell parity checked this run: the `<style>` block and the `<script>` block are byte-identical to the paper the
  shell was copied from, the `:root` block still matches `design-tokens.css` byte for byte, and the changed lines
  outside the question payload are confined to the title, header, meta strip, bank tab and About tab.
- Structural checks this run (no browser harness): 25 `.qcard` elements, 25 palette buttons, a payload that decodes
  to 25 answers and 25 solutions, zero solution HTML inside the active test cards, 50 `.hcard` items in the Question
  Bank tab, zero stem overlap between the active test and that tab, and a tag-balance baseline identical to the
  existing shell.
- The Question Bank tab inside the paper lists the 50 solved questions of Unit 1 and nothing else: its 25 run-1 cards
  are carried over byte for byte from the previous Algorithms paper, and its 25 run-2 cards are generated from
  `master_bank.json` because no earlier tab had listed them. Unit 2's 25 are the active test and are not repeated in
  the tab, so the tab and the paper share no question. `index.html` now holds 1300 banked questions and 33 test cards.

- **2026-10-27, Digital Logic → Unit 3 (Sequential Circuits: Flip-Flops & Registers), Set 1 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (draw index 2 of 11); it gave **Digital Logic**. `runs[-1]` for the subject is `{date 2026-10-27, run 4, unit 2,
  combinational-circuits, Set 2 of 2}`. Unit 2 held **50** questions — exactly `UNIT_QUESTION_CAP = 50` — so the cap
  test in step B3 failed and step B4 advanced exactly one unit:
  `(index_of(combinational-circuits) + 1) mod 4 = (1 + 1) mod 4 = 2` → **Unit 3, Sequential Circuits: Flip-Flops &
  Registers** (`sequential-flipflops`). Unit 3 had no earlier paper, so nothing was archived; the paper is filed only
  at `digital-logic/sequential-flipflops/gate_dl_mock_3_2026-10-27.html`, the unit folder holds exactly one current
  paper and no root copy was written. This is Set 1 of 2: 25 questions are now banked on Unit 3, so the next Digital
  Logic run re-selects Unit 3 (25 < 50, 0 days) before advancing to Unit 4 of the same pass. No override was used, no
  unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — latches vs flip-flops (8), setup & hold times (6), characteristic
  equations (5) and shift registers (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium /
  5 hard; marks 15 × 1 + 10 × 2 = 35. Every question carries `data-subject="digital-logic"`,
  `data-unit="sequential-flipflops"`, `data-unit-number="3"` and its subtopic slug.
- All 25 items are new: `DL-U3-Q01`..`DL-U3-Q25` did not exist in the bank, and every stem and every option set was
  compared against the 100 banked Digital Logic items (Units 1 and 2) with a string-normalised check (tags stripped,
  case and punctuation removed): zero collisions, and no id overlap.
- **Every countable answer was recomputed by script, not by hand.** The shift traces were simulated bit by bit: the
  right shift of `0000` under the input sequence `1, 0, 1, 1` gives `1000, 0100, 1010, 1101` (Q04); the ring counter
  from `1000` after three clocks gives `0001` (Q17); `1011` shifted left twice with a 0 entering gives `1100` = 12
  (Q18); the 4-bit Johnson cycle was generated and has exactly **8** states — `0000, 1000, 1100, 1110, 1111, 0111,
  0011, 0001` — leaving 8 unused (Q05), while the 4-bit ring cycle has 4 states and leaves 12 (Q24). The timing items
  were computed from the two inequalities: `T = 2 + 6 + 2 = 10` ns giving **100 MHz** (Q12); a hold slack of
  `1 + 0.5 − 2 = −0.5` ns giving **0.5** ns of extra delay (Q13); and `T = 1.5 + 3.0 + 1.0 = 5.5` ns giving
  **181.82 MHz** with a hold slack of +0.7 ns (Q22). The characteristic-equation items were evaluated on both rows of
  the next-state function: `J = Q̄, K = Q` toggles (Q15), `J = Q, K = Q̄` holds (Q23), and `D = Q̄` toggles (Q16).
  **Every one of the 25 answers was reproduced by an independent computation; 0 disagreements.**
- The latch items were settled by solving the cross-coupled equations for both outputs simultaneously rather than by
  pattern-matching: the NOR latch at `S = 0, R = 1` is forced to `Q = 0, Q̄ = 1` from either previous state (Q01);
  the NAND latch is set by a low pulse on `S̄` and holds after release (Q02); `S = R = 1` on the NOR latch drives both
  outputs to 0, which is what makes it forbidden (Q10A); and releasing both NAND inputs from `S̄ = R̄ = 0` leaves two
  self-consistent solutions, so the outcome is a race, not a priority (Q21). The transparency item follows from the
  gated latch's definition — while the enable is high, `Q = D` continuously (Q09).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 5, (C) 3 and
  (D) 3, and the five MSQ answer sets are (A,C,D), (B,C,D), (A,B,C), (A,B,D) and (A,B,C).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged at 2 for Digital Logic (both Unit 1), the
  Question Bank tab shows **100 solved** and **2 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`.
  Every item is `STANDARD_TEXTBOOK` (9) or `ORIGINAL_SYNTHESIS` (16), so nothing on this paper claims
  previous-year status.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the 50
  Unit 1 questions and the 50 Unit 2 questions — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Unit 3 questions do not appear there (verified: zero overlap between the 25
  active stems and the 100 bank-tab stems). Unit 3 has no accordion of its own this run because all 25 of its banked
  questions are the active test.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions replaced by placeholders (title, header sub-line, candidate ID, bank tab label, meta
  strip, `#qhost`, bank tab, About tab, payload), the remaining **27 594 bytes are byte-identical** to the shell
  extracted from the Digital Logic Unit 2 Set 2 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper,
  `index.html` and `design-tokens.css`, and no new literal hex value was introduced, so the known Section 6.4
  deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**51 checks, all passing**, across four runs): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane,
  key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the palette reaches `na`, `ans`, `amr` and back through Unmark review and Clear response; the timer was
  observed ticking 60:00 → 59:59 under a real interval; all 25 answered correctly scores **35 / 35** with 25 correct,
  0 wrong, 25 `ok` palette buttons and 25 key cards; one wrong MCQ, two MSQs one option short and two wrong NATs score
  **26 / 35** with 20 correct, 5 wrong and 5 `bad` buttons, confirming that an MSQ earns nothing unless the exact set
  is selected and that there is no negative marking; an empty paper scores **0 / 35** with 25 `skip` buttons; every
  card carries all seven data attributes with lowercase difficulty values; all four subtopics appear; the Question
  Bank tab renders 100 cards with no active question repeated; the About tab carries its three sections; and all four
  tabs open.
- `index.html` holds all **1275** questions. Its data block was updated in place: the new test record was inserted at
  the head of `tests`, the 25 new question records were appended, and Digital Logic Unit 3 was registered in the
  portal's `units` table (it was the only Digital Logic unit missing). The static header strings were recomputed from
  the data block and now read 65 units, 32 sets published, 1275 solved questions / records and 281 subtopics. Every
  path in the data block resolves against the repository tree.

- **2026-10-27, Engineering Mathematics → Unit 3 (Calculus: Limits, Continuity & Differentiability), Set 2 of 2.**
  MODE A: one subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded
  `random.SystemRandom()` draw (seed `213900260`, draw index 1 of 11); it gave **Engineering Mathematics**. `runs[]`
  sorted by `(date, run)` gives the most recent paper as `{date 2026-10-27, run 5, unit 3, calculus-limits-derivatives,
  Set 1 of 2}`. Unit 3 held **25** questions, below `UNIT_QUESTION_CAP = 50`, and had been current for **0** days,
  below `DAYS_PER_UNIT_MAX = 7`, so the cap test in step B3 held and step B4 was not reached: the current unit was
  generated again. This is Set 2 of 2, so Unit 3 now holds exactly 50 questions — the cap — and the next Engineering
  Mathematics run advances `(index_of(calculus-limits-derivatives) + 1) mod 5 = (2 + 1) mod 5 = 3` → **Unit 4,
  Calculus: Maxima, Minima & Integrals**. The Set 1 paper was moved to
  `engineering-mathematics/calculus-limits-derivatives/archive/gate_em_mock_3_2026-10-27_run1.html` with its content
  frozen, and the Set 2 paper took the canonical filename, so the unit folder holds exactly one current paper and no
  root copy was written. No override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — indeterminate forms & L'Hôpital's rule (7), continuity analysis (6),
  mean value theorems (6), partial derivatives (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `EM-U3B-Q01`..`EM-U3B-Q25` did not exist in the bank, and every stem was checked against the
  125 banked Engineering Mathematics items (Unit 1, Unit 2 and Unit 3 Set 1) so that no stem, option set or numeric
  answer repeats. The check was string-normalised (tags stripped, case and punctuation removed): zero collisions.
- **Every countable answer was recomputed by script, not by hand.** The limits were evaluated symbolically rather than
  by inspection: `lim tan(3x)/(2x) = 3/2` (Q01), `lim sin 5x/sin 2x = 5/2` (Q02), `lim (√x − 3)/(x − 9) = 1/6` (Q03),
  `lim (x − sin x)/x³ = 1/6` (Q07), `lim (tan x − sin x)/x³ = 1/2` (Q11), `lim (1 − cos 4x)/x² = 8` (Q21) and
  `lim (sin 3x − 3 sin x)/x³ = −4` (Q24). The derivative quantities were differentiated symbolically:
  `f_y = 4xy` giving 8 at (1, 2) (Q05), `∇f(2,1) = (4, 6)` (Q06), `∂z/∂r = 2r` under the polar substitution (Q10),
  Euler's `x f_x + y f_y = 2f` giving 30 (Q15) and `∂⁴f/∂x²∂y∂z = 12xy` giving 24 at (1, 2, 1) (Q25). The
  one-sided derivatives that decide the corners of `|x − 2| + |x + 2|` were computed as 0 and 2 at `x = 2`, and
  −2 and 0 at `x = −2` (Q08). The critical points of `4xy − x⁴ − y⁴` were solved and classified: `(0, 0)` with
  `D = −16` is a saddle, `(1, 1)` and `(−1, −1)` with `D = 128` and `f_xx = −12` are local maxima (Q14). Rolle's
  point for `x² − 4x + 1` on `[1, 3]` is `c = 2` after confirming `f(1) = f(3) = −2` (Q04); the Lagrange points for
  `x³ − 3x² + 2x` on `[0, 3]` are the roots of `3c² − 6c = 0`, of which only `c = 2` is interior (Q23). The
  continuity parameter in Q22 was settled by two conditions at once — `a + b = 1` from continuity and `a = 2` from
  the matching slopes — giving `a + b = 1`. **Every one of the 25 answers was reproduced by an independent symbolic
  computation; 0 disagreements.**
- The conceptual items were settled against the standard rather than by taste: `x^(2/3)` satisfies two of Rolle's
  three hypotheses on `[−1, 1]` and fails only differentiability at the interior point 0, which is what Q09 asks for;
  `x² sin(1/x)` is differentiable at 0 with `f′(0) = 0` while `f′` oscillates without limit there, so a derivative
  need not be continuous (Q12); a derivative bounded by `1 ≤ f′ ≤ 2` gives a two-sided bound `3 ≤ f(3) ≤ 6`, both
  sides attained by `x` and `2x` (Q13); Lagrange's theorem asks for differentiability on the **open** interval only, so
  `√x` on `[0, 1]` qualifies despite its vertical tangent at the endpoint while `|x|` on `[−1, 1]` does not (Q20);
  the discriminant `D = f_xx f_yy − f_xy²` — not the sign of `f_yy` — is what separates a saddle from a maximum, and
  it does so at `(0, 0)` of `4xy − x⁴ − y⁴` where both pure second derivatives vanish (Q14); and a cancelled common
  factor removes a singularity rather than creating an asymptote (Q19).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 2 times, (B) 4, (C) 4
  and (D) 5, and the five MSQ answer sets are (A,C), (B,C), (A,B,C), (A,B) and (B,C,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged (empty for this subject), the Question Bank tab
  shows **125 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **125** banked items that are not part of the active set — 50 from
  Unit 1, 50 from Unit 2 and 25 from Unit 3 Set 1 — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Set 2 questions do not appear there (verified: zero overlap between the 25 active
  stems and the 125 bank-tab questions). Unit 3's accordion therefore carries only its Set 1 questions this run, because
  all 25 of its Set 2 questions are the active test.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions replaced by placeholders (title, header sub-line, tab label, meta set chip, `#qhost`, bank tab,
  About tab, payload), the remaining **28 423 bytes are byte-identical** to the shell extracted from the Engineering
  Mathematics Unit 3 Set 1 paper, so the `<style>` block (13 243 bytes), the exam `<script>` (9 428 bytes), the
  palette, the answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper,
  `index.html` and `design-tokens.css`, and the count of literal hex values outside `:root` is unchanged at 114 in the
  paper, so the known Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**59 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no `ansline` markup in the test pane, key tab
  disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible, every input
  enabled); the timer was observed ticking 60:00 → 59:59 under real intervals; the palette reaches `ans`, `amr`, `na`
  and `mrk` and falls back correctly on Unmark review and Clear response; all 25 answered correctly scores
  **35 / 35** with 25 correct, 0 wrong, 25 `ok` palette buttons and 25 key cards; one wrong MCQ, one skipped MCQ, an
  MSQ one option short and a wrong NAT score **29 / 35** with 21 correct, 3 wrong and 1 unattempted, confirming that
  an MSQ earns nothing unless the exact set is selected and that there is no negative marking; an empty paper scores
  **0 / 35** with 25 `skip` buttons; every card carries `data-subject`, `data-unit`, `data-unit-number`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`, with lowercase difficulty values; all four
  subtopics appear; the Question Bank tab renders 125 cards; the About tab carries its three sections; and all four
  tabs open.
- `index.html` holds all **1250** questions. Its data block was updated in place: the existing 2026-10-27 Engineering
  Mathematics Unit 3 record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1
  copy (so the card reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No unit
  had to be registered — Engineering Mathematics Units 1–5 were already in the portal's `units` table. The static
  header strings were recomputed from the data block and now read 64 units, 31 sets published, 1250 solved questions /
  records and 277 subtopics. Every path in the data block resolves against the repository tree.

- **2026-10-27, Engineering Mathematics → Unit 3 (Calculus: Limits, Continuity & Differentiability), Set 1 of 2.**
  MODE A: one subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded
  `random.SystemRandom()` draw (seed `1855517764`, draw index 1 of 11); it gave **Engineering Mathematics**. `runs[]`
  gives the most recent paper as `{date 2026-10-27, run 4, unit 2, eigenvalues-eigenvectors, Set 2 of 2}`. Unit 2 held
  **50** questions — exactly `UNIT_QUESTION_CAP = 50` — so the cap test in step B3 failed and step B4 advanced exactly
  one unit: `(index_of(eigenvalues-eigenvectors) + 1) mod 5 = (1 + 1) mod 5 = 2` → **Unit 3, Calculus: Limits,
  Continuity & Differentiability** (`calculus-limits-derivatives`). Unit 3 had no earlier paper, so nothing was
  archived; the paper is filed only at
  `engineering-mathematics/calculus-limits-derivatives/gate_em_mock_3_2026-10-27.html`, the unit folder holds exactly
  one current paper and no root copy was written. This is Set 1 of 2: 25 questions are now banked on Unit 3, so the
  next Engineering Mathematics run re-selects Unit 3 (25 < 50, 0 days) before advancing to Unit 4. No override was
  used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — indeterminate forms & L'Hôpital's rule (7), continuity analysis (6),
  mean value theorems (6), partial derivatives (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `EM-U3-Q01`..`EM-U3-Q25` did not exist in the bank, and every stem was checked against the
  100 banked Engineering Mathematics items (Unit 1 and Unit 2) so that no stem, option set or numeric answer repeats.
- **Every countable answer was recomputed by script, not by hand.** The verification script evaluates each limit with
  a symbolic algebra system rather than by inspection: `lim sin 3x/x = 3` (Q01), `lim (1 − cos x)/x² = 1/2` (Q02),
  `lim (eˣ − 1 − x)/x² = 1/2` (Q07), `lim (1/x² − 1/sin²x) = −1/3` (Q12), `lim (e²ˣ − 1)/x = 2` (Q21) and
  `lim x ln x = 0` (Q24). The mean-value points are solved, not guessed: `c = 1` for `x²` on `[0, 2]` (Q04), exactly
  **2** stationary points of `x³ − 3x` inside `(−√3, √3)` (Q09), `c = 14/9` for Cauchy's theorem on `x², x³` over
  `[1, 2]` (Q14), `c = 2` for `x² + 2x` on `[0, 4]` (Q23), and the two roots `1 ± √3/3 ≈ 0.423, 1.577` of
  `3x² − 6x + 2` both inside `(0, 2)` (Q20). The partial-derivative items were differentiated symbolically:
  `f_xy = 2x` (Q05), the tangent plane `z = 2x + 2y − 2` (Q06), `f_xx(1,1) = 6` (Q10), `dw/dt = 16` by both the
  chain rule and direct substitution (Q11), the critical points `(0, 0)` with `D = −9` and `(1, 1)` with `D = 27`
  (Q15), and `∂⁴f/∂x²∂y² = 12` at `(1, 1)` (Q25). The removable-discontinuity parameter `a = 15` (Q22) was confirmed
  by factoring the numerator as `3(x + 2)(x + 3)` and checking that the limit at `x = −2` is the finite value −1.
  **35 of 35 scripted checks passed.**
- The conceptual items were settled against the standard rather than by taste: continuity needs `a > 0` in
  `xᵃ sin(1/x)` while differentiability needs `a > 1`, and the boundary case `a = 1` is continuous but not
  differentiable (Q08, Q13); Rolle's theorem guarantees *at least* one stationary point, so counting them needs the
  derivative solved (Q09, Q20); Cauchy's theorem couples two functions through a ratio of derivatives at one point, so
  it is not the average of two Lagrange applications (Q14); the discriminant `D = f_xx f_yy − f_xy²` — not the sign of
  `f_yy` — is what separates a saddle from a minimum (Q15); a product form `0 · ∞` must be rewritten as a quotient
  before L'Hôpital's rule applies (Q24); and a discontinuity is removable exactly when a finite two-sided limit
  exists, which excludes both `1/x` and `|x|/x` (Q19).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 5 times, (B) 4, (C) 3
  and (D) 3, and the five MSQ answer sets are (A,B,C), (A,B,D), (A,B,D), (A,C) and (A,B).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged (empty for this subject), the Question Bank tab
  shows **100 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the 50
  Unit 1 questions and the 50 Unit 2 questions — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Unit 3 questions do not appear there (verified: zero overlap between the 25
  active stems and the 100 bank-tab stems). Unit 3 has no accordion of its own this run because all 25 of its banked
  questions are the active test.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eight payload regions replaced by placeholders (title, header sub-line, candidate ID, tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining bytes are **identical** to the shell extracted from the
  Engineering Mathematics Unit 2 Set 2 paper, so the `<style>` block, the exam `<script>`, the palette, the
  answer-key view and the footer are byte-for-byte unchanged. The `:root` block is byte-identical across the new
  paper, `index.html` and `design-tokens.css`. No new literal hex value was introduced — the count outside `:root`
  went from 115 to 114 — so the known Section 6.4 deviation below is untouched and was not partially fixed for one
  paper.
- The paper was exercised in a jsdom harness before shipping (**34 checks, all passing**, across three runs): nothing
  is revealed pre-submit (every active `.sol` empty, no option mark, no `ansline` markup, key tab disabled and
  labelled locked, key pane empty, summary hidden, timer at 60:00, one card visible); the palette reaches `ans`, `mrk`
  and `amr` and falls back correctly on Unmark review; all 25 answered correctly scores **35 / 35** with 25 correct,
  0 wrong, 25 `ok` palette buttons and 25 key cards; one wrong MCQ, an MSQ one option short and a wrong NAT score
  **30 / 35** with 22 correct and 3 wrong, confirming that an MSQ earns nothing unless the exact set is selected and
  that there is no negative marking; an empty paper scores **0 / 35** with 25 `skip` buttons; every card carries
  `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`;
  and all four subtopics appear.
- `index.html` holds all **1225** questions. Its data block was updated in place: the new test record was inserted at
  the head of `tests`, the 25 new question records were appended, and the static header strings were recomputed from
  the data block — 64 units, 31 sets published, 1225 solved questions and records, 277 subtopics. Engineering
  Mathematics Unit 3 was already registered in the portal's `units` table, so no unit had to be added. Every `href`
  on the portal and every path in the data block resolves against the repository tree.

- **2026-10-27, Engineering Mathematics → Unit 2 (Linear Algebra: Eigenvalues & Vectors), Set 2 of 2.** MODE A: a
  subject was drawn with a seeded `random` draw (seed `20261027-2`, the second draw of the day) restricted to the
  three subjects that still had no paper dated 2026-10-27 — Algorithms, Databases, Engineering Mathematics — so the
  day's second paper lands on a subject not already served today. It gave **Engineering Mathematics**. `runs[]`
  sorted by `(date, run)` gives the most recent paper as `{date 2026-10-26, run 3, unit 2, eigenvalues-eigenvectors,
  Set 1 of 2}`. Unit 2 held **25** questions (< `UNIT_QUESTION_CAP = 50`) and had been current for **1** day
  (< `DAYS_PER_UNIT_MAX = 7`), so step B3 re-selected it: no advance, no modulo. The paper is Set 2 of 2, filed only
  at `engineering-mathematics/eigenvalues-eigenvectors/gate_em_mock_2_2026-10-27.html`. The previous current paper
  for the unit was moved to `engineering-mathematics/eigenvalues-eigenvectors/archive/gate_em_mock_2_2026-10-26_run1.html`
  with its content frozen, so the unit folder holds exactly one current paper and no root copy was written. Unit 2 now
  stands at 50 questions, exactly the cap, so the next Engineering Mathematics run advances one unit to
  `(index_of(eigenvalues-eigenvectors) + 1) mod 5 = 2` → Unit 3, Calculus: Limits, Continuity & Differentiability.
  No override was used, no unit exceeded 50 questions and no second pass has started.

- **2026-10-27, Compiler Design → Unit 2 (Syntax Analysis: Top-Down Parsing), Set 1 of 2.** MODE A: one subject was
  drawn from the 11 GATE CSE subjects with a seeded `random` draw (seed `20261027`), restricted to the four subjects
  that had no paper dated 2026-10-27 — Algorithms, Compiler Design, Databases, Engineering Mathematics — so that the
  day's paper lands on a subject that has not already been served today. It gave **Compiler Design**. `runs[]` sorted
  by `(date, run)` gives the most recent paper as `{date 2026-10-26, run 2, unit 1, lexical-analysis, Set 2 of 2}`.
  Unit 1 held **50** questions — exactly `UNIT_QUESTION_CAP = 50` — so the cap test in step B3 failed and step B4
  advanced exactly one unit: `(index_of(lexical-analysis) + 1) mod 5 = (0 + 1) mod 5 = 1` → **Unit 2, Syntax
  Analysis: Top-Down Parsing** (`top-down-parsing`). Unit 2 had no earlier paper, so nothing was archived; the paper
  is filed only at `compiler-design/top-down-parsing/gate_cd_mock_2_2026-10-27.html`, the unit folder holds exactly
  one current paper and no root copy was written. This is Set 1 of 2: 25 questions are now banked on Unit 2, so the
  next Compiler Design run re-selects Unit 2 (25 < 50, 0 days) before advancing to Unit 3 of the same pass. No
  override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 2 subtopics — FIRST and FOLLOW sets (7 questions), LL(1) parsing tables (6),
  recursive-descent parsers (6) and left recursion & factoring (6). Every question carries
  `data-subject="compiler-design"`, `data-unit="top-down-parsing"`, `data-unit-number="2"` and its subtopic slug.
  No verified previous-year question exists for this unit in the bank, so no item is labelled an official GATE
  question and the About tab says so.
- **2026-10-27, Theory of Computation → Unit 4 (Turing Machines & Decidability), Set 1 of 2.** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw
  index 6 of 11); it gave **Theory of Computation**. `runs[]` sorted by `(date, run)` gives the most recent paper as
  `{date 2026-10-27, run 6, unit 3, pushdown-automata, Set 2 of 2}`. Unit 3 held **50** questions — exactly
  `UNIT_QUESTION_CAP = 50` — so the cap test in step B3 failed and step B4 advanced exactly one unit:
  `(index_of(pushdown-automata) + 1) mod 4 = (2 + 1) mod 4 = 3` → **Unit 4, Turing Machines & Decidability**
  (`turing-machines-decidability`). Unit 4 had no earlier paper, so nothing was archived; the paper is filed only at
  `theory-of-computation/turing-machines-decidability/gate_toc_mock_4_2026-10-27.html`, the unit folder holds exactly
  one current paper and no root copy was written. This is Set 1 of 2: 25 questions are now banked on Unit 4, so the
  next Theory of Computation run re-selects Unit 4 (25 < 50, 0 days) before advancing to Unit 1 of a second pass.
  No override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all five Unit 4 subtopics, five questions each — standard TM models & variants, recursive vs
  recursively enumerable, halting problem & undecidability, Rice's theorem & reductions, and the Chomsky hierarchy
  summary. Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `TOC-U4-Q01`..`TOC-U4-Q25` did not exist in the bank, and every stem was compared against
  the 150 banked items of Units 1–3 (string-normalised) so that no stem repeats. No earlier paper existed for
  Unit 4, so no file was archived and the unit folder holds exactly one current paper.
- **Every countable answer was recomputed by script, not by hand.** The transition table has `8 × 5 = 40` entries
  (Q02); the bounded-tape machine has `3 × 4 × 3⁴ = 972` configurations (Q05); the cross-off machine for `{0ⁿ1ⁿ}`
  makes **13** moves on `0011` (Q14), confirmed by simulating the transition table step by step and cross-checked
  against `2n² + 2n + 1`, which gives 5 and 25 for `n = 1` and `n = 3`; **2** of the five listed languages are
  recursive (Q09); **5** of the six properties are undecidable by Rice's theorem (Q20), the exception being the
  trivially true `L(M) ⊆ Σ*`; and **3** of the six listed languages are context-free (Q25).
- The conceptual items were settled against the standard rather than by taste: every TM variant is simulated by the
  standard machine, so the class of accepted languages never grows (Q01, Q03, Q04); a fixed 1000-cell tape is finite
  memory and therefore accepts only regular languages, unlike an LBA whose bound grows with `n` (Q04); "both r.e."
  is exactly "recursive", by dovetailing the two recognisers (Q06, Q08, Q10); the r.e. languages are the one class
  in the question that is not closed under complement, the context-sensitive class being closed by
  Immerman–Szelepcsényi (Q07); a reduction from `HALT` runs from the known-hard problem *to* the new one, so the
  opposite arrow proves only r.e.-ness (Q12, Q15); Rice's theorem needs a semantic **and** non-trivial property, so
  "has three states" and "uses at most 50 cells" are outside it (Q16, Q17, Q18); and the answer to Q14 was worded
  so that the count is unambiguous — every application of `δ` counts, including the final one that halts.
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4
  and (D) 3, and the five MSQ answer sets are (A,B,D), (A,B,C), (A,B,D), (A,B,C) and (A,B,C).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged (empty for this subject), the Question Bank tab
  shows **150 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **150** banked items that are not part of the active set — 50 from
  Unit 1, 50 from Unit 2 and 50 from Unit 3 — under one expander per unit and one heading per subtopic, every
  solution collapsed. The 25 active questions do not appear there (verified: zero overlap between the 25 active
  stems and the 150 banked stems).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the payload regions replaced by placeholders (title, header sub-line, candidate ID, tab label, meta strip,
  `#qhost`, bank tab, About tab, payload), the remaining bytes are **identical** to the shell extracted from the
  Theory of Computation Unit 3 Set 2 paper; the `<style>` block (13 243 bytes) and the exam `<script>` (9 428 bytes)
  are byte-for-byte identical. The `:root` block is byte-identical across the new paper, `index.html` and
  `design-tokens.css`, and the count of literal hex values outside `:root` is unchanged at 697 in the paper and 704
  in the portal, so the known Section 6.4 deviation below is untouched and was not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**510 checks, all passing**, plus a second DOM run
  against a deliberately mixed submission): nothing is revealed pre-submit (every active `.sol` empty and hidden,
  every option mark empty, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one
  card visible, every input enabled); the palette reaches `ans`, `na`, `mrk` and `amr` and falls back correctly on
  Clear response and on Unmark review; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong, 25 `ok`
  palette buttons and 25 key cards; one wrong MCQ, an MSQ one option short and a wrong NAT score **30 / 35** with 22
  correct, 3 wrong and 3 `bad` buttons, confirming that an MSQ earns nothing unless the exact set is selected and
  that there is no negative marking; every card carries `data-subject`, `data-unit`, `data-unit-number`,
  `data-subtopic`, `data-type`, `data-difficulty` and `data-source`; all five subtopics appear; the Question Bank tab
  renders 150 cards with no active question repeated; and the About tab carries its three sections.
- `index.html` holds all 1150 questions. Its data block was updated in place: the new test record was
  inserted at the head of `tests`, the 25 new question records were appended, and the static header strings were
  recomputed from the data block — 64 units, 29 sets published, 1150
  solved questions and records, 277 subtopics. Theory of Computation Unit 4 was already registered in
  the portal's `units` table, so no unit had to be added. Every `href` on the portal and every path in the data block
  resolves against the repository tree.

- **2026-10-27, Operating Systems → Unit 2 (Inter-Process Communication & Synchronization), Set 2 of 2.** MODE A:
  one subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()`
  draw (draw index 8 of 11); it gave **Operating Systems**. `runs[]` gives the most recent paper as
  `{date 2026-10-26, run 3, unit 2, synchronization-ipc, Set 1 of 2}`. Unit 2 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **1** day, below `DAYS_PER_UNIT_MAX = 7`, so the cap test in
  step B3 held and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 2 now
  holds exactly 50 questions and the next Operating Systems run advances
  `(index_of(synchronization-ipc) + 1) mod 6 = (1 + 1) mod 6 = 2` → **Unit 3, Deadlocks**. No override was used, no
  unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 2 subtopics — critical section & Peterson's solution (7), hardware primitives:
  test-and-set & swap (6), binary & counting semaphores (6), producer–consumer, dining philosophers &
  readers–writers (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks
  15 × 1 + 10 × 2 = 35.
- All 25 items are new: `OS-U2B-Q01`..`OS-U2B-Q25` did not exist in the bank, and every stem was checked against the
  75 banked Operating Systems items (Unit 1 and Unit 2 Set 1) so that no stem, option set or numeric answer repeats.
  The Set 1 paper was moved to
  `operating-systems/synchronization-ipc/archive/gate_os_mock_2_2026-10-26_run1.html` with its content frozen, and
  the Set 2 paper took the canonical filename, so the unit folder holds exactly one current paper and no root copy
  was written.
- **Every countable answer was recomputed by hand and re-checked by script.** Semaphore arithmetic: a value of 0
  under `P` goes to −1 with one waiter (Q14); a value of −2 under `V` goes to −1 and wakes exactly one waiter (Q15);
  the magnitude of −2 is two blocked processes (Q16); a binary mutex at 1 taken by A and then requested by B and C
  reads −2 with two waiters, whose answer is option (D) (Q17). Concurrency counts: 8 contenders leave 7 spinning
  (Q13); Peterson's `n − 1` levels for `n = 6` is 5 (Q7); a buffer of capacity 8 with `full = 3` has `empty = 5`
  (Q24); five forks admit at most ⌊5/2⌋ = 2 simultaneous eaters (Q25). The Peterson trace of Q3 was walked step by
  step: after `P0: flag[0] = true; turn = 1` and `P1: flag[1] = true; turn = 0`, P0 finds `turn != 1` and enters
  while P1 spins on `flag[0] && turn == 0`.
- The conceptual items were settled against the standard rather than by taste: progress and bounded waiting are
  independent obligations, so progress never implies bounded waiting (Q4, Q5); strict alternation violates progress
  rather than mutual exclusion (Q5); Peterson's proof assumes sequential consistency, so a store buffer can let both
  processes in without fences (Q6); interrupt masking is atomic on a uniprocessor but not on a multiprocessor
  because the mask is per processor (Q19); a ticket lock built from `fetch-and-add` is the construction that adds
  bounded waiting to an atomic primitive (Q10); a release store can be reordered with the critical-section writes,
  which is the multicore spin-lock bug (Q12); the four-at-a-time dining-philosophers bound works because it removes
  circular wait, not because contention disappears (Q22); and the two readers–writers solutions starve writers and
  readers respectively (Q21).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 3
  and (D) 4, and the five MSQ answer sets are (A,B,C), (B,C,D), (A,B,D), (A,B,C) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` is unchanged for this subject, the Question Bank tab shows
  **75 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **75** banked items that are not part of the active set — the 50
  Unit 1 questions and the 25 Unit 2 Set 1 questions — under one accordion per unit and one heading per subtopic,
  every solution collapsed. The 25 active Set 2 questions do not appear there (zero overlap between the 25 active
  stems and the 75 banked stems).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block (13 228 bytes) and the exam `<script>` (9 411 bytes) are byte-for-byte identical to the Operating
  Systems Unit 2 Set 1 paper, and the `:root` block is byte-identical to `design-tokens.css` and `index.html`. No new
  literal hex value was introduced, so the known Section 6.4 deviation below is unchanged and was not partially fixed
  for one paper.
- The paper was exercised in a jsdom harness before shipping (19 checks, all passing, plus a second run against a
  deliberately mixed submission): nothing is revealed pre-submit (every active `.sol` empty, key tab disabled and
  labelled locked, one card visible, timer at 60:00); all 25 answered correctly scores **35 / 35** with 25 correct;
  one wrong MCQ, an MSQ one option short and a wrong NAT score **30 / 35** with 22 correct, 3 wrong and 0
  unattempted, confirming that an MSQ earns nothing unless the exact set is selected and that there is no negative
  marking; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`; all four subtopics appear; the Question Bank tab renders 75 cards with no
  active question repeated; and the About tab carries its three sections.
- `index.html` holds all **1125** questions. Its data block was updated in place: the Operating Systems Unit 2 record
  was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1 copy (so the card reads
  "Earlier sets for this date: Set 1"), and the 25 new question records were appended. The static header strings were
  recomputed and now read 64 units, 29 sets published and 1125 solved questions / records. Every `href` on the portal
  and every path in the data block resolves against the repository tree.

- **2026-10-27, Theory of Computation → Unit 3 (Pushdown Automata), Set 2 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 6 of
  11); it gave **Theory of Computation**. The bank's `runs[]` was read in append order — the last appended entry is
  the most recent paper, because several subjects store their runs out of chronological order — giving
  `{date 2026-10-27, run 5, unit 3, pushdown-automata, Set 1 of 2}`. Unit 3 held **25** questions, below
  `UNIT_QUESTION_CAP = 50`, and had been current for **0** days, below `DAYS_PER_UNIT_MAX = 7`, so the cap test in
  step B3 held and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 3 now
  holds exactly 50 questions and the next Theory of Computation run advances
  `(index_of(pushdown-automata) + 1) mod 4 = (2 + 1) mod 4 = 3` → **Unit 4, Turing Machines & Decidability**. No
  override was used, no unit exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — deterministic PDA (7), nondeterministic PDA (6), acceptance by empty
  store versus final state (6), equivalence with CFG (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `TOC-U3B-Q01`..`TOC-U3B-Q25` did not exist in the bank, and every stem was checked against the
  125 banked items (Units 1, 2 and 3 Set 1) so that no stem, option set or numeric answer repeats. Two MSQ stems
  collided on generic wording in the first draft ("Select every statement about the two acceptance modes …" was
  byte-identical to a Set 1 stem); both were reworded before the paper was written. The Set 1 paper was moved to
  `theory-of-computation/pushdown-automata/archive/gate_toc_mock_3_2026-10-27_run1.html` with its content frozen, and
  the Set 2 paper took the canonical filename, so the unit folder holds exactly one current paper and no root copy
  was written.
- **Every countable answer was recomputed by script, not by hand.** '18' transitions for 3 states × (2 input symbols
  + ε) × 2 stack symbols (Q03); '16' configurations at stack height 3 as 2 × 2³ (Q09); '48' variables as |Q|²|Γ| =
  4² × 3 (Q23); '2' for the Catalan count C₂ on `aaa` under `S → SS | a` (Q24). The NPDA of Q13 was executed as a
  search over (state, remaining input, stack) and returns exactly **3** accepting computations on `aabb` — switch on
  the first `b`, switch on the second `b`, and stay in `q₀` using the final ε-move. A first draft of that machine
  carried `δ(q₁, ε, Z₀) = {(q₁, Z₀)}`, which makes the number of accepting move sequences unbounded through an ε-loop;
  the loop was removed and the machine re-run, which is what fixes the answer at 3. The two classification counts
  (Q07 = 3 deterministic, and the Q02/Q04/Q06/Q12 language facts) were settled against the standard results rather
  than by taste: `{aⁿbⁿ} ∪ {aⁿbⁿc}` **is** a DCFL because the `c` is visible, which is why the closure-failure
  counterexample `{aⁿbⁿ} ∪ {aⁿb²ⁿ}` is used only as the contrast; palindromes are context-free but not deterministic
  context-free, while `{w c wᴿ}` is; and `{a, ab}` is a DCFL that no DPDA accepts by empty stack.
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B), (A,D), (A,B,D), (A,B) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` stays empty for Theory of Computation, the Question Bank tab
  shows **125 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **125** banked items that are not part of the active set — 50 from
  Unit 1, 50 from Unit 2 and 25 from Unit 3 Set 1 — under one accordion per unit and one heading per subtopic, every
  solution collapsed. The 25 active Set 2 questions do not appear there (verified: zero overlap between the 25 active
  stems and the 125 banked stems).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. With
  the eleven payload regions replaced by placeholders, the remaining bytes are **identical** to the shell extracted
  from the Theory of Computation Unit 3 Set 1 paper, so the `<style>` block, the exam `<script>`, the palette legend,
  the answer-key view and the footer are unchanged. The `:root` block is byte-identical across the new paper,
  `index.html` and `design-tokens.css`, and the count of literal hex values outside `:root` is unchanged at 697 in
  the paper and 704 in the portal, so the known Section 6.4 deviation below is untouched and was not partially fixed
  for one paper.
- The paper was exercised in a jsdom harness before shipping (**232 checks, all passing**, plus a second run of the
  same 232 against a deliberately mixed submission): nothing is revealed pre-submit (every active `.sol` empty and
  hidden, no option mark, no mark text, no "Answer:" string in the test pane, key tab disabled and labelled locked,
  key pane empty, summary hidden, timer at 60:00, one card visible); the palette reaches `na`, `ans`, `mrk` and `amr`
  and falls back correctly on Clear response; all 25 answered correctly scores **35 / 35** with 25 correct and 25 `ok`
  palette buttons; one wrong MCQ, an MSQ one option short and a wrong NAT score **30 / 35** with 22 correct, 3 wrong
  and 3 `bad` buttons, confirming that an MSQ earns nothing unless the exact set is selected and that there is no
  negative marking; every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`; all four subtopics appear; the Question Bank tab renders 125 cards with no
  active question repeated; and all four tabs open.
- One content defect was repaired in passing. The shipped Unit 3 Set 1 paper's About tab was truncated mid-sentence
  — its concept-map list stops at "…with the DPDA as a proper subclass; the " and the footer follows immediately, so
  the second and third About sections were missing and the `</ul></div>` never closed. This paper carries the full
  three-section About tab. The repair is content-level only and does not touch the shell; the other papers that share
  the truncation still need the same pass as the open token deviation.
- `index.html` holds all **1100** questions. Its data block was updated in place: the existing 2026-10-27 Theory of
  Computation Unit 3 record was retargeted at the new paper and given an `archives` entry pointing at the frozen Set 1
  copy (so the card reads "Earlier sets for this date: Set 1"), and the 25 new question records were appended. No
  unit had to be registered — Theory of Computation Units 1–4 were already in the portal's `units` table. The static
  header strings were recomputed from the data block and now read 64 units, 28 sets published and 1100 solved
  questions / records. Every `href` on the portal and every path in the data block resolves against the repository
  tree.

- **2026-10-27, Computer Networks → Unit 2 (Data Link Protocols & MAC), Set 1 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 10 of
  11); it gave **Computer Networks**. `runs[]` was sorted by `(date, run)` before reading: the most recent paper was
  `{date 2026-10-27, run 2, unit 1, network-fundamentals-framing}`. Unit 1 held **50** questions — exactly
  `UNIT_QUESTION_CAP = 50` — so the cap test in step B3 failed and step B4 advanced exactly one unit:
  `(index_of(network-fundamentals-framing) + 1) mod 6 = (0 + 1) mod 6 = 1` → **Unit 2, Data Link Protocols & MAC**
  (`data-link-mac`). Unit 2 had no earlier paper, so nothing was archived and the unit folder holds exactly one
  current paper. This is Set 1 of 2; 25 questions are now banked on Unit 2, so the next Computer Networks run
  re-selects Unit 2 (25 < 50, 0 days) before advancing to Unit 3. No override was used, no unit exceeded 50 questions
  and no second pass has started.
- Coverage this run: all five Unit 2 subtopics, five questions each — stop-and-wait ARQ, Go-Back-N & selective
  repeat, pure & slotted ALOHA, CSMA/CD & CSMA/CA & backoff, and Ethernet, switches & bridges. Composition 15 MCQ /
  5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `CN-DL2-Q01`..`CN-DL2-Q25` did not exist in the bank, and every stem was checked against the
  50 banked Unit 1 questions so that no stem, option set or numeric answer repeats. The paper is filed only at
  `computer-networks/data-link-mac/gate_cn_mock_2_2026-10-27.html`, and no root copy was written.
- **Every countable answer was recomputed by script, not by hand.** Stop-and-wait utilisation `1/41 = 2.44%` (Q01)
  and `1/5 = 20%` (Q05); slotted-ALOHA success probability `0.9⁹ = 0.387` for 10 stations at p = 0.1 (Q12); pure-ALOHA
  vulnerable period `2 × 1000/10⁶ s = 2 ms` (Q14); minimum CSMA/CD frame at 100 Mbps over 1 km at 2 × 10⁸ m/s,
  `100 Mbps × 2 × 5 μs = 1000 bits = 125 bytes` (Q17); the 10 Mbps slot-time frame `10⁷ × 51.2 μs = 512 bits` (Q20).
  The window bounds were checked against the protocol definitions rather than quoted: Go-Back-N `2ᵐ − 1 = 7` for
  m = 3 (Q06), selective repeat `2ᵐ⁻¹ = 8` for m = 4 (Q10), and both ALOHA peaks, `1/(2e) = 0.184` (Q11) and
  `1/e = 0.368`, were evaluated numerically.
- No `GATE_PYQ_VARIATION` item: `verified_pyqs` is empty for Computer Networks, so nothing in this paper is claimed
  as an official GATE question, and the About tab and Question Bank tab both say so.

- **2026-10-27, Discrete Mathematics → Unit 6 (Mathematical Induction & Recursion), Set 1 of 2.** MODE A: one subject
  was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index
  6 of 11); it gave **Discrete Mathematics**. The bank's `runs[]` was sorted by `(date, run)` before reading, because
  the Discrete Mathematics entries are not stored in chronological order; the most recent paper was
  `{date 2026-10-26, run 2, unit 5, functions}`. Unit 5 held **50** questions — exactly `UNIT_QUESTION_CAP = 50` — and
  had been current since 2026-10-26, so the cap test in step B3 failed and step B4 advanced exactly one unit:
  `(index_of(functions) + 1) mod 16 = (4 + 1) mod 16 = 5` → **Unit 6, Mathematical Induction & Recursion**
  (`induction-recursion`). This is Set 1 of 2; 25 questions are now banked on Unit 6, so the next Discrete Mathematics
  run re-selects Unit 6 (25 < 50, 0 days) before advancing to Unit 7. No override was used, no unit exceeded 50
  questions and no second pass has started.
- Coverage this run: all four Unit 6 subtopics — weak & strong induction (7), structural induction (6), well-ordering
  principle (6), proof techniques & errors (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium /
  5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `DM-IR6-Q01`..`DM-IR6-Q25` did not exist in the bank, and every stem was checked against the
  325 banked Discrete Mathematics questions (Units 1–5 and 16) so that no stem, option set or numeric answer repeats.
  Unit 6 had no earlier paper, so nothing was archived; the paper is filed only at
  `discrete-mathematics/induction-recursion/gate_dm_mock_6_2026-10-27.html`, the unit folder holds exactly one current
  paper, and no root copy was written.
- **Every countable answer was recomputed by script, not by hand.** `∑_{i=1}^{10} i³ = 55² = 3025` (Q03); a full binary
  tree with 20 internal nodes has `2·20 + 1 = 41` nodes (Q09); the smallest set containing 1 and closed under doubling
  and tripling holds exactly **10** values below 20 — 1, 2, 3, 4, 6, 8, 9, 12, 16, 18 (Q12); the largest amount not
  representable as `4a + 5b` is **11**, confirmed by checking every value up to 60 (Q15); the least `n` with
  `n! > 2ⁿ` is **4** (Q19). The two string-set questions were settled by generating the sets rather than by inspection:
  the set `S` with rules `w ↦ awb, bwa` contains `ab, ba, aabb, abab, baba, bbaa` and **not** `abba` (Q10), and the set
  with rules `w ↦ 0w1, 1w0` contains exactly `0011, 0101, 1010, 1100` at length 4 and **not** `0110` (Q13), which also
  confirms the characterisation `w = reverse(complement(w))` used in the solution. The closed forms in Q01
  (`∑ i·2ⁱ = (n−1)2ⁿ⁺¹ + 2`) and Q07 (`∑ k·k! = (n+1)! − 1`) were each checked against the true sum for n = 1..5, and
  the three distractor formulas in Q01 were checked to fail at n = 2 so that exactly one option survives.
- The conceptual items were settled by the standard rather than by taste: weak and strong induction prove the same
  theorems, and the equivalence is exhibited by applying ordinary induction to the running conjunction
  `Q(n) = P(0) ∧ … ∧ P(n)` (Q04, Q05); structural induction on prefix-generated strings is ordinary induction on length,
  because each rule raises the length by exactly one (Q11); the well-ordering principle fails for `ℤ`, for `{1/n}` and
  for `(0, 1]`, which is what Q14 and Q16 turn on; the remainder bound `r < b` in the division algorithm is forced by
  minimality and not by the definition of `S` (Q18); “all horses are the same colour” fails at `n = 1` because the two
  groups of one horse do not overlap (Q22); and `¬¬P` yields `P` only classically, which is why option (C) of Q25 is
  marked false.
- No GATE PYQ is claimed for Unit 6. No induction question has been verified against an official GATE paper and
  answer key, so the About tab and the Question Bank tab say so plainly and every item carries
  `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`. The six verified PYQs recorded in the series are unchanged.
- Verification run before this push: shell parity is byte-identical to the Discrete Mathematics Unit 5 shell outside
  the seven payload regions (title, header sub-line, tab counts, meta strip, `#qhost`, palette, bank tab, About tab,
  payload); `find . -name "*.html"` shows `index.html` plus one file per paper and nothing at the repository root;
  every `href` in `index.html` and in the paper's archive list resolves; the `:root` block is byte-identical to
  `design-tokens.css`; the paper renders 25 test cards, a 25-button palette and 325 bank cards (350 banked minus the 25
  in this test, so no question appears twice); and the dashboard counts match `master_bank.json` (1050 questions,
  42 papers).

- **2026-10-27, Theory of Computation → Unit 3 (Pushdown Automata), Set 1 of 2.** MODE A: one subject was drawn
  uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw (draw index 6 of
  11); it gave **Theory of Computation**. The bank's `runs[]` was sorted by `(date, run)` before reading, because the
  Theory of Computation entries are not stored in chronological order; the most recent paper was
  `{date 2026-10-27, run 4, unit 2, unit_slug cfl-grammars}`. Unit 2 held **50** questions — exactly
  `UNIT_QUESTION_CAP = 50` — and had been current since 2026-10-26, so the cap test in step B3 failed and step B4
  advanced exactly one unit: `(index_of(cfl-grammars) + 1) mod 4 = (1 + 1) mod 4 = 2` → **Unit 3, Pushdown Automata**
  (`pushdown-automata`). This is Set 1 of 2; 25 questions are now banked on Unit 3, so the next Theory of Computation
  run re-selects Unit 3 (25 < 50, 0 days) before advancing to Unit 4. No override was used, no unit exceeded 50
  questions and no second pass has started.
- Coverage this run: all four Unit 3 subtopics — deterministic PDA (7), nondeterministic PDA (6), acceptance by
  empty store vs final state (6), equivalence with CFG (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: `TOC-U3-Q01`..`TOC-U3-Q25` did not exist in the bank, and every stem, option set and numeric
  answer was checked against the 100 banked Unit 1 and Unit 2 questions. Unit 3 had no earlier paper, so nothing was
  archived; the paper is filed only at
  `theory-of-computation/pushdown-automata/gate_toc_mock_3_2026-10-27.html`, the unit folder holds exactly one current
  paper, and no root copy was written.
- **Every countable answer was recomputed by script, not by hand.** The NPDA of Q9 was executed as a computation tree
  over lists of stack symbols and gives exactly **2** accepting computations on `aabb` (the second `b` branches to
  `q0`-then-ε or straight to `q1`; the branch that reaches `q1` with an `A` still on top dies); the DPDA of Q7 was
  traced deterministically — `ab`, `aabb`, `aaabbb` accepted, `aab` ending in `q1` with `AZ₀` still on the stack
  (non-final, which is what makes option D of Q7 true), `abb` and `aabbb` rejected with input left over; the
  two-phase NPDA of Q10 was run on ten strings to confirm the language is `{aⁿbⁿ : n ≥ 1}` and not `{aⁿbⁿ : n ≥ 0}`
  (`ε` never reaches `q1`, where the only ε-move lives); Q15 is `2 × (2 + 2²) = 12` configurations; the top-down
  NPDA of Q21 peaks at **4** symbols on `aabb` and the one of Q24 at **5**, both computed by enumerating every
  derivation and taking the maximum **along the accepting derivation only** — a first draft took the maximum over
  all branches, which gives 6 for Q24 because the dead `S → aSb → aSb → aSb` branch pushes one symbol too many, and
  the question was reworded to say "during the computation that accepts" so the answer is unambiguous; Q23 is
  `|P| + |T| = 5 + 2 = 7`.
- The conceptual items were settled by the standard rather than by taste: determinism is one successor per
  `(q, a, X)` plus the rule that an ε-move and an input move may never coexist on the same `(q, X)`; DCFLs are
  closed under complement, under intersection with a regular language and under union with a regular language, but
  not under union in general — the witness `{aⁿbⁿ} ∪ {aⁿb²ⁿ}` was confirmed against the standard references before
  being used as Q6; `{aⁿbᵐ : n ≠ m}` is a DCFL because it is the complement of `{aⁿbⁿ}` inside the regular set
  `a*b*`; `{aⁱbʲcᵏ : i = j or j = k}` is context-free but not deterministic, which is what Q13 turns on; converting
  a DPDA from final-state to empty-stack acceptance fails exactly when the machine accepts with input still
  unread, and empty-stack acceptance forces the prefix property (Q17, Q18, Q19); in the triple construction
  `[q, A, p]` generates the strings read while popping `A` without looking below it (Q22).
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4,
  (C) 4 and (D) 3, and the five MSQ answer sets are (A,C,D), (A,B,D), (A,B,C), (A,C,D) and (A,B,D).
- No verified PYQ exists for this unit: `verified_pyqs` stays empty for this subject, the Question Bank tab shows
  **125 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (15) or `ORIGINAL_SYNTHESIS` (10), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **100** banked items that are not part of the active set — the
  50 Unit 1 questions and the 50 Unit 2 questions — under one accordion per unit and one heading per subtopic,
  every solution collapsed. The 25 active Unit 3 questions do not appear there (verified: zero overlap between the
  25 active stems and the 100 banked stems).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block (13 235 bytes) and the exam `<script>` (9 419 bytes) are byte-for-byte identical to the Theory of
  Computation Unit 2 Set 2 paper, and the `:root` block matches `design-tokens.css` and `index.html` exactly. The
  palette, the answer-key view, the footer and the head-before-`<style>` region are also byte-identical after
  normalising the title, the header sub-line, the candidate ID, the tab label and the meta chips. No new literal hex
  value was introduced, so the known Section 6.4 deviation below is unchanged and was not partially fixed for one
  paper.
- The paper was exercised in a jsdom harness before shipping (**251 checks, all passing** across two runs): nothing
  is revealed pre-submit (every active `.sol` empty and hidden, no option mark, no mark text, no "Answer:" string in
  the test pane, key tab disabled and labelled locked, key pane empty, summary hidden, timer at 60:00, one card
  visible); the palette reaches `ans` / `mrk` / `amr` and falls back correctly on Clear Response; all 25 answered
  correctly scores **35 / 35** with 25 correct, 0 wrong and 25 `ok` palette buttons; a deliberately wrong MCQ, an
  MSQ one option short and a wrong NAT score **30 / 35** with 22 correct, 3 wrong and 0 unattempted, confirming that
  an MSQ earns nothing unless the exact set is selected and that there is no negative marking; every card carries
  `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and `data-source`;
  all four subtopics appear; the Question Bank tab renders 100 cards with no active question repeated; and the About
  tab renders once the bank tab is hidden.
- `index.html` holds all **1025** questions. Its data block was updated in place: the new test record was prepended,
  the 25 new question records appended, and Theory of Computation Units 2, 3 and 4 registered in the portal's `units`
  table — they had never been added, so the 50 Unit 2 questions banked yesterday had no card in the archive view.
  Two defects were repaired while doing this. First, the render loop was `D.tests.slice().reverse()`, which printed
  the **oldest** paper first and the newest last, contradicting Section 5.1; it now sorts by date descending, so the
  newest paper renders first. Second, the static header strings had drifted one run behind the data block (they said
  61 units / 24 sets / 975 records while the data held 61 / 25 / 1000); they are now recomputed from the data block
  and read 64 units, 26 sets published, 1025 solved questions, 1025 records and 277 subtopics. Every `href` on the
  portal resolves, and the archive view now shows Theory of Computation Units 1, 2 and 3 at 50, 50 and 25 solved.



- **2026-10-27, Theory of Computation → Unit 2 (Grammars & Context-Free Languages), Set 2 of 2.** MODE A: one
  subject was drawn uniformly at random from the seven subjects that had not already produced a paper dated
  2026-10-27 (discrete-mathematics, engineering-mathematics, algorithms, theory-of-computation, compiler-design,
  operating-systems, databases) with an unseeded `random.SystemRandom()` draw; it gave **Theory of Computation**.
  The bank read back `runs[-1] = {date 2026-10-26, unit 2, set "Set 1 of 2"}`; Unit 2 stood at **25** questions,
  below `UNIT_QUESTION_CAP = 50`, and had been current for 1 day, below `DAYS_PER_UNIT_MAX = 7`, so step B3 held
  and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 2 now holds
  exactly 50 questions and the next Theory of Computation run advances to
  `(index_of(cfl-grammars) + 1) mod 4 = 2` → **Unit 3, Pushdown Automata**. No override was used, no unit
  exceeded 50 questions and no second pass has started.
- Coverage this run: all four Unit 2 subtopics — CFG derivation trees (6), ambiguity in grammars (6), CNF & GNF
  normal forms (7), closure properties of CFLs (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: no stem repeats `TOC-U2-Q01`..`TOC-U2-Q25`. The Set 1 paper was moved to
  `theory-of-computation/cfl-grammars/archive/gate_toc_mock_2_2026-10-26_run1.html` with its content frozen, and
  the Set 2 paper took the canonical filename, so the unit folder holds exactly one current paper. No root copy
  was written.
- **Every countable answer was recomputed by script, not by hand.** The Catalan recurrence gives **2** trees for
  `a + a + a` under `S → S + S | a` (Q8) and **5** trees for `aaaa` under `S → SS | a` (Q12), cross-checked
  against `C₂ = 2` and `C₃ = 5`; `S → aS | Sa | a` was enumerated by its recurrence `T(n) = 2T(n−1)` and yields
  1, 2, 4, 8 trees for `a`, `aa`, `aaa`, `aaaa`, so the shortest ambiguous string is `aa` (Q9); the Dyck
  membership test was run on `aabb`, `abab`, `aaabbb` (in) and `abba` (out) for `S → aSb | SS | ε` (Q3); the
  `ε`-node tree for `a⁴b⁴` under `S → aSb | ε` was walked node by node, giving **5** internal nodes (Q2); the
  unit-production elimination on `S → A | B | c, A → aA | a, B → bB | b` was executed symbolically and leaves
  `S → aA | a | bB | b | c` plus the two untouched nonterminals, i.e. **9** productions (Q15); and the CYK
  triangular table for `n = 10` is `10 × 11 / 2 = **55**` entries (Q21).
- The conceptual items were settled by the standard rather than by taste: a node and its ordered children encode
  exactly one production; the yield of a subtree rooted at `A` is a string derivable from `A`, not a member of
  `L(G)`; a nonterminal repeated on one root-to-leaf path is the tree-level statement of the CFL pumping lemma
  and says nothing about ambiguity; `S → AB | ε` with nullable `A` and `B` is ambiguous because `ε` has two
  trees; GNF derivations take exactly `|w|` steps while CNF trees have `2n − 1` nodes; the `j > i` ordering in
  GNF conversion is a termination measure, not the GNF condition itself; CNF pumping bounds the repeated block
  by `2^k`, not by `k`; CFL is closed under reversal, inverse homomorphism, substitution and right quotient by a
  regular language, but not under intersection or complement; DCFL is closed under complement, so `{aⁿbⁿ}` and
  its complement are both context-free although the language is not regular; and `{aⁱbʲcᵏ : i ≠ j}` is
  context-free while `{aⁱbʲcᵏ : i < j < k}` is not.
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4,
  (C) 4 and (D) 3, and the five MSQ answer sets are (A,B,C), (B,D), (B,C,D), (A,C) and (A,B,C).
- No verified PYQ exists for this unit: `verified_pyqs` stays empty for this subject, the Question Bank tab shows
  **75 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **75** banked items that are not part of the active set — the
  50 Unit 1 questions and the 25 Unit 2 Set 1 questions — under one accordion per unit and one heading per
  subtopic, every solution collapsed. The 25 active Set 2 questions do not appear there (verified: zero overlap
  between the 25 active stems and the 75 banked stems).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it.
  The `<style>` block (13 243 bytes) and the exam `<script>` (9 445 bytes) are byte-for-byte identical to the
  Computer Networks Unit 1 Set 2 paper, and the `:root` block matches `design-tokens.css` and `index.html`
  exactly. No new literal hex value was introduced, so the known Section 6.4 deviation below is unchanged and was
  not partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**39 checks, all passing**): nothing is revealed
  pre-submit (every active `.sol` empty and hidden, no option mark, no mark text, key tab disabled and labelled
  locked, key pane empty, summary hidden, timer at 60:00, one card visible); the palette reaches `ans` / `mrk` /
  `amr` and falls back correctly on Clear Response; a mixed paper scores **8 / 35** with 6 correct, 2 wrong and
  17 unattempted, confirming that an MSQ one option short earns nothing and that there is no negative marking;
  every card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`,
  `data-difficulty` and `data-source`; all four subtopics appear; and the Question Bank tab renders 75 cards with
  no active question repeated.
- `index.html` holds all **1000** questions. Its data block was updated in place: the new test record was
  prepended so the newest paper renders first, the 2026-10-26 Theory of Computation Unit 2 card was retargeted at
  the archived copy, and every `href` on the portal resolves. Per-subject question counts in the portal match
  each `master_bank.json`.

- **2026-10-27, Computer Networks → Unit 1 (Layering, Physical & Framing), Set 2 of 2.** MODE A: one subject was
  drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw; the draw
  index was 10 of 11 and gave **Computer Networks**. The bank read back `runs[-1] = {date 2026-10-26, unit 1, set
  "Set 1 of 2"}`; Unit 1 stood at **25** questions, below `UNIT_QUESTION_CAP = 50`, and had been current for 1 day,
  so step B3 held and step B4 was not reached: the current unit was generated again. This is Set 2 of 2, so Unit 1
  now holds exactly 50 questions and the next Computer Networks run advances to `(index_of(network-fundamentals-framing)
  + 1) mod 6 = 1` → **Unit 2, Data Link Protocols & MAC**. No override was used, no unit exceeded 50 questions and no
  second pass has started.
- Coverage this run: all four Unit 1 subtopics — OSI & TCP/IP models (6), delays & bandwidth-delay product (6),
  framing: bit & byte stuffing (6), CRC, checksum & Hamming (7). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty
  10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: no stem, option set or numeric answer repeats a Set 1 question. The Set 1 paper was moved to
  `computer-networks/network-fundamentals-framing/archive/gate_cn_mock_1_2026-10-26_run1.html` before this one was
  written, so the unit folder holds exactly one current paper, no root copy was written, and the archived paper's
  content is frozen (same questions, options, answers, solutions and duration).
- Every numeric answer was recomputed by script, not by hand: traffic intensity 60 × 1500 × 8 / 10⁶ = **0.72** (Q8);
  bandwidth-delay product 10⁷ × 0.025 = **250000 bits** (Q9); one-way delay 4000/10⁶ + 10⁶/(2×10⁸) = **9 ms** (Q12);
  worst-case bit stuffing ⌊1024/5⌋ = **204** (Q14); de-stuffing `0111110011111001` → **01111101111101** (Q15), checked
  by re-stuffing the result back to the received stream; byte-stuffing overhead 300 + 12 + 5 = **317** (Q18); CRC
  `1100` ÷ `1011` leaves remainder `010` = **2** (Q21); Hamming capacity 2⁶ − 6 − 1 = **57** (Q25).
- No verified PYQ exists for this unit: `verified_pyqs` stays empty for this subject, the Question Bank tab shows
  **25 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (8) or `ORIGINAL_SYNTHESIS` (17), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **25** solved Set 1 questions under four subtopic accordions,
  every solution collapsed, and the 25 active Set 2 questions do not appear there (verified: zero overlap between
  the 25 active stems and the 25 banked stems).
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block (13 243 bytes), the exam `<script>` (9 428 bytes) and the `:root` block are byte-for-byte identical
  to the Computer Architecture Unit 2 paper and to the archived Computer Networks Set 1 paper, and the `:root` block
  also matches `design-tokens.css` and `index.html`. The paper carries 114 literal hex occurrences outside `:root`,
  the same count as the Set 1 paper it replaces, so the known Section 6.4 deviation below is unchanged and was not
  partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**285 checks, all passing**): nothing is revealed
  pre-submit (every `.sol` empty and hidden, no option mark, no mark text, key tab disabled, key pane empty, summary
  hidden, timer at 60:00, every input enabled); the palette reaches `na` / `ans` / `amr` / `cur` and falls back
  correctly on Clear Response; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong and 25 `ok`
  palette buttons; a deliberately wrong MCQ, a partial MSQ and a wrong NAT score **30 / 35** with 3 wrong and 22
  correct, confirming MSQ earns nothing unless the exact set is selected and that there is no negative marking; every
  card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and
  `data-source`; all four subtopics appear; and the Question Bank tab renders 25 cards with no active question
  repeated.
- `index.html` holds all **975** questions; the Computer Networks Unit 1 card reads "50 solved" in the archive view
  with four subtopic pills and two launch buttons ("Practise Set 1 →" for the archived 2026-10-26 paper and
  "Practise Set 2 →" for today's), and its data block was updated in place so the newest paper renders first. The
  2026-10-26 card's link was retargeted at the archived copy, so every `href` on the portal resolves. Static header
  strings were recomputed from the data block: 11 subjects, 61 units, 975 solved, 24 sets published, 975 records,
  264 subtopics.

- **2026-10-27, Programming and Data Structures → Unit 2 (Pointers, Memory & Preprocessors), Set 1 of 2.** MODE A:
  one subject was drawn from the nine that had not already produced a paper dated 2026-10-27, with
  `random.Random(20261027).choice` over the list in syllabus order minus Digital Logic and Computer Architecture
  (both already ran today). The draw gave **Programming and Data Structures**. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "2 of 2"}`; Unit 1 stood at **50** questions, exactly
  `UNIT_QUESTION_CAP = 50`, so the cap test in step B3 failed and step B4 advanced exactly one unit:
  `(index_of(c-programming-core) + 1) mod 7 = (0 + 1) mod 7 = 1` → **Unit 2, Pointers, Memory & Preprocessors**
  (`pointers-memory`). This is Set 1 of 2; 25 questions are now banked on Unit 2 and the next Programming and Data
  Structures run generates Unit 2 again before advancing to Unit 3. No override was used, no unit exceeded 50
  questions and no second pass has started.
- Coverage this run: all four Unit 2 subtopics — pointer arithmetic (7), pointers to functions (6), dynamic memory
  allocation (6), macro expansion, scope & lifetime (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy /
  10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: no stem, code listing, option set or numeric answer repeats a Unit 1 question. The paper is
  filed only at `programming-data-structures/pointers-memory/gate_ds_mock_2_2026-10-27.html`; Unit 2 had no earlier
  paper, so nothing was archived, no root copy was written and the unit folder holds exactly one current paper.
- **Every program-output answer was compiled and executed, not reasoned about by hand.** All thirteen C listings on
  the paper were built with `zig cc 0.17.0 -std=c11 -O0` and run. Confirmed: `*(p-1) + p[1]` = **60** (Q1);
  `(char*)(p+3) - (char*)p` over a `sizeof`-8 struct = **24** bytes (Q2); the pointer-to-pointer trace prints
  **`2 3 14`** (Q6); the pre-decrement loop prints **`43210`** (Q7); the dispatch table over `(7,3)` sums to **35**
  (Q10); the nested `typedef` table prints **20** (Q11); `SQR(2+3)` with `#define SQR(x) x*x` prints **11** (Q20);
  the `static` local prints **`1 2 3`** (Q22); `CUBE(1+2)` with unparenthesised `SQ`/`CUBE` prints **7** (Q23); the
  block-scope `extern int x` prints **`10 20`** (Q24); `calloc(6, sizeof(struct rec))` with `sizeof` 16 requests
  **96** bytes (Q15); the overwritten `malloc` handle leaks **20** bytes (Q19). `sizeof(*(a+1))` for `int a[3][4]`
  evaluates to 16, which is what fixes the type in Q5 as `int (*)[4]`. Two declaration questions were checked by
  compilation rather than by eye: `int (*f)(int, int)` and `typedef char (*F)(int)` are the only options of Q8 and
  Q13 that declare a pointer to a function.
- The conceptual items were settled by the standard rather than by taste: `a + n` is a legal one-past-the-end value
  but must not be dereferenced; `p - q` has type `ptrdiff_t`, not `int`; function pointers compare for equality but
  not for order; `fp()` and `(*fp)()` are both valid calls; a function pointer does not convert to `void *` by
  guarantee; `realloc(p, 0)` is implementation-defined in C99 and is not a portable free; `malloc(0)` may return
  `NULL` or a unique freeable pointer; `free` on a non-heap pointer is undefined behaviour; an identical macro
  redefinition is allowed while a different one must be diagnosed; `const` does not imply static storage duration;
  and file-scope `static` gives internal linkage.
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 5 times, (B) 4,
  (C) 3 and (D) 3, and the five MSQ answer sets are (A,C), (A,B), (A,B,D), (A,C,D) and (A,C,D). Option order was
  fixed at drafting time so the letter distribution was balanced before the solutions were written.
- No verified PYQ exists for this unit: `verified_pyqs` stays empty for this subject, the Question Bank tab shows
  **50 solved** and **0 verified GATE PYQs**, and no item is tagged `GATE_PYQ_VARIATION`. Every item is
  `STANDARD_TEXTBOOK` (14) or `ORIGINAL_SYNTHESIS` (11), so nothing on this paper claims previous-year status.
- The Question Bank tab inside the paper lists the **50** solved Unit 1 questions under four subtopic accordions
  inside one unit accordion, every solution collapsed, and the 25 active Unit 2 questions do not appear there.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block (13 235 bytes), the exam `<script>` (9 419 bytes) and the `:root` block are byte-for-byte identical
  to the Computer Architecture Unit 2 paper, and the `:root` block also matches `design-tokens.css` and
  `index.html`. No new literal hex value was introduced; the paper carries 81 hex occurrences outside `:root`,
  the same count as the reference shell, so the known Section 6.4 deviation below is unchanged and was not
  partially fixed for one paper.
- The paper was exercised in a jsdom harness before shipping (**146 checks, all passing**): nothing is revealed
  pre-submit (every `.sol` empty and hidden, no option mark, no mark text, key tab disabled, key pane empty, summary
  hidden, timer at 60:00); the palette reaches `ans` / `amr` / `na` / `cur` and falls back correctly on Clear
  Response; all 25 answered correctly scores **35 / 35** with 25 correct, 0 wrong and 25 `ok` palette buttons; every
  card carries `data-subject`, `data-unit`, `data-unit-number`, `data-subtopic`, `data-type`, `data-difficulty` and
  `data-source`; all four subtopics appear; and the Question Bank tab renders 50 cards with no active question
  repeated.
- `index.html` holds all **950** questions; the new Programming and Data Structures Unit 2 card reads "25 solved"
  with four subtopic pills and one "Practise Set 1 →" button, and its data block was updated in place so the newest
  paper renders first. Its static header strings were recomputed from the data block: 11 subjects, 61 units,
  950 solved, 49 sets published, 950 records, 264 subtopics.

- **2026-10-27, Computer Architecture → Unit 2 (CPU Control Design & Data Path), Set 1 of 2.** MODE A: the subject was
  drawn with `random.Random(20261027).choice` from the ten subjects that had not already produced a paper today
  (Digital Logic had taken three runs of the day and both of its units were at the 50-question cap, so it was excluded
  from the draw rather than being given a fourth paper). The draw gave **Computer Architecture**, the one subject with
  no folder, no bank and no `runs[]` history. With no `runs[]` entry there is no `current_unit` to measure against the
  cap, so the documented fallback applied: `unit_index = (2026-10-27 − 2026-10-26) mod 6 = 1` → **Unit 2, CPU Control
  Design & Data Path** (`datapath-control-unit`). No override was used, no unit exceeded 50 questions, and no second
  pass has started.
- Coverage this run: all four Unit 2 subtopics — hardwired control (7), microprogrammed control (6), ALU & datapath
  timing (6), bus architectures (6). Composition 15 MCQ / 5 MSQ / 5 NAT; difficulty 10 easy / 10 medium / 5 hard;
  marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new to the series: `computer-architecture/question-bank/master_bank.json` is created by this run, so
  there is nothing to collide with. No earlier set exists for this unit, so nothing was archived and the paper is filed
  at `computer-architecture/datapath-control-unit/gate_co_mock_2_2026-10-27.html` and nowhere else.
- **Every numeric answer was recomputed by script, not by hand.** 6 timing states need 3 counter bits (Q3); a 3-to-8
  decoder serving 7 states leaves 1 output unused (Q6); 1024 control-store words need a 10-bit microprogram counter
  (Q10); 512 × (40 + 10) = 25,600 control-store bits (Q11); 3 × ⌈log₂10⌉ + 6 = 3 × 4 + 6 = 18 control-word bits (Q13);
  2 + 1 + 5 + 1 + 2 = 11 ns single-bus ADD path (Q16); 31 × 2 + 3 = 65 ns to S31 (Q17); 3 + 6 + 2 + 2 = 13 ns clock
  period (Q19); 4 bytes × 100 MHz = 400 MB/s (Q22); 8 bytes × 66 MHz ÷ 2 = 264 MB/s (Q23). The remaining items are
  conceptual and their answer sets were checked option by option against the solution text.
- The paper carries `data-subject="computer-architecture"` on all 25 cards, as the portability attribute requires; it is
  the first paper in the repository for which that attribute is not `discrete-mathematics` or one of the nine subjects
  that predate this run.
- No verified PYQ exists for this unit yet: `verified_pyqs` is empty, the Question Bank tab shows **0 solved** and
  **0 verified GATE PYQs**, and the three `GATE_PYQ_VARIATION` items (Q7, Q13, Q23) are pattern-built practice questions
  that claim no year, paper or key.

- **2026-10-27, Digital Logic → Unit 2 (Combinational Circuit Design), Set 2 of 2.** MODE A: one subject was drawn at
  random from the 11 GATE CSE subjects with `random.Random(20261027).choice`, and the draw gave **Digital Logic** for the
  third run of the day. The bank read back `runs[-1] = {date 2026-10-27, unit 2, set "Set 1 of 2"}`; Unit 2 stood at
  **25** questions, below `UNIT_QUESTION_CAP = 50`, and had been current for **0** days, below `DAYS_PER_UNIT_MAX = 7`.
  Step B3 therefore held and the current unit was generated again; step B4 was not reached. This is Set 2 of 2, the unit
  now holds exactly 50 questions, and the next Digital Logic run advances `(index_of(combinational-circuits) + 1) mod 4
  = (1 + 1) mod 4 = 2` → **Unit 3, Sequential Circuits: Flip-Flops & Registers**. No override was used and no second
  pass has started.
- Coverage this run: all five Unit 2 subtopics, five questions each — adders & subtractors, multiplexers &
  demultiplexers, decoders & encoders, code converters, hazards & glitches. Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; marks 15 × 1 + 10 × 2 = 35.
- All 25 items are new: no stem repeats anything banked in Unit 1 or in Unit 2 Set 1. The Set 1 paper was moved to
  `digital-logic/combinational-circuits/archive/gate_dl_mock_2_2026-10-27_run1.html` with its content frozen, and the
  new Set 2 took the canonical filename, so the unit folder holds exactly one current paper.
- **Every answer was checked by script, not by hand.** `1 + 1 + 1 = 11₂` gives Sum 1, Cout 1 (Q1); `2 × 3 + 1 = 7`
  gate delays to `S3` (Q2); `0110 + 0110 = 1100` with carry into the sign bit 1 and carry out 0, so `V = 1` and
  `C = 0` (Q3); `7 + 8 = 15` corrects to carry 1 with digit `0101` (Q5); the 4-to-1 multiplexer data inputs were
  enumerated over all eight minterms of `Σm(0,2,5,7)`, giving `D3 D2 D1 D0 = C, C, C', C'` (Q7);
  `64/4 + 16/4 + 4/4 = 21` four-input multiplexers, cross-checked as `63 / 3` (Q10); `1 + 4 = 5` decoders (Q12);
  Gray `1011` decodes to binary `1101` = 13, confirmed by re-encoding (Q17); excess-3 `0101` is `5 − 3 = 2` (Q18);
  the BCD correction condition `Cout + S3S2 + S3S1` was tested against every binary sum 0–19 and is the only option
  that matches "sum > 9" exactly, while the distractors fail at 6–7 and 10–11, and at 16–19 (Q20); the consensus term
  for `AB' + BC` is `AC` (Q22); and the K-map of `A'C' + BC` was enumerated cell by cell, leaving `(m2, m3)` as the only
  split adjacent pair, so the hazard is `C` changing with `A = 0, B = 1` (Q25).
- No verified PYQ was added this run, so `verified_pyqs` for Digital Logic stays at two (both Unit 1 items,
  `PYQ-GATE2019-Q4` and `PYQ-GATE2016S1-Q7`). No Unit 2 item is tagged `GATE_PYQ_VARIATION`; every Unit 2 question is
  `STANDARD_TEXTBOOK` (11) or `ORIGINAL_SYNTHESIS` (14), so nothing on this paper claims previous-year status.
- Question-bank tab inside the paper shows the 75 banked items that are not part of the active set — the 50 Unit 1
  questions and the 25 Unit 2 Set 1 questions. The 25 active Set 2 questions do not appear there.
- Shell parity: the `:root` block, the `<style>` block, the palette, the answer-key view and the JavaScript are
  byte-identical to the shipped shell; the only differences from the archived Set 1 are the title, the header sub-line,
  the set chip and the bank-tab count. One markup repair was made inside the `view-bank` / `view-about` region: both
  outer `<div>`s were left unclosed in every earlier paper, which nests the About view inside the Question Bank view
  and makes the About tab render blank when the bank view is hidden. This paper closes both, so its About tab works.
  The repair is invisible in the shared shell and does not touch CSS or JavaScript, but it does mean the other 35
  papers still carry the defect — it needs the same coordinated all-papers pass as the open token deviation below.

- **2026-10-27, Digital Logic → Unit 2 (Combinational Circuit Design), Set 1 of 2.** MODE A: one subject was drawn at
  random from the 11 GATE CSE subjects with `random.Random(20261027).choice`, and the draw gave **Digital Logic** for the
  second run of the day. The bank read back `runs[-1] = {date 2026-10-27, unit 1, set "Set 2 of 2"}`; Unit 1 stood at
  **50** questions, exactly `UNIT_QUESTION_CAP = 50`, so the cap test in step B3 failed and step B4 advanced exactly one
  unit: `(0 + 1) mod 4 = 1` → **Unit 2, Combinational Circuit Design**. This is Set 1 of 2; 25 questions are now banked
  on Unit 2 and the next Digital Logic run generates Unit 2 again before advancing to Unit 3. No override was used, and
  the modulo has not yet wrapped, so no second pass has started.
- Coverage this run: all five Unit 2 subtopics, five questions each — adders & subtractors, multiplexers &
  demultiplexers, decoders & encoders, code converters, hazards & glitches. Composition 15 MCQ / 5 MSQ / 5 NAT;
  difficulty 10 easy / 10 medium / 5 hard; 35 marks.
- No verified PYQ was added this run, so `verified_pyqs` for Digital Logic stays at two (both Unit 1 items,
  `PYQ-GATE2019-Q4` and `PYQ-GATE2016S1-Q7`). No Unit 2 item is tagged `GATE_PYQ_VARIATION`; every Unit 2 question is
  `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS`, so nothing on this paper claims previous-year status.
- Question-bank tab inside the paper shows the 50 Unit 1 questions, which are the only banked items that are not part
  of the active set — the 25 active Unit 2 questions do not appear there.
- Two deliberate deviations from earlier papers, both content-level and not shell-level: the NAT answer-format hint now
  reads only "Answer format: an integer." with no worked value (earlier papers printed the answer inside the hint), and
  the `:root` block, `<style>` block and JavaScript are byte-identical to the shipped shell, so shell parity holds
  against the other papers. The Section 6.4 raw-hex and palette-contrast deviation recorded above is **still open** and
  still needs the coordinated all-papers pass; it was not partially fixed for one paper.

- **2026-10-27, Digital Logic → Unit 1 (Number Systems & Representation), Set 2 of 2.** MODE A: one subject was drawn
  at random from the 11 GATE CSE subjects with `random.Random(20261027).choice`, a date-derived reproducible seed, and
  the draw gave **Digital Logic**. The bank read back `runs[-1] = {date 2026-10-26, unit 1, set "Set 1 of 2"}` with
  **25** questions banked on Unit 1 (`number-systems`), current for 1 day. Step B3 therefore held — 25 <
  `UNIT_QUESTION_CAP = 50` and 1 < `DAYS_PER_UNIT_MAX = 7` — so the current unit was generated again and step B4 was
  not reached. This is Set 2 of 2; the unit now stands at exactly 50 questions, so the next Digital Logic run advances
  one unit. No override was used and no second pass has started.
- All 25 items are new: no stem repeats a question already banked on Unit 1. Composition is the standard 15 MCQ /
  5 MSQ / 5 NAT with the 10 easy / 10 medium / 5 hard split, and marks total 15 × 1 + 10 × 2 = 35. Coverage is
  7 / 6 / 6 / 6 across base conversions, one's and two's complement, IEEE 754 and range/overflow, so all four
  subtopics are represented.
- **Every numeric answer was recomputed by script, not by hand.** `0xB7C = 2940` (Q1); `(1101.101)₂ = 13.625` (Q2);
  `(27)₈ + (45)₈ = (74)₈`, checked as 23 + 37 = 60 (Q3); `1101 0110 1111 = 0xD6F` (Q4); `(101101)₂ + (1101)₂ = 58`
  (Q6); `(2E.A)₁₆ = 46.625` (Q7); the one's complement of −37 is `1101 1010` (Q8); `1000 0001` is −127 (Q9);
  sign-extending `1100 1011` preserves −53 (Q10); a 4-bit one's complement register holds 15 distinct integers (Q11);
  `0xFF9C = −100` (Q13); `0x40400000 = 3.0` (Q16, decoded with `struct.unpack`); `0x41200000 = 10.0` (Q19);
  400 mod 256 = 144, which reads back as −112 (Q25).
- No verified PYQ was added this run, so `verified_pyqs` for Digital Logic is unchanged at two. Two items are tagged
  `GATE_PYQ_VARIATION` on recurring GATE patterns (octal addition with a carry at the base; the smallest normal
  IEEE 754 single precision number) with no year claimed.
- No paper was archived: Set 1 (2026-10-26) is a different question set on a different date, not a superseded run of
  this one, so it stays at unit level beside Set 2.
- **2026-10-26, Engineering Mathematics → Unit 2 (Linear Algebra: Eigenvalues & Vectors), Set 1 of 2.** MODE A: one
  subject was drawn at random from the 11 GATE CSE subjects with `random.Random(20261026).choice`, a date-derived
  reproducible seed, and the draw gave **Engineering Mathematics**. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "2 of 2"}` with **50** questions banked on Unit 1
  (`linear-algebra-matrices`). Since 50 >= `UNIT_QUESTION_CAP = 50`, step B3 failed on the cap and step B4 advanced
  exactly one unit: `(index_of(1) + 1) mod 5 = (0 + 1) mod 5 = 1` → **Unit 2, Linear Algebra: Eigenvalues & Vectors**.
  This is Set 1 of 2 for the unit; a second Engineering Mathematics run today would re-select Unit 2, since 25 < 50 and
  the unit is current for 0 days. No override was used and no second pass has started for this subject.
- All 25 items are new: no stem repeats a question already banked on Unit 1. Composition is the standard 15 MCQ /
  5 MSQ / 5 NAT with the 10 easy / 10 medium / 5 hard split, and marks total 15 × 1 + 10 × 2 = 35. Coverage is
  6 / 7 / 5 / 7 across characteristic equations, eigenvalue properties, the Cayley–Hamilton theorem and
  diagonalization, so all four subtopics are represented.
- **Every numeric answer was recomputed by script with sympy, not by hand.** The characteristic polynomial of
  `[[2,1],[1,2]]` is `λ² − 4λ + 3` with eigenvalues 1 and 3 (Q1); the polynomial of `A⁻¹` was rebuilt from
  `(λ−1)(λ−2)(λ−3)` as `μ³ − (11/6)μ² + μ − 1/6` (Q7); `A⁴ = 145A + 54I` was confirmed against the direct product
  `A⁴ = [[199,290],[435,634]]` for `A = [[1,2],[3,4]]` (Q13); the `(1,1)` entry of `[[2,1],[1,2]]¹⁰` was confirmed as
  `(3¹⁰+1)/2 = 29525` (Q14); `A⁻¹ = 4I − A = [[2,−3],[−1,2]]` for `A = [[2,3],[1,2]]` (Q10); `A³ = [[37,54],[81,118]]`,
  so the `(2,2)` entry is 118 (N3); `[[1,1],[0,2]]¹⁰ = [[1,1023],[0,1024]]` (N4); `rank(diag(1,1,2) − I) = 1` (Q12);
  `det(A²+A+I) = 3·1·7 = 21` for eigenvalues 1, −1, 2 (Q4); `tr(A⁻¹) = 25/12` for eigenvalues 1, 2, 3, 4 (Q8); and the
  3-cycle permutation matrix `[[0,1,0],[0,0,1],[1,0,0]]` was confirmed to satisfy `A³ = I` with eigenvalues
  `{1, ω, ω²}` and trace 0 (N5). The four candidate matrices of the diagonalizability MSQ were each tested with
  sympy rather than by inspection.
- No `GATE_PYQ_VARIATION` item is present. No eigenvalues-and-eigenvectors previous-year question has been verified
  against an official paper and key, so none is claimed as an official GATE question; the paper says this in its
  Question Bank tab and in the About tab.
- The new paper is filed only at `engineering-mathematics/eigenvalues-eigenvectors/`. No previous current paper existed
  for Unit 2, so nothing was archived and the unit folder holds exactly one current paper. The Unit 1 paper stays where
  it is; it is still current for its own unit.
- Bank and dashboard hygiene: `meta.total_questions` in the Engineering Mathematics bank had drifted to 25 while 50
  records were present after the previous run. It is now recomputed from `len(questions)` on every append and stands at
  75. The portal's embedded question data had also drifted (800 records against 825 in the banks, and stale per-subject
  splits for Discrete Mathematics and Theory of Computation); `index.html` was regenerated from all ten master banks,
  so every dashboard count now matches its bank.
- **2026-10-26, Theory of Computation → Unit 2 (Grammars & Context-Free Languages), Set 1 of 2.** MODE A: one
  subject was drawn uniformly at random from the 11 GATE CSE subjects with an unseeded `random.SystemRandom()` draw
  (seed 2455681511, draw index 6 of 11) and it gave **Theory of Computation**. The bank read back
  `runs[-1] = {date 2026-10-26, unit 1, set "Set 2 of 2"}` with **50** questions banked on Unit 1
  (`regular-languages-fa`). Since 50 >= `UNIT_QUESTION_CAP = 50`, step B3 failed on the cap and step B4 advanced
  exactly one unit: `(index_of(1) + 1) mod 4 = (0 + 1) mod 4 = 1` → **Unit 2, Grammars & Context-Free Languages**.
  This is Set 1 of 2 for the unit; a second Theory of Computation run today would re-select Unit 2, since 25 < 50 and
  the unit is current for 0 days. No override was used and no second pass has started for this subject.
- All 25 items are new: each question body was compared as an exact string against the 50 Unit 1 questions already in
  `master_bank.json`; none repeats. Composition is the standard 15 MCQ / 5 MSQ / 5 NAT with the 10 easy / 10 medium /
  5 hard split, and marks total 15 × 1 + 10 × 2 = 35. Coverage is 7 / 6 / 6 / 6 across CFG derivation trees, ambiguity,
  CNF & GNF normal forms, and CFL closure properties, so all four subtopics are represented.
- **Every answer that can be computed was recomputed by script, not by hand.** The Catalan counts were evaluated by
  the recurrence — `C2 = 2` for `aaa` (Q9) and `C4 = 14` for `a⁵` (Q10); the derivation-tree node counts were
  simulated — **4** internal nodes for `aaab` under `S → aS | b` (Q1) and **6** for `a³b²` under
  `S → AB, A → aA | a, B → bB | b` (Q6); the language of `S → aSc | T, T → bTc | ε` was enumerated and only
  `a²bc³` of the four offered strings is a member (Q7); the four candidate grammars of Q15 were each tested against
  the two CNF production shapes and only `S → AB, A → a, B → b` passes; and the standard ε-elimination procedure was
  run on Q18's grammar, giving nullable set `{A, B, S}` and exactly **8** productions
  (`S → AB | A | B | ε`, `A → aA | a`, `B → bB | b`). The full-tree bound in Q4 was re-derived after a first draft
  shipped the wrong answer: with no ε- and no unit productions the maximum is **3n − 1** total nodes, not `2n − 1`,
  because terminal-production nodes are unary and were being forgotten; `2n − 1` is the *internal*-node count. The
  question, its options and its solution were rewritten to match.
- The key is not clustered on one letter: across the 15 MCQs the correct option sits at (A) 4 times, (B) 4, (C) 4 and
  (D) 3, and the five MSQ answer sets are (A,B,C), (A,C), (A,B,C), (A,B,C) and (A,C,D). Option order was fixed at
  drafting time so that the letter distribution was balanced before the solutions were written.
- No `GATE_PYQ_VARIATION` item ships: no context-free-grammar previous-year question has been verified against an
  official paper and answer key for this unit, so none is claimed and `verified_pyqs` for this subject stays empty.
  Every item is `STANDARD_TEXTBOOK` (13) or `ORIGINAL_SYNTHESIS` (12). The About tab and the Question Bank tab both
  say so.
- Unit 2 had no earlier paper, so nothing was archived: `theory-of-computation/cfl-grammars/` holds exactly one
  current paper and the Theory of Computation Unit 1 paper was not touched. No root copy was written and no unit
  folder holds two current papers.
- Shell parity: the paper was produced by splicing new content into the shipped shell rather than re-typing it. The
  `<style>` block (13 243 bytes), the exam `<script>` and the `:root` block (521 bytes, identical to
  `design-tokens.css` and to `index.html`) are byte-for-byte identical to the Theory of Computation Unit 1 paper. No
  new literal hex value was introduced.
- The Question Bank tab inside the paper lists the **50** previously banked Unit 1 questions and deliberately omits
  the 25 active Unit 2 questions, so no question appears twice in one paper. The tab label reads
  `Question Bank (50 solved)`.
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
  eigenvalues-eigenvectors/gate_em_mock_2_<date>.html current paper for Unit 2
  question-bank/master_bank.json                     append-only master question bank
programming-data-structures/
  c-programming-core/gate_ds_mock_1_<date>.html      current paper for Unit 1
  linear-data-structures/gate_ds_mock_3_<date>.html  current paper for Unit 3
  question-bank/master_bank.json                     append-only master question bank
computer-networks/
  network-fundamentals-framing/gate_cn_mock_1_<date>.html  current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
theory-of-computation/
  regular-languages-fa/gate_toc_mock_1_<date>.html   current paper for Unit 1
  question-bank/master_bank.json                     append-only master question bank
digital-logic/
  number-systems/gate_dl_mock_1_<date>.html          current paper for Unit 1
  combinational-circuits/gate_dl_mock_2_<date>.html  current paper for Unit 2
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
| 6 | Mathematical Induction & Recursion | `induction-recursion` | 50 | yes |
| 7 | Counting & Combinatorics | `combinatorics` | 50 | yes |
| 8 | Recurrence Relations & Generating Functions | `recurrence-generating-functions` | 25 | yes |
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
| 1 | Asymptotic Analysis & Recurrences | `asymptotic-analysis` | 50 | yes |
| 2 | Divide and Conquer & Sorting | `sorting-divide-conquer` | 50 | yes |
| 3 | Greedy Algorithms | `greedy-algorithms` | 50 | yes |
| 4 | Dynamic Programming | `dynamic-programming` | 0 | — |
| 5 | Graph Algorithms: Traversals & Spanning Trees | `graph-algorithms-traversals-mst` | 0 | — |
| 6 | Graph Algorithms: Shortest Paths | `shortest-paths` | 0 | — |
| 7 | Complexity Theory & NP-Completeness | `complexity-np-complete` | 0 | — |

### Programming and Data Structures

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | C Programming Foundations | `c-programming-core` | 50 | yes |
| 2 | Pointers, Memory & Preprocessors | `pointers-memory` | 50 | yes |
| 3 | Linear Data Structures | `linear-data-structures` | 50 | yes |
| 4 | Binary Trees & Tree Traversals | `trees-traversals` | 50 | yes |
| 5 | Binary Search Trees & Balanced Trees | `search-trees` | 0 | — |
| 6 | Heaps & Priority Queues | `heaps-priority-queues` | 0 | — |
| 7 | Hashing & Hash Tables | `hashing` | 0 | — |

### Databases

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | ER Models & Relational Algebra | `er-relational-algebra` | 50 | yes |
| 2 | SQL & Advanced Querying | `sql-querying` | 50 | yes |
| 3 | Database Normalization | `normalization` | 50 | yes |
| 4 | Transactions & Concurrency Control | `transactions-concurrency` | 0 | — |
| 5 | Indexing, B-Trees & Storage | `indexing-storage` | 0 | — |

### Compiler Design

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Lexical Analysis | `lexical-analysis` | 50 | yes |
| 2 | Syntax Analysis: Top-Down Parsing | `top-down-parsing` | 50 | yes |
| 3 | Syntax Analysis: Bottom-Up Parsing | `bottom-up-parsing` | 50 | yes |
| 4 | Syntax-Directed Translation & Intermediate Code | `sdt-intermediate-code` | 50 | yes |
| 5 | Runtime Environments & Code Optimization | `runtime-code-optimization` | 0 | — |

### Operating Systems

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Process Management & CPU Scheduling | `process-scheduling` | 50 | yes |
| 2 | Inter-Process Communication & Synchronization | `synchronization-ipc` | 50 | yes |
| 3 | Deadlocks | `deadlocks` | 50 | yes |
| 4 | Memory Management & Paging | `memory-paging` | 50 | yes |
| 5 | Virtual Memory & Page Replacement | `virtual-memory` | 25 | yes |
| 6 | File Systems & Disk Scheduling | `storage-file-systems` | 0 | — |

### Engineering Mathematics

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Linear Algebra: Matrices & Systems | `linear-algebra-matrices` | 50 | yes |
| 2 | Linear Algebra: Eigenvalues & Vectors | `eigenvalues-eigenvectors` | 50 | yes |
| 3 | Calculus: Limits, Continuity & Differentiability | `calculus-limits-derivatives` | 50 | yes |
| 4 | Calculus: Maxima, Minima & Integrals | `calculus-optimization-integrals` | 25 | yes |
| 5 | Continuous Probability & Distributions | `probability-distributions` | 0 | — |

### Computer Networks

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Layering, Physical & Framing | `network-fundamentals-framing` | 50 | yes |
| 2 | Data Link Protocols & MAC | `data-link-mac` | 50 | yes |
| 3 | Network Layer: IP Addressing & Subnetting | `ipv4-subnetting` | 50 | yes |
| 4 | Network Layer: Routing & Protocols | `routing-protocols` | 0 | — |
| 5 | Transport Layer: TCP, UDP & Congestion | `transport-layer` | 0 | — |
| 6 | Application Layer & Network Security | `application-layer-security` | 0 | — |

### Theory of Computation

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Regular Languages & Finite Automata | `regular-languages-fa` | 75 | yes |
| 2 | Grammars & Context-Free Languages | `cfl-grammars` | 75 | yes |
| 3 | Pushdown Automata | `pushdown-automata` | 75 | yes |
| 4 | Turing Machines & Decidability | `turing-machines-decidability` | 75 | yes |

### Digital Logic

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Number Systems & Representation | `number-systems` | 50 | yes |
| 2 | Combinational Circuit Design | `combinational-circuits` | 50 | yes |
| 3 | Sequential Circuits: Flip-Flops & Registers | `sequential-flipflops` | 50 | yes |
| 4 | Sequential Circuits: Counters & State Machines | `sequential-fsm-counters` | 0 | — |

### Computer Architecture

| # | Unit | Slug | Questions in bank | Covered |
| --- | --- | --- | --- | --- |
| 1 | Machine Instructions & Addressing Modes | `instructions-addressing` | 0 | — |
| 2 | CPU Control Design & Data Path | `datapath-control-unit` | 50 | yes |
| 3 | Memory Hierarchy & Cache Memory | `cache-memory` | 0 | — |
| 4 | Main Memory & Virtual Memory Interface | `memory-management-unit` | 0 | — |
| 5 | Instruction Pipelining | `pipelining` | 0 | — |
| 6 | I/O Interface & Storage | `io-interfaces` | 0 | — |

- **Raw hex in the Unit 2 paper (checked 2026-10-27).** The new paper carries 133 literal hex occurrences outside
  `:root`, exactly the count in the reference shell it was generated from, so no new value was introduced; every new
  card uses `var(--…)` tokens or inherits the shared shell's existing tints. The item above still needs its one
  coordinated pass across all 43 papers.
- **Bank tab structure (changed 2026-10-27, deliberately).** The Question Bank tab of the Unit 2 paper nests one
  `details.sub` accordion per subtopic inside the unit accordion, as `6.2` requires, instead of the flat subtopic
  headings used by the earlier papers. No CSS or JavaScript changed: `details.sub` and `.count` are part of the shared
  shell, so shell parity still holds. The older papers should be rebuilt with the same structure in the one-pass
  repair.

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
   Computer Architecture Unit 2 carries three variations (`CO-U2-Q07`, `CO-U2-Q13`, `CO-U2-Q23`) that are built on
   recurring control-word-width, sequence-counter and bus-bandwidth patterns but claim no year, paper or key, and the
   subject's `verified_pyqs` list is empty.
3. Everything else is tagged `STANDARD_TEXTBOOK` or `ORIGINAL_SYNTHESIS` and is practice material written for this series.
4. Historical questions are never deleted, never counted towards an active test, and are always filed under their
   `data-subtopic` slug.

## Answer key policy

The active mock test reveals nothing before submission. On submit, the file grades itself, marks the correct options,
unlocks the answer-key tab and shows a detailed solution for every question (concept, steps, final answer, why the other
options fail, common misconception, faster method, takeaway). Banked historical questions use a separate expand-on-demand
review interface.

## Known deviations (to be fixed in one pass across every paper)

- **`#view-about` is never closed, so the provenance footer is invisible (found 2026-10-28, not fixed).** In the
  shared shell the About view opens with `<div class="hidden" id="view-about">` and ends after its last card with a
  single `</div>`, which closes that card rather than the view. The parser therefore places `<footer class="foot">`
  and both trailing `<script>` elements inside `#view-about`, and because that view carries `.hidden` the footer
  defined by `5.4` never renders on any paper. The scripts still execute, so behaviour is unaffected; only the footer
  is lost. Repairing it means adding one `</div>` before `<footer>` in the shell and re-issuing all 39 current and 34
  archived papers together, so it is recorded here rather than fixed in one file and breaking shell parity.

- **Two current papers in one unit folder (found 2026-10-27, not fixed).** `digital-logic/number-systems/` holds both
  `gate_dl_mock_1_2026-10-26.html` and `gate_dl_mock_1_2026-10-27.html`, so a single unit folder carries two files that
  both claim to be current, which `4.1` forbids. Both are reachable from `index.html` and both are correct; the fault is
  filing only. Fixing it means moving the 2026-10-26 paper into `archive/` as `..._run1.html`, retargeting its portal
  card and re-running the link check, i.e. the same one-pass repair as the items below. It was not touched by the
  2026-10-27 Computer Networks Unit 1 run, which confined itself to `computer-networks/network-fundamentals-framing/`, nor by the later Computer Networks Unit 2 run of the same
  date, which confined itself to `computer-networks/data-link-mac/`.
- `6.4 No raw hex outside :root` is not yet met (the Engineering Mathematics Unit 1 Set 2 paper carries 84 literal hex
  occurrences, against the reference shell's 86 — no new value was added, because the new cards use `var(--muted)`):
  the shipped shell uses literal hex
  values for a handful of tints and borders (`#f8fafc`, `#b9c6d2`, `#eaf2f8`, …). Because every paper must share one
  byte-identical shell, this can only be corrected by re-issuing all papers together, so it is recorded here rather than
  fixed in one file and breaking shell parity.
- The `index.html` archive prints an answer line from `answer_display` and, for records created before 2026-10-25, a
  second identical line inside `solution_html`. The 50 Unit 2 records and the 25 Digital Logic Set 2 records carry it once; the
  older records still carry it twice. Normalising them is part of the same one-pass fix as the raw-hex item above.
- ~~The exam shell bound `btnNext`, `btnPrev`, `btnMark` and `btnClear` with `document.getElementById` while every
  question card carried the same four ids, so those handlers attached only to Question 1's buttons and the footer
  buttons on cards 2–25 were inert.~~ **Fixed 2026-10-26, across all 15 papers that share the current shell.** The
  handlers are now delegated to the `#qhost` container and act on the card that owns the clicked button, so Save &
  Next, Previous, Mark for review and Clear response work on every question. Verified in a jsdom harness on the
  Operating Systems paper, the Databases paper and an archived Discrete Mathematics set. The two older
  `proof-techniques/archive/..._run1/_run2` files do not use this shell and were left untouched.
- ~~In three papers the question palette sat outside the `.layout` grid.~~ **Fixed 2026-10-27.**
  `digital-logic/number-systems/gate_dl_mock_1_2026-10-26.html`, `gate_dl_mock_1_2026-10-27.html` and
  `algorithms/asymptotic-analysis/gate_algo_mock_1_2026-10-26.html` closed `.layout` before `<aside class="side">`,
  so the palette rendered as a full-width grid under the question instead of a 300px column on its right. In each,
  one closing `</div>` was moved from before the `<aside>` to after `</aside>`; `<style>`, `<script>` and the payload
  are byte-identical to the other 28 papers, so shell parity still holds. The remaining paper with a different nesting
  defect is `operating-systems/process-scheduling/archive/gate_os_mock_1_2026-10-26_run1.html`, which is missing a
  closing `</div>` inside the card region; it was left untouched rather than guessed at, and needs a proper rebuild.
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

- The Compiler Design Unit 2 Set 1 paper inherits the three open shell items above unchanged (literal hex outside
  `:root`, no explicit `:focus-visible` selector, palette fills on the `--green`/`--red`/`--violet` tokens rather than
  their `-d` variants), for the same reason: re-typing any of them in one paper would break shell parity. Its `<style>`
  block and its script are byte-identical to the previously shipped papers.

- Shell parity, measured on the 2026-10-28 Computer Networks Unit 3 Set 2 paper: its `<style>` block, its script and its
  body structure are byte-identical to the Set 1 paper it was generated from, apart from the five metadata strings that
  are allowed to differ (title, header sub-line, candidate id, Question Bank count, Set label). Against the other
  current papers, three pre-existing variants show up and none is introduced here: some papers write the meta-strip
  separators as raw glyphs where the Computer Networks papers write `&middot;`/`&mdash;` entities; some break lines
  around `</aside>` differently; and several close `.layout`/`#view-test` with one extra `</div>`, which puts the
  Answer Key panel outside `.wrap`. All three render identically or are the known nesting defect already recorded
  above, and normalising them belongs to the one-pass re-issue.
