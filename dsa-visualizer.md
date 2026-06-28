---
name: dsa-visualizer
description: >
    Generates step-by-step SVG diagrams to visually explain DSA concepts — sorting, searching, trees, graphs, DP, backtracking, and more. Use when asked to visualize, trace, draw, or explain any algorithm.
---

# DSA Visualizer Skill

Produce **static SVG diagrams** that teach DSA through step-by-step line-wise progression and state snapshots. No animation, no interactivity. Pure visual pedagogy.

---

## ⚡ Token Efficiency (highest priority)

- **SVG only, minimal prose.** Output the SVG diagram directly. Do NOT write a lengthy text explanation before or after it.

- **Skip preamble.** No "Sure, here's a visualization of…" or "Let me walk you through…". Jump straight to the SVG.
- **One short intro line max.** If context is needed, use one sentence (e.g., "Bubble Sort on `[5,3,8,1]`:"), then the SVG.
- **No post-SVG summary.** Don't restate the algorithm's time/space complexity or recap steps already visible in the diagram unless explicitly asked.
- **Reuse this skill's vocabulary table** — don't re-derive colors or sizes; reference them directly to keep your internal reasoning short.

---

## 📂 Reference-First Workflow

Before generating any SVG from scratch, **always check `references/`** in this skill's directory for an existing template:

1. **Look up**: List files in `references/` and find one matching the requested topic (e.g., `bubble-sort.svg`, `dijkstra.svg`, `bst-insert.svg`).
2. **If found**: Read the reference SVG → use it as a **base template**. Modify only what the question requires (different input values, array size, specific steps). Keep the layout, colors, and structure intact.
3. **If not found**: Generate from scratch using the rules below, then **save the result** to `references/<topic-name>.svg` for future reuse.

> **Naming convention**: lowercase, hyphenated topic name — `merge-sort.svg`, `floyd-warshall.svg`, `n-queens.svg`, `lcs-dp.svg`.

This avoids regenerating identical SVG scaffolding every time and drastically cuts token usage.

---

## Four Pillars (apply always)

1. **Algorithmic Comprehension** — Mentally execute the full algorithm first. Identify the pattern before drawing anything.
2. **Cognitive-Load Reduction** — Each step = one snapshot. Show variable/index states explicitly. Never make the student infer hidden state.
3. **Line-wise Step Sequencing** — Steps flow **top → bottom**, one per row. Each row = one logical operation. Label each step clearly.
4. **Light Aesthetics** — Soft pastel colors only. White or near-white background. No dark fills.

---

## Visual Vocabulary

| Element                                 | Shape                           | Fill      | Stroke / Color                             |
| --------------------------------------- | ------------------------------- | --------- | ------------------------------------------ |
| Section heading                         | Rounded rect                    | `#dbeafe` | `#3b82f6`                                  |
| Array cell (default)                    | Rectangle                       | `#f0fdf4` | `#86efac`                                  |
| Array cell (comparing)                  | Rectangle                       | `#fce7f3` | `#f472b6`                                  |
| Array cell (sorted)                     | Rectangle                       | `#dcfce7` | `#4ade80`                                  |
| Array cell (pivot)                      | Rectangle                       | `#fef3c7` | `#f59e0b`                                  |
| Array cell (less-than-pivot)            | Rectangle                       | `#e0f2fe` | `#38bdf8`                                  |
| Array cell (eliminated / Binary Search) | Rectangle                       | `#f1f5f9` | `#cbd5e1`                                  |
| Pointer / index label                   | Triangle ▼ above cell           | —         | `#34d399` text                             |
| Linked list node                        | Rounded rect, two compartments  | `#fef9c3` | `#fbbf24`                                  |
| Null pointer                            | `∅` text                        | —         | `#9ca3af`                                  |
| Tree node (unvisited)                   | Circle                          | `#ede9fe` | `#a78bfa`                                  |
| Tree node (current/visiting)            | Circle                          | `#fce7f3` | `#f472b6`                                  |
| Tree node (visited)                     | Circle                          | `#dcfce7` | `#4ade80`                                  |
| Tree node (back-edge / DFS)             | Circle                          | `#fef3c7` | `#f59e0b`                                  |
| Graph node                              | Circle                          | `#e0f2fe` | `#38bdf8`                                  |
| Edge (unweighted)                       | Line                            | —         | `#cbd5e1`                                  |
| Edge (active/traversed)                 | Line                            | —         | `#f472b6` thick                            |
| Edge weight label                       | White pill at edge midpoint     | `#ffffff` | `#cbd5e1` border, `#1e293b` text 13px bold |
| Stack frame                             | Stacked rectangle               | `#fff7ed` | `#fb923c`                                  |
| DP cell (empty)                         | Rectangle                       | `#f8fafc` | `#94a3b8`                                  |
| DP cell (current)                       | Rectangle                       | `#fce7f3` | `#f472b6`                                  |
| DP cell (source/dependency)             | Rectangle                       | `#fef3c7` | `#f59e0b`                                  |
| DP cell (filled/done)                   | Rectangle                       | `#dcfce7` | `#4ade80`                                  |
| DP dependency arrow                     | Curved line                     | —         | `#93c5fd` → `#86efac` after fill           |
| Heap node (normal)                      | Circle                          | `#fef3c7` | `#f59e0b`                                  |
| Heap node (inserting/sifting)           | Circle                          | `#fce7f3` | `#f472b6`                                  |
| Heap node (valid subtree)               | Circle                          | `#dcfce7` | `#4ade80`                                  |
| Heap node (last element)                | Circle                          | `#e0f2fe` | `#38bdf8`                                  |
| Trie node                               | Circle                          | `#ecfccb` | `#84cc16`                                  |
| Trie root                               | Circle 44×44px labeled ∅        | `#e0f2fe` | `#38bdf8`                                  |
| Trie end-of-word                        | Double-ring circle              | `#e8f0f8` | `#80b0d0`                                  |
| Trie shared-path edge                   | Line 3px thick                  | —         | `#84cc16`                                  |
| Trie miss edge                          | Dashed line                     | —         | `#ef4444`                                  |
| Union-Find root                         | **Square** 32×32px              | `#dbeafe` | `#3b82f6` 2px                              |
| Union-Find child                        | Circle 32×32px                  | `#f1f5f9` | `#94a3b8`                                  |
| Union-Find finding path                 | Circle                          | `#fce7f3` | `#f472b6`                                  |
| Union-Find compressed edge              | Dashed arrow                    | —         | `#3b82f6`                                  |
| UF edge direction                       | Upward arrowhead (child→parent) | —         | `#94a3b8`                                  |
| Backtrack: valid leaf                   | Circle                          | `#dcfce7` | `#4ade80`                                  |
| Backtrack: pruned                       | Circle, dashed                  | `#fef2f2` | `#ef4444` dashed                           |
| Backtrack: base case                    | Square                          | `#e0f2fe` | `#38bdf8`                                  |
| Backtrack: pending                      | Circle                          | `#ffffff` | `#cbd5e1`                                  |
| Two-pointer left                        | Triangle ▼                      | `#fce7f3` | `#f472b6`                                  |
| Two-pointer right                       | Triangle ▼                      | `#e0f2fe` | `#38bdf8`                                  |
| Sliding window (active)                 | Rect behind cells               | `#fde8f0` | —                                          |
| Sliding window (best)                   | Rect behind cells               | `#e0f5e0` | —                                          |
| Morris thread edge                      | Dashed arrow                    | —         | `#fb923c` orange                           |
| Segment tree node                       | Circle/rect with `[l,r]:val`    | `#ede9fe` | `#a78bfa`                                  |
| BIT cell                                | Rectangle                       | `#e0f2fe` | `#38bdf8`                                  |

