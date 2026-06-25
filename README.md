# DSA Visualizer 🧠✨

> **An AI-driven SVG generator that visually traces Data Structures and Algorithms step-by-step.**

---

# 📖 The Origin Story

## A Student's Perspective

If you're reading this, you probably know the grind.

As an ICT student staring down a list of **90+ LeetCode problems**, trying to understand everything from **Binary Search** and **Hashing** to full-blown **Dynamic Programming**, I hit a cognitive wall.

Reading about an algorithm is one thing.

Mentally tracing pointer swaps in a **Doubly Linked List**, keeping track of recursion stacks in **N-Queens**, or visualizing a **Sliding Window** is something completely different.

I filled notebooks with messy diagrams, crossed out array indices, and constantly lost track of where my `lo` and `hi` pointers were.

I wanted a tool that didn't just **explain** the code.

I wanted one that could **show the algorithm thinking.**

I tried asking AI to generate diagrams.

The result?

- Overlapping SVGs
- Missing intermediate steps
- Implicit logic
- Inconsistent layouts

After months of experimentation, prompt engineering, trial and error, and repeatedly refining the constraints, I built **DSA Visualizer**.

It is designed to be an educational visualization engine.

- No skipped steps
- No hidden variables
- No implied state
- No messy layouts

Just clean, mathematically centered SVG diagrams that trace every algorithm exactly as it executes.

---

# 🏗️ Architecture & Core Workflow

This is **not** just a prompt.

It is a modular visualization system engineered to force an AI model into a deterministic workflow before drawing anything.

Before generating even a single SVG element, the engine must:

1. Execute the algorithm mentally.
2. Detect the algorithm pattern.
3. Decide the visualization strategy.
4. Determine step granularity.
5. Generate sequential SVG snapshots.

---

## Workflow

```
Input
   │
   ▼
Understand Algorithm
   │
   ▼
Execute Mentally
   │
   ▼
Detect Pattern
   │
   ▼
Choose Visualization Module
   │
   ▼
Generate Step-by-Step SVG
```

---

# ⭐ The Four Pillars

## 1. Algorithmic Comprehension

Execute first.

Draw later.

Nothing is visualized until the algorithm has been fully understood.

---

## 2. Cognitive Load Reduction

Every important variable is explicitly displayed.

Example:

```
lo = 2
hi = 7
mid = 4
sum = 18
```

Nothing is left for the reader to infer.

---

## 3. Line-wise Sequencing

One logical operation equals one frame.

Never combine:

- comparison + swap
- recursion + return
- pointer movement + insertion

Each action gets its own visualization.

---

## 4. Precision Aesthetics

Every SVG follows strict engineering rules.

- mathematically centered
- equal spacing
- zero overlaps
- exact edge intersections
- soft educational colors

---

# 🎨 Visual Language

The same colors are used across every algorithm.

| Color | Hex | Meaning |
|-------|------|---------|
| 🩷 Pink | `#F5A0C5` | Active operation |
| 🟩 Green | `#90E090` | Completed / Sorted / Final |
| 🟨 Amber | `#F5D0A0` | Future / Heap / Linked List |
| 🟦 Light Blue | `#A8D0F0` | Structural elements |
| 🟥 Dashed Red | `#E88080` | Pruned / Invalid / Backtracked |
| ⬜ Gray | `#D0D0D0` | Ignored / Eliminated |

---

# 🧩 Modular Architecture

The project is divided into two major components.

```
DSA Visualizer
│
├── SKILL.md
│
└── references/
    ├── linked-lists.md
    ├── dynamic-programming.md
    ├── recursion-backtracking.md
    ├── trees-graphs.md
    ├── heaps.md
    ├── union-find.md
    ├── sorting-searching.md
    ├── two-pointer.md
    └── tries.md
```

---

# 🧠 Core Engine (`SKILL.md`)

The core engine is responsible for:

- overall SVG layout
- title formatting
- step numbering
- diagram flow
- precision engineering rules
- module routing

It ensures every visualization follows the exact same structure regardless of algorithm.

---

# 📚 Reference Modules

## `linked-lists.md`

Designed specifically for pointer-heavy algorithms.

Features:

- 80×36 px nodes
- split pointer compartments
- explicit `prev`, `curr`, `next`
- Floyd Cycle Detection
- Reverse Linked List
- Merge Lists

---

## `dynamic-programming.md`

Supports:

- 1D DP
- 2D DP
- Dependency arrows
- Cell highlighting
- Transition visualization

Perfect for:

- Knapsack
- LCS
- Coin Change
- LIS

---

## `recursion-backtracking.md`

Visualizes:

- recursion tree
- current state
- recursion stack
- pruning

Supports:

- N Queens
- Sudoku
- Permutations
- Combination Sum

Pruned branches are drawn using dashed red edges.

---

## `trees-graphs.md`

Supports:

- DFS
- BFS
- Dijkstra
- Bellman Ford
- Topological Sort

Uses mathematical spacing:

```
x ± (120 / 2^depth)
```

to prevent node overlap.

---

## `heaps.md`

Uses synchronized dual visualization.

Tree View

↓

Array View

Both remain synchronized throughout heap operations.

Ideal for:

- Heapify
- Insert
- Delete
- Heap Sort

---