**Background**: `#ffffff` or `#f8fafc` · **Primary text**: `#1e293b` · **Step number**: `#6366f1` bold · **Font**: sans-serif, 16–17px values, 13px annotations

---

## Dimension Reference

| Structure                  | Size                                | Gap                 |
| -------------------------- | ----------------------------------- | ------------------- |
| Sorting / searching arrays | 48×48px cells                       | 2px                 |
| 1D DP array                | 48×48px cells                       | 2px                 |
| 2D DP grid                 | 44×44px cells                       | 1px                 |
| Tree nodes                 | Circle r = max(22, text_len × 5)    | 70px between levels |
| Graph nodes                | Circle r = 22px                     | fixed positions     |
| Heap nodes                 | Circle r = 22px; array 48×48px      | —                   |
| Trie nodes                 | Circle r = 22px; root r = 22px      | 70px between levels |
| Union-Find nodes           | Circle/Square 32×32px               | —                   |
| Linked list node           | 80×36px (60px value + 20px pointer) | 20px between nodes  |
| Segment tree nodes         | Circle r = max(24, text_len × 5)    | 70px between levels |
| BIT array                  | 48×48px cells                       | 2px                 |

---

## Layout Rules

### Steps are LINE-WISE (most important rule)

Each algorithm step occupies its **own horizontal row**, top to bottom. Separated by thin dividers or `↓`. Row format: `[Step N]  description  [data state]  [variable values]`. Only headings get rounded-rect shapes. Everything else is plain text.

### Text must fit inside shapes

Estimate text width: ~8.5px/char at 16px. Set `rect width = text_width + 24px`, `height = 32px` min. For circles: `r = max(22, text_length × 5)`.

### Tree / Graph positioning

- **Root** at exact horizontal center: `root_x = viewBox_width / 2`
- **Children** at `x ± 120/2^depth` — guarantees centering and no overlap up to depth 5
- **Edge endpoints — exact circle-boundary formula (mandatory):**
    ```
    dx=x2-x1; dy=y2-y1; dist=sqrt(dx²+dy²)
    ux=dx/dist; uy=dy/dist
    start = (x1+r·ux, y1+r·uy)
    end   = (x2-r·ux, y2-r·uy)
    ```
    Compute this for EVERY edge before writing SVG coordinates. Never eyeball.
- **Weighted edge label position:**
    ```
    mid = ((start.x+end.x)/2, (start.y+end.y)/2)
    px=-uy; py=ux  (perpendicular)
    label_pos = (mid.x+12·px, mid.y+12·py)
    ```
    Draw white pill behind the weight. Flip sign if it overlaps a node.
- **Graphs**: fixed node positions across all frames

### Clean line rule

Every `<line>`/`<path>`/`<circle>` must be load-bearing. No stray, dangling, duplicate, or zero-length elements. No overlapping text or shapes. Re-read every element before finalizing.

### Sizing

- SVG width: 900px minimum; 1000–1100px for side-panel layouts
- Height: scales with step count (~70–80px per row)
- Padding: 24px all edges

---

## Output Format

Single self-contained SVG via `show_widget`:

```
Title (blue rounded rect)
Step 1: description  [data state]  vars
Step 2: ...
Final State (green rounded rect)
```

---

## Algorithm-Specific Notes

---

## 🔍 Searching

### Linear Search

**Array**: 48×48px cells, `curr` triangle ▼ pointer above array. Show `"Searching for: X"` box at top.

1. Highlight current cell pink; show `"A[i] == target? X == Y"`
2. **Found**: cell green, `"FOUND at index i"`, stop
3. **Not found**: cell gray; advance pointer; past last cell → `"NOT FOUND"`

### Binary Search

**Array**: 48×48px cells. `lo`/`mid`/`hi` as labeled triangle ▼ pointers below array.

1. Label `lo=0, hi=n-1`
2. Compute `mid=(lo+hi)/2` → highlight `A[mid]` pink; show comparison as text
3. Eliminate wrong half → gray fill + diagonal-hatch pattern on eliminated cells
4. Update pointers, draw bracket on active range
5. Found → green; Not found → all gray with `"NOT FOUND"`

---

## 📊 Sorting

**Common rules for all sorts**: 48×48px cells, 2px gap, index labels below.

**Color states:**
| State | Fill | Stroke |
|---|---|---|
| Default | `#f0fdf4` | `#86efac` |
| Comparing | `#fce7f3` | `#f472b6` |
| Swapping | `#fce7f3` | `#e879a6` (darker) |
| Sorted | `#dcfce7` | `#4ade80` |
| Pivot | `#fef3c7` | `#f59e0b` |
| Less-than-pivot | `#e0f2fe` | `#38bdf8` |
| Greater-than-pivot | `#f1f5f9` | `#cbd5e1` |

Each step = one comparison OR one swap OR one partition — never bundle.

### Bubble Sort

1. Compare adjacent pair → both pink
2. If swap needed → show before/after
3. After each full pass → rightmost unsorted becomes green
   Show outer loop iteration number.

### Selection Sort

1. Mark current position with pink outline; scan right to find minimum (light pink per comparison)
2. Highlight found minimum brighter pink; swap → mark position green, advance

### Insertion Sort

1. Take next element → amber `key`; shift sorted elements right one by one
2. Insert `key` at correct position; extend green region with vertical separator line

### Merge Sort — split-view

- Left: subarray with `i`; Right: subarray with `j`; Bottom: merged result building left-to-right
- Compare `A[i]` vs `B[j]` → pink; take smaller → green append
- Show call-hierarchy tree on the left for top-level view

### Quick Sort

1. Choose pivot → amber, label `"pivot = X"`
2. Partition: `A[j] < pivot` → swap `A[i]↔A[j]` → both blue; else gray
3. Pivot to correct position → green; show `lo`, `hi`, `p` explicitly

### Heap Sort

**Uses dual view (array top, tree bottom) from Heap section.**

**Phase 1 — Build-Heap** (heapify from `floor(n/2)−1` down to `0`):
Follow Build-Heap step pattern. Final: entire array valid max-heap, all green.

**Phase 2 — Repeated Extract-Max**:

1. Swap `A[0]↔A[n-1]` → show swap in both views
2. Mark `A[n-1]` sorted (green); draw red dashed vertical line as heap boundary
3. Heapify down from root on reduced heap; repeat
   Show `"Extract max=9, heap size: 6→5"` each step. Sorted region grows from right.

### Counting Sort

**Three arrays stacked**: input (top), count array (middle), output (bottom).

1. **Count phase**: for each input element → increment count cell (amber); label `"Count array (index = value)"`
2. **Prefix-sum phase**: `count[i] += count[i-1]` left-to-right; annotate `"count[3]=3 (last position of 3 in output)"`
3. **Placement phase**: traverse input right-to-left; use `count[v]-1` as output index; place → green; draw arrow input→count→output at each step

### Radix Sort

**LSD approach.** For each digit position `d` (units → tens → hundreds):

1. Label `"Pass d: sorting by digit at position d"`
2. Extract digit of each element → pink, show digit: `"142 → digit=4"`
3. Place into bucket row `0..9` (amber); collect back in order (green)
4. Show reassembled array with `↓ collect` annotation
   Show 10 horizontal bucket rows labeled `0..9`; elements fill left-to-right per bucket.

---

## 🌳 Trees

**Positioning**: root at SVG center, children at `x ± 120/2^depth`, 70px between levels.

### DFS (Depth-First Search)

- Highlight current node pink; show **recursion stack** on right: `Stack: [3, 7, 12]` with current at bottom
- Backtrack → node green, pop from stack; repeat for right subtree

### BFS (Breadth-First Search)

- Show **queue** as horizontal bar on right: `[2, 5, 8]` with `front` and `back` labels
- Dequeue → pink; enqueue children → amber; processed → green; show queue after every operation

### BST Insert

1. Start at root; show `"X < node.val, go left"` annotation at each comparison
2. Follow path; insert at null position → new green node + green edge

### BST Delete — 3 cases

- **Case 1 (leaf)**: remove node, edge disappears
- **Case 2 (one child)**: pointer redirect arrow shown
- **Case 3 (two children)**: find inorder successor (show search path), swap values, delete successor (reduces to Case 1/2) — label both phases

### Tree Traversals (Inorder / Preorder / Postorder)

**Call stack** on left, **result sequence** building on right. Current node: pink → green.

- **Preorder (Root→Left→Right)**: visit node first, append to result: `"Visit 5 → result: [5]"`
- **Inorder (Left→Root→Right)**: recurse left first; visit root after left subtree complete → annotate `"BST inorder = sorted sequence"`
- **Postorder (Left→Right→Root)**: root only turns green after BOTH children complete — make timing visually clear

### Level Order Traversal (BFS on Trees)

Follow BFS above plus:

- **Level separators** in queue: `[2 | 5, 8 | 12, 3, 9]` with `|` marking level boundaries
- Annotate each level: `"Level 2: processing [5, 8]"`; all nodes at a level turn green simultaneously
- Result: `"Level 0: [1], Level 1: [2,3], Level 2: [4,5,6,7]"`

### Morris Traversal (Inorder — no stack/recursion)

Two edge types: **thread edges** (dashed orange) vs **tree edges** (solid gray).

1. `curr = root`
2. While `curr ≠ null`:
    - `curr.left == null`: visit `curr` (green, append); `curr = curr.right`
    - Else: find inorder predecessor `p` (rightmost in left subtree) — highlight path amber
        - `p.right == null`: **create thread** `p.right = curr` → dashed orange arrow; `curr = curr.left`; annotate `"Thread created: p→curr"`
        - `p.right == curr`: **remove thread** `p.right = null` → arrow disappears; visit `curr` (green); `curr = curr.right`; annotate `"Thread removed, node visited"`

Thread creation and removal is the defining visual — use dashed orange prominently.

---

## 🕸️ Graph Algorithms

### Dijkstra's Shortest Path

**Layout**: graph left, priority queue (min-heap) right, distance table below.