## `union-find.md`

Shows two synchronized views.

Left:

- Disjoint Set Forest

Right:

- `parent[]`

Supports:

- Union
- Find
- Rank
- Path Compression

---

## Other Modules

### `two-pointer.md`

- Sliding Window
- Fast & Slow Pointer
- Two Sum

Includes highlighted active ranges.

---

### `sorting-searching.md`

Supports:

- Bubble Sort
- Merge Sort
- Quick Sort
- Binary Search

Shows pivots, partitions, swaps, and recursion.

---

### `tries.md`

Visualizes:

- Prefix Tree
- Insert
- Search
- Delete

Word endings are explicitly marked.

---

# 🛠️ Evolution

The visualizer evolved through multiple major iterations.

---

## Phase 1 — The Messy Beginning

Problems:

- overlapping edges
- random layouts
- skipped steps
- inconsistent arrays

---

## Phase 2 — Step Granularity

A strict rule was introduced:

> **One logical operation = One visualization**

This dramatically improved readability.

---

## Phase 3 — Formatting

Engineering constraints were added.

Examples:

- monospace fonts
- exact node sizes
- 48×48 px arrays
- fixed spacing
- centered layouts

---

## Phase 4 — Modularization

A single giant prompt became impossible to maintain.

The project was split into:

- `SKILL.md`
- `references/*.md`

Each module now specializes in one family of algorithms.

---

# 📐 Reference Design Library

To maintain consistency across all generated visualizations, the engine should first consult the existing SVG design library before creating a new layout.

## Guiding Principle

> **Reuse an existing design whenever the requested algorithm shares the same underlying structure.**

The visualizer should adapt the existing SVG by updating:

- node values
- labels
- colors
- highlights
- arrows
- variable states
- active regions

while **preserving the original geometry, spacing, alignment, and overall layout**.

Only generate an entirely new layout when no suitable reference exists.

---

## Current Reference Templates

### 🌳 Trees

Use the existing tree layouts as the foundation for all tree-based algorithms.

Applicable algorithms include:

- Binary Tree Traversal
- BST Operations
- AVL Tree
- Red Black Tree
- Segment Tree
- Fenwick Tree
- Heap Trees
- Huffman Tree
- Expression Tree
- Lowest Common Ancestor
- Tree DP

Available references:

- Full Binary Tree (7 Nodes)
- Complete Binary Tree
- Skewed Tree
- Unbalanced Tree A
- Unbalanced Tree B
- Multi-level Tree (12 Nodes)

---

### 🔗 Linked Lists

Reuse linked list templates for all pointer-based algorithms.

Applicable algorithms:

- Reverse Linked List
- Reverse Between
- Merge Lists
- Merge K Lists
- Detect Cycle
- Remove Nth Node
- Palindrome List
- Odd Even List
- Rotate List
- Partition List

Available references:

- Singly Linked List
- Doubly Linked List
- Circular Linked List

---

### 📚 Stack

Use the stack template whenever a LIFO structure is involved.

Applicable algorithms:

- Valid Parentheses
- Min Stack
- Next Greater Element
- Monotonic Stack
- Largest Rectangle
- Evaluate Postfix
- Infix to Postfix

Reference:

- Stack (Peek)

---

### 🚶 Queue

Reuse the queue layout for FIFO-based algorithms.

Applicable algorithms:

- Queue Operations
- BFS
- Level Order Traversal
- Sliding Window Queue
- Deque
- Circular Queue

Reference:

- Queue (FIFO)

---

### 🕸️ Graphs

Graph layouts should be reused depending on graph type.

Applicable algorithms:

- DFS
- BFS
- Dijkstra
- Bellman Ford
- Floyd Warshall
- Prim
- Kruskal
- Topological Sort
- SCC
- Cycle Detection
- Bipartite Checking
- Union Find Visualization

Available references:

- Directed Graph
- Undirected Graph
- Weighted Graph
- Complete Graph
- DAG
- Bipartite Graph

---

## Adaptation Rules

When using a reference design:

- Preserve overall layout.
- Preserve spacing and alignment.
- Preserve edge routing.
- Preserve node positioning.
- Preserve SVG proportions.

Only modify:

- node contents
- colors
- active highlights
- labels
- arrows
- variable annotations
- state indicators

---

## When No Reference Exists

If no suitable template exists:

1. Detect the underlying data structure.
2. Follow the corresponding module rules (`references/*.md`).
3. Generate a new SVG using the project's engineering standards.
4. Ensure the newly generated layout remains stylistically consistent with the existing design library.

---

## Long-Term Goal

The reference library should continuously expand over time.

Whenever a high-quality visualization is created that represents a reusable structure, it should be added to the library so future visualizations can inherit its layout instead of generating one from scratch.

This ensures:

- consistent appearance
- predictable layouts
- improved readability
- reduced hallucinations
- faster and more reliable SVG generation

---
# 🎯 Design Goals

- Teach algorithms visually
- Reduce cognitive load
- Eliminate skipped steps
- Standardize every visualization
- Produce presentation-quality SVGs

---

# 💡 Philosophy

> **"The best way to understand an algorithm is to trace it. If you're tired of tracing it on paper, let this draw it for you."**

---

# 👨‍💻 Author

**Rushil Sureja**