1. Init: source dist=0 (green), others=∞ (gray); PQ: `[(0, src)]`
2. Each step: extract min → pink; for each neighbor `v`: highlight edge, show `"alt=dist[u]+w(u,v)"`; if alt < dist[v] → flash cell green, update table, update PQ
3. Final: shortest-path tree green; trace `prev[]` pointers to show any path

Distance table: `node | dist | prev` — flash updated row green.

### Bellman-Ford

**Layout**: graph left, edge-list panel right, distance table below.

1. Init distances; for each of `|V|−1` iterations — show iteration number prominently
2. Process each edge: highlight, show relaxation check; if relaxed → flash node green
3. Final check: if any dist still reducible → red dashed cycle + `"NEGATIVE CYCLE DETECTED"`

### Floyd-Warshall (All-Pairs Shortest Path)

**Layout**: N×N distance matrix (44×44px cells), row/column headers = vertex labels.

Init: direct edge weights; `∞` for no edge; `0` on diagonal.

For each intermediate vertex `k`:

1. Label `"Intermediate vertex: k=B"` prominently
2. Highlight entire row k and column k amber
3. For each `(i,j)`: highlight `dist[i][k]` blue, `dist[k][j]` blue, `dist[i][j]` pink
4. Show: `"dist[A][C] = min(8, dist[A][B]+dist[B][C]) = min(8, 3+2) = 5"`
5. If improved: flash green, draw composition arrow from `[i][k]`+`[k][j]`→`[i][j]`; else `"no improvement"`
6. After all `(i,j)` for fixed `k`: show updated matrix with caption

Negative cycle: if `dist[i][i] < 0` → highlight diagonal red, `"NEGATIVE CYCLE"`.

### Kruskal's Algorithm (MST)

**Layout**: graph left, sorted edge list right, MST growing on graph, UF forest below.

1. Sort edges by weight → show sorted list panel: `[(A-B,2),(C-D,3),…]`
2. Init UF — each vertex its own component (square root nodes)
3. For each edge `(u,v,w)` in order (amber highlight):
    - Same component → `"CYCLE — skip"`, edge dashed red
    - Different → `"ADD to MST"`, edge green on graph, union UF sets
4. Stop when MST has `|V|-1` edges; show running `"MST weight: W"`

Final: MST edges thick green; non-MST edges gray dashed.

### Prim's Algorithm (MST)

**Layout**: graph left, PQ (min-heap of edges) right, visited set indicator below.

1. Start at vertex `s` → green; add all its edges to PQ; show PQ
2. Each step: extract min edge `(u,v,w)` → pink
    - `v` visited → `"skip (already in MST)"`, dashed gray
    - Else: add `v` → green, draw edge green; push `v`'s unvisited-neighbor edges to PQ
3. Show PQ sorted by weight; `Visited` set updates each step

### Topological Sort

**Both methods, separated by divider.**

**Kahn's (BFS)**: graph + in-degree table + queue

1. Compute in-degrees → table `vertex | in-degree`
2. Enqueue all `in-degree=0` vertices → blue in graph + queue
3. Dequeue `u` (pink): append to result, decrement neighbors' in-degrees; if neighbor hits 0 → enqueue (amber)
4. Show result order growing as horizontal sequence below
5. Queue empties but not all processed → `"CYCLE DETECTED"`

**DFS-based**: run DFS; on each vertex's finish → push to result stack; show stack building; reversed stack = topological order.

### Kosaraju's Algorithm (SCCs)

**Two-pass DFS.** Layout: original graph left, transposed graph right.

**Pass 1 — original graph**: run DFS; when vertex finishes → push to stack; label finish times `f=1, f=2…`

**Pass 2 — transposed graph** (all edges reversed): pop from stack → run DFS from that vertex; all vertices reached = one SCC → unique pastel color; repeat for unvisited. Label each SCC with bounding ellipse + `"SCC #N"`.

### Tarjan's Algorithm (SCCs)

**Single DFS.** Each node shows `disc=N / low=M` as two-line label. Stack on right with active nodes (orange tint).

1. Visit `u`: assign `disc[u]=low[u]=timer++`; push to stack; pink
2. For each neighbor `v`:
    - Unvisited (tree edge): recurse; after return `low[u]=min(low[u],low[v])`; update label
    - On stack (back edge): `low[u]=min(low[u],disc[v])`; amber dashed edge
3. If `low[u]==disc[u]`: `u` is SCC root → pop stack until `u` is popped; highlight those vertices unique color

SCC roots get double-border. Show `disc`/`low` values updating live.

---

## 💡 Dynamic Programming

### 1D DP

Input array (48×48px) above, DP array below aligned by index; init values in gray.

For each `i`: pink on `A[i]`, amber on relevant previous DP cells; show recurrence with actual values: `"dp[3]=max(4+(−1),−1)=4"`; write result → flash green; draw dependency arrows (blue `#93c5fd`); final answer cell bright green with trace-back.

### 2D DP

Grid `(m+1)×(n+1)`, 44×44px, row/column headers = input characters; base cases light blue.

For each cell `(i,j)`: pink border on current, amber on sources; show recurrence with values; write → flash green; draw incoming arrows. Final answer: `dp[m][n]` bright green.

### Longest Common Subsequence (LCS)

Same 2D layout. Highlight matching characters in inputs when diagonal match occurs. Trace back from `dp[m][n]` with green arrows to reconstruct LCS string.

### Edit Distance

Same 2D layout. At each cell show three operations: insert (from left), delete (from above), replace (from diagonal) — label each with cost.

### 0/1 Knapsack

Rows = items, columns = capacity 0..W. Gray out cells where `w < weight[i]`. Show include vs exclude decision explicitly.

### Coin Change

Rows = denominations, columns = amounts 0..target. Show use-coin (same row, earlier column) vs skip (row above). Init: `0` for amount=0, `∞` for others.

### Longest Increasing Subsequence (LIS)

Input array (top), DP array (below, init all `1`s).

For each `i`:

1. Pink on `A[i]`; for each `j < i` where `A[j] < A[i]`: amber on `A[j]` and `dp[j]`
2. Show: `"dp[i]=max(dp[i], dp[j]+1)=max(2, 1+1)=2"`; update → green
3. Draw upward arrow from `dp[j]` to `dp[i]` for each contributing `j`

Final: highlight `max(dp)` bright green; trace contributing cells; show LIS: `"LIS: [2, 5, 8]"`.

### Kadane's Algorithm (Maximum Subarray)

Input array + running panel below showing `current_sum` and `max_sum`.

For each `i`:

1. Pink on `A[i]`; show: `"extend or restart? max(A[i], current_sum+A[i])=max(-1, 4+(-1))=3"`
2. If restart: shade abandoned subarray gray, start fresh
3. If extend: grow shaded window to include `A[i]`
4. Update `current_sum`; if > `max_sum` → flash `max_sum` panel green

Use window shading (pink=active, green=best). Final: best subarray green, `max_sum=X`.

### Matrix Chain Multiplication

Dimensions array `p[]` at top: `p=[10,30,5,60]` means `A₁(10×30), A₂(30×5), A₃(5×60)`.

Upper-triangular DP table `m[i][j]` + split table `s[i][j]` side by side.

Fill by chain length `l=2,3,…n`:

1. Label `"Chain length l=2"` prominently
2. For each `(i,j)`: pink on `m[i][j]`; try each `k` from `i` to `j-1`: amber on `m[i][k]` + `m[k+1][j]` + cost
3. Show: `"m[1][3]=min over k of: m[1][k]+m[k+1][3]+p[0]·p[k]·p[3]"`
4. Best `k` → write value green; store in split table
   Final: `m[1][n]` = min operations; trace `s[][]` to show `"((A₁(A₂A₃)))"`.

---

## 🎯 Greedy Algorithms

### Fractional Knapsack

**Layout**: item table left, knapsack fill bar right.

Table columns: `Item | Weight | Value | Value/Weight`. Fill bar = horizontal rect of capacity `W`.

1. Compute ratios → show in table column; sort by ratio descending (amber reorder)
2. For each item: show `"remaining capacity: C"`
    - `weight ≤ C`: take whole → fill bar grows green, `"Take 100% of item i"`
    - `weight > C`: take fraction → fill bar fills amber, `"Take C/weight=X%"`, stop
3. Update `"Total value: V"` panel each step

### Huffman Coding

**Layout**: PQ (min-heap) → tree building → code table.

1. Init: each char as leaf node (circle labeled `char:freq`)
2. Build (repeat until one node left):
    - Extract two min-freq nodes → pink; create internal node `#:sum_freq`; re-insert → amber; show PQ after each merge
3. Final tree: left edges labeled `0`, right edges labeled `1`
4. Code table: char → root-to-leaf path; show bit savings: `"Original: 24 bits → Huffman: 14 bits"`

### Activity Selection Problem

**Layout**: horizontal timeline. Activities as colored bars `[start, end]`.

1. Show all activities on timeline; sort by finish time (amber reorder)
2. For each activity: pink bar; check `"start ≥ last_finish?"`
    - Compatible → green bar; update `last_finish`; add to selected list
    - Incompatible → gray bar, `"SKIP — overlaps with previous"`
      Final: green=selected, gray=rejected; `"Max activities: N"`.

### Job Sequencing with Deadlines

**Layout**: job table left, slot array right.

Table: `Job | Deadline | Profit`. Slot array: cells `1..max_deadline`.

1. Sort by profit descending (amber); for each job: scan slots from `deadline` down to `1`
    - Slot found → green with job label; add profit
    - No slot → gray, `"SKIP — no available slot before deadline"`
      Final: filled slots, total profit, job sequence.

---

## 🔤 String Matching

### Naive Pattern Searching

**Layout**: Text array top (48×48px cells), Pattern array sliding below.

1. Align pattern at offset `i`; compare character by character: match → green pairs, mismatch → red pair + `"MISMATCH at j=k"`
2. Full match → all green, `"FOUND at index i"`; mismatch → shift right with arrow
   Show sliding "window" tint under pattern.

### KMP Algorithm

**Phase 1 — Build Failure Function (LPS array)**

- Pattern + LPS array aligned; for each `i`: highlight matched prefix (green) and suffix (blue); annotate: `"lps[3]=2: 'ab' is prefix and suffix of 'abab'"`

**Phase 2 — Search**

- Text top, pattern below, LPS below pattern; `i` pointer (pink) on text, `j` pointer (blue) on pattern
- Match: both advance, cells green
- Mismatch with `j>0`: `"j=lps[j-1]=N"` — curved amber arrow showing `j` jumping back; annotate `"TEXT POINTER STAYS — no backtracking"` (the key insight)
- Full match: record position, `j=lps[j-1]` to continue

### Rabin-Karp Algorithm (Rolling Hash)

**Layout**: text above, pattern below, hash panel on right.

1. Compute `pattern_hash`; compute `text_hash` for first window
2. For each window: show hash comparison `"window_hash==pattern_hash? X==Y"`
    - Match: verify character by character → true match (green) or spurious hit (amber, `"false positive"`)
    - No match: show rolling update: `"new_hash=(old_hash−A[i]·base^(m-1))·base+A[i+m]"` — advance window
      Show rolling hash panel updating; make `O(1)` per-slide nature visible.

### Boyer-Moore Algorithm

**Phase 1 — Bad Character Table**: show `char → last_index` table for pattern.

**Phase 2 — Search** (right-to-left comparison within window):

- Mismatch at text char `c`: look up table; shift: `"Bad char 'x' at pos j: last['x']=2, shift=max(1,j-last['x'])=3"`
- Show large skip as a rightward jump arrow — the algorithm's visual advantage
- Match: all green, record, shift by 1

### Z Algorithm

**Input**: concatenated string `S = pattern+"$"+text` as cell array. Z-array below.

1. Show `$` separator highlighted amber
2. Show **Z-box** `[L,R]` as a shaded region: current rightmost matching window; `L` and `R` bracket pointers on array
3. For each `i`: pink on current position
    - `i > R`: compare directly, extend Z-box if match
    - `i ≤ R`: use `Z[i-L]` as start (show known prefix in green), only extend beyond `R` with pink comparisons
4. Update `Z[i]` → amber; if `Z[i]==pattern_length` → match, green highlight

---

## ♟️ Backtracking

**Node types:**
| Type | Visual |
|---|---|
| Active call | Pink fill `#fce7f3` |
| Completed | Green fill `#dcfce7` |
| Pruned | Red dashed border, no fill |
| Base case | Blue square `#e0f2fe` |
| Pending | White fill, gray border |

**Edge labels**: label with parameter change — `n-1`, `"include 3"`, `"place Q at (1,2)"`.

Pruned branches are the pedagogical point — always label **WHY** they were pruned.

### Recursion Trees

1. Show full tree in gray (pending); trace depth-first
2. Current node → pink; show params + local state in side panel
3. Base case → blue square, show return value
4. Return → node green, value propagates upward
5. Prune → red dashed, label reason

### N-Queens

**Side-by-side** (1000px+): chessboard left (N×N, 40×40px cells, alternating white/`#f0f0f0`), decision tree right.

- Queen → pink cell with ♕; attack conflicts → red highlight + red lines showing attack path
- Valid placement → `#e0f5e0` green glow
- Backtrack: queen removed, small `"↩ backtrack"` annotation

### Permutations

Decision tree; each level = choosing next element. Each node shows partial result: `[1, 3, _]`. Show "remaining elements" set tag below each node.

### Subsets

Binary decision tree: include left (`"+A[i]"`), exclude right (`"skip"`). Node shows current subset. Leaf = complete subset → green.

### Sudoku Solver

**9×9 grid** (44×44px). 3×3 box borders thicker than row/col borders.

- Pre-filled: `#e0f2fe`, fixed. Trial: `#fce7f3`, pink text. Confirmed: `#dcfce7`, green. Conflict: `#fef2f2`, red border.

1. Find next empty cell → pink; try 1–9: valid → place (pink), recurse; invalid → red X, try next
2. Backtrack: no valid value → clear cell, `"↩ backtrack"`, return to previous; show conflict check across row+col+box

### Rat in a Maze

**N×N grid** (48×48px). Walls = `#374151` dark; open = white; path = green; dead-end = pink with ✗.

1. Mark `(0,0)` green; try Down, Right, Up, Left in order
2. Valid move → green; no valid moves → pink ✗, `"backtrack"`, cell reverts to white
3. Reach `(N-1,N-1)` → entire path bold green; show path sequence below: `"(0,0)→(1,0)→…"`

### Subset Sum Problem

Show **recursive backtracking tree**: each node labeled `"[included] sum=S"`. Left child=include, right=exclude. Pruning: `"sum exceeds target"` (red dashed). Solution leaf: `"SOLUTION: {subset}"` (green).

Alternatively: **2D DP table** (boolean, same layout as 0/1 Knapsack) — true cells green, false light gray.

### M-Coloring Problem

**Layout**: graph left, color assignment panel right. Color legend at top.

1. Try colors 1..M for each vertex in order; check adjacent vertices → highlight edges red if conflict
2. Safe → assign color (vertex fills with color), recurse; conflict → try next color; exhausted → backtrack (vertex reverts to white)
3. All colored → `"SOLUTION FOUND with M colors"`; impossible → `"No valid M-coloring exists"`

---

## 👆 Two Pointer / Sliding Window

**Array**: 48×48px cells. Pointers are **triangles ▼ above cells** with colored pill labels.

| Pointer      | Color           |
| ------------ | --------------- |
| `left`/`lo`  | Pink `#f472b6`  |
| `right`/`hi` | Blue `#38bdf8`  |
| `mid`        | Amber `#f59e0b` |
| `i` iterator | Green `#4ade80` |

**Window shading**: rect behind active cells, 4px taller, rounded — pink tint `#fde8f0` (active), green tint `#e0f5e0` (best), gray `#f1f5f9` (invalid).

### Fixed-size Sliding Window

1. Initial window shaded pink, label `window=[0..k-1]`
2. Slide right: update pointer labels, show computation; if improved → flash green

### Variable-size Sliding Window

1. Both at 0; expand: move `right`, show constraint check
2. Contract (invalid): move `left`, shade invalid red, `"contracting to restore validity"`
3. Valid state: check if best, update green best-window

### Two Pointers Converging

1. `left` at start, `right` at end; show `A[left]=3, A[right]=7`
2. Show computation: `sum=10, target=8`; decision: `"sum > target → right--"`; pointer moves; processed cells light-green-faded

### Dutch National Flag Algorithm

Three colored regions with pointer boundaries:

- `[0..low-1]`: 0s — blue `#e0f2fe`
- `[low..mid-1]`: 1s — green `#f0fdf4`
- `[mid..high]`: unknown — amber `#fef9c3`
- `[high+1..n-1]`: 2s — pink `#fce7f3`

Three pointer triangles (`low`, `mid`, `high`) always labeled.

1. Init: `low=mid=0`, `high=n-1`; all cells amber
2. While `mid ≤ high`: pink on `A[mid]`
    - `A[mid]==0`: swap `A[mid]↔A[low]`; `low++, mid++`; `"0 found → swap with low, advance both"`
    - `A[mid]==1`: `mid++` only; `"1 found → already in place"`
    - `A[mid]==2`: swap `A[mid]↔A[high]`; `high--` only; `"2 found → swap with high"`
3. After each step: re-render all three colored regions; update all pointer labels

### Floyd's Cycle Detection (Tortoise and Hare)

**Layout**: linear chain leading into a cycle (cycle as rough circle of nodes on right).

1. `slow` (pink) and `fast` (amber) start at head
2. Each step: `slow` advances 1, `fast` advances 2 (show both hops); label `step=N`
3. Meet → meeting node bright pink, `"MEET!"`
4. Phase 2: reset one to head, advance both by 1; cycle start → green
5. `fast` reaches `∅` → `"No cycle found"`

---

## 🔺 Heap / Priority Queue

**Dual view**: array (48×48px) above, tree (r=22 circles) below — both synced every step.

**Parent-child index indicators**: brackets below array showing groups: `[0]`, `[1–2]`, `[3–4,5–6]`.
**Index tracking**: annotate every step: `"i=4, parent(i)=1"`.

### Insert (Sift-Up)

1. New element at end → blue cell at index `n`
2. Compare with parent (both pink); if violated → swap in BOTH views; label `"parent(4)=1: 8>5? swap"`; `i=parent(i)`, repeat
3. Final: node in position, ancestor paths green

### Extract-Min / Extract-Max (Sift-Down)

1. Remove root → extracted value moves to result area (green)
2. Move last element to root → blue cell to index 0, tree updates
3. Compare with BOTH children (all three highlighted); smaller/larger child identified; if violated → swap in both views; update index; repeat
4. Final: heap restored; extracted value in result area

### Heapify (Single Node)

1. Highlight node `i` pink; compare with left and right children
2. Find extremum among three; if ≠ `i` → swap in both views; recursively heapify affected child (show recursion arrow)

### Build-Heap

1. Initial unsorted array; process from `floor(n/2)−1` down to `0`
2. Each: label `"Heapify(i=3)"`; run Heapify steps; node turns green
3. Progress from leaves upward; final: entire array/tree green

---

## 🔤 Trie

- Root: r=22px, labeled `"∅"`, fill `#e0f2fe`, stroke `#38bdf8`
- **Character labels ON THE EDGE** (not the node) — 13px monospace centered on edge line
- **Shared prefix paths**: 3px thick edges to emphasize sharing
- End-of-word: double-ring circle (inner ring 28px inside outer)

### Insert

For each character `c`: exists → traverse (edge+node pink); not exists → new green node + new edge labeled `c`. After last char: double-ring marker. Annotate: `"Inserting 'at' from 'cat'"`.

### Search

For each `c`: exists → traverse (matched path green); missing → red dashed edge + `"NOT FOUND"`, stop.
All matched: end-of-word → `"FOUND ✓"` green double-ring; not end-of-word → `"PREFIX ONLY"` red.

### Prefix Search

Same as Search but success = all chars matched regardless of end-of-word. Label `"PREFIX EXISTS ✓"`. List all words with prefix on the right.

---

## 🔗 Union-Find / Disjoint Set

**Dual view**: forest left (~60% width), parent array right (~40%). Both update simultaneously.

- Regular nodes: circles 32×32px
- **Root nodes: SQUARES 32×32px**, fill `#dbeafe`; rank/size label below
- **Edges: child → parent** (upward arrowheads)

### Find with Path Compression (two passes — both shown)

1. **Pass 1**: follow parents upward, pink path; log each hop: `"parent[4]=2, parent[2]=0"`; reach root → blue
2. **Pass 2**: redirect each path node directly to root → green arrows; cross out old parent array values, write new root in green

### Union

1. Find root of set A (amber) and set B (amber)
2. Same root → `"Already in same set"`, green, stop
3. Different → compare ranks/sizes: `"rank(A)=2, rank(B)=1 → attach B under A"`; draw new root arrow; flash parent array cell green
4. Show merged forest

**By rank**: increment only on equal-rank merge. **By size**: negative size in root's parent entry.

---

## 🔗 Linked Lists

**Node structure**: 80×36px rounded rect — 60px value compartment (white) + 20px pointer compartment (amber). 20px gap between nodes.

**Pointer colors:**
| Pointer | Color |
|---|---|
| `head` | Blue `#60a5fa` pill |
| `curr`/`current` | Pink `#f472b6` pill, bold |
| `prev` | Green `#4ade80` pill |
| `next`/`fast`/`slow` | Amber `#fbbf24` pill |
| null | `∅` gray |

### Traversal

One row per node. `curr` pill above current node. Visited nodes turn green progressively. Show `"curr.val=X"` label.

### Reversal

Show **ALL pointer states simultaneously every row**:

- Already-reversed: solid arrow pointing backward, green
- Current flip: pink arrow
- Not-yet-touched: gray forward arrow
  Every node has exactly one visible outgoing arrow. Label `prev`/`curr`/`next` beneath their nodes.

### Floyd's Cycle Detection

See Two Pointer section above.

### Merge Two Sorted Lists — three-row layout

- Row 1: list A with `l1` pointer
- Row 2: list B with `l2` pointer
- Row 3: merged result with `dummy` head + `tail` pointer
- Compare `l1.val` vs `l2.val` (both pink); take smaller → green; annotate: `"pick 3 from B (3<5)"`. One list empty → append remainder all-green.

---

## 🌲 Special Data Structures

### Segment Tree (Build, Query, Update)

**Layout**: input array top, segment tree below (binary tree where each node = `[l,r]: val`).

Node labels `[l,r]: val` e.g., `[0,3]: 10` (sum of elements 0–3). Leaves: light blue. Internal nodes: purple tint.

**Build**: bottom-up; leaves map to elements → parents aggregate; show: `"[0,1]: sum(3,7)=10"`.

**Range Query `[l,r]`**: highlight query range in input (pink). At each node:

- Fully inside `[nl,nr]⊆[l,r]`: **green** — return value, no recurse
- Fully outside: **gray** — return 0, no recurse
- Partial overlap: **amber** — recurse both children, label `"partial: recurse"`
  Show aggregation propagating upward.

**Point Update**: trace root to leaf (path pink); update leaf → green; propagate up: each ancestor re-computes aggregate from children → flash green.

### Fenwick Tree / Binary Indexed Tree (BIT)

**Layout**: original array top, BIT array (1-indexed, cell 0 gray/unused) below.

Show **coverage brackets** below BIT: `BIT[4]` covers indices 1–4, `BIT[6]` covers 5–6. Show formula once: `"coverage = i & (-i)"`.

**Update (add δ to index i)**:

1. Pink on `A[i]`; walk affected BIT indices: `i, i+(i&-i), …` until `>n`
2. For each: amber on BIT cell, add δ → green; show: `"i=4+(4&-4)=4+4=8"`
3. Draw upward arrows between successive BIT cells

**Prefix Sum Query (sum of 1..i)**:

1. Walk BIT indices: `i, i-(i&-i), …` until `i=0`
2. For each: green BIT cell, accumulate: `"sum+=BIT[4]=10"`; show: `"i=4-4=0, done"`
3. Running total in panel: `"prefix_sum=10+3=13"` → final result bright green

---

## ✅ Quality Checklist (before outputting)

**General**

- [ ] Background white or off-white — no dark fills
- [ ] Steps top-to-bottom, one row each — NOT left-right box panels
- [ ] Only headings/titles use rounded-rect shapes
- [ ] All text fits inside shapes (no overflow, no clipping)
- [ ] Colors are light pastels only
- [ ] Font: 16–17px values, 13px annotations
- [ ] SVG readable at 100% zoom without scrolling
- [ ] No stray, duplicate, or dangling lines
- [ ] No overlapping text or shapes
- [ ] All connector lines computed from circle-boundary formula — no eyeballing
- [ ] Every tree horizontally centered; children at x ± 120/2^d

**Searching & Sorting**

- [ ] Linear Search: "Searching for: X" shown at top; found/not-found explicit
- [ ] Binary Search: eliminated cells gray with hatch; active range bracket shown
- [ ] Sorting: color states match table (pink=comparing, green=sorted, amber=pivot, blue=less-than-pivot)
- [ ] Heap Sort: sorted boundary (red dashed) grows from right; both phases labeled
- [ ] Counting Sort: all 3 arrays visible simultaneously; placement arrows shown
- [ ] Radix Sort: 10 bucket rows visible; each pass labeled by digit position

**Trees**

- [ ] Tree traversals: call stack on left; result array on right; postorder root greens after both children done
- [ ] Level Order: level separators in queue; all same-level nodes green simultaneously
- [ ] Morris Traversal: thread edges dashed orange; tree edges solid gray; creation AND removal both shown

**Graphs**

- [ ] Floyd-Warshall: current k prominently labeled; row k + col k amber; composition arrows shown
- [ ] Kruskal: sorted edge list shown; UF forest updates; MST weight running total shown
- [ ] Prim: PQ sorted by weight on right; visited set updated each step
- [ ] Topological Sort: in-degree table (Kahn's) OR finish-time stack (DFS) shown; cycle detection labeled
- [ ] Kosaraju: both original and transposed graphs shown; SCCs different colors; finish-time stack visible
- [ ] Tarjan: disc[] and low[] on every node; back edges amber dashed; SCC roots double-border; stack shown

**DP**

- [ ] Dependency arrows drawn from source cells; recurrence shown with actual values
- [ ] 2D DP: base cases light blue; current cell pink; source cells amber
- [ ] LIS: arrows from dp[j] to dp[i]; LIS sequence traced at end
- [ ] Kadane: current window shaded; restart decision explicit each step
- [ ] Matrix Chain: upper-triangular table; split table beside; parenthesization string at end

**Greedy**

- [ ] Huffman: PQ state after every merge; edges labeled 0/1; code table at end
- [ ] Activity Selection: timeline bar chart; sorted by finish time; green=selected, gray=rejected
- [ ] Job Sequencing: slot array shown; latest-available-slot scan visible; profit tracked
- [ ] Fractional Knapsack: ratio column shown; fill bar updates each step

**String Matching**

- [ ] Naive: pattern slides under text; shift arrow on mismatch
- [ ] KMP: LPS built in Phase 1; j jumps back using LPS (i never moves back) — annotated explicitly
- [ ] Rabin-Karp: rolling hash update formula shown; spurious hits labeled amber
- [ ] Boyer-Moore: skip jump arrow shown; bad character table referenced each shift
- [ ] Z Algorithm: Z-box [L,R] bracket on string; Z-array below; matches when Z[i]==m

**Backtracking**

- [ ] Pruned branches red-dashed, no children, WHY label always shown
- [ ] N-Queens: chessboard + decision tree side-by-side; attack shown with red lines
- [ ] Sudoku: 3×3 box borders thicker; conflict check shows row+col+box; backtrack clears cell
- [ ] Rat in Maze: 4 directions tried in order; dead-end cells revert to white; solution path listed below
- [ ] M-Coloring: color legend shown; conflict edges red; backtrack reverts vertex to white
- [ ] Dutch National Flag: three colored regions re-rendered after each step; all 3 pointer triangles labeled

**Two Pointer / Sliding Window**

- [ ] Triangle pointers ▼ above cells; window shading rect behind active cells
- [ ] Show constraint check text at each expand/contract step
- [ ] Dutch National Flag: three colored regions always visible

**Heap**

- [ ] Array AND tree in sync; parent-child brackets shown
- [ ] Both views swap simultaneously; index tracking (i=N, parent(i)=M) shown

**Trie**

- [ ] Character labels ON THE EDGE not the node
- [ ] End-of-word: double-ring circle; shared-path edges 3px
- [ ] Root labeled ∅, distinctly styled

**Union-Find**

- [ ] Root nodes are SQUARES not circles; edges point child→parent (upward arrows)
- [ ] Path compression: both passes shown; old values crossed out, new root values in green
- [ ] Forest view left + parent array right, both updated together

**Linked Lists**

- [ ] Pointer arrows from pointer compartment; prev/curr/next labeled every row
- [ ] Reversal: all pointer states visible simultaneously every row
- [ ] Floyd's: slow (pink) + fast (amber) labeled every step; step count shown; meeting node highlighted
- [ ] Merge: 3-row layout; dummy head + tail pointer shown

**Special Data Structures**

- [ ] Segment Tree: node labels show [l,r]:val; query colors: green=full-inside, gray=outside, amber=partial
- [ ] Fenwick Tree: coverage brackets below BIT; i&(-i) formula shown once; update propagation arrows shown
