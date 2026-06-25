# 🎨 DSA Visualizer

**A Claude Skill that turns any algorithm into a diagram you can actually learn from.**

No animations. No black boxes. No "trust me, it works." Just the exact moment a swap happens, a pointer flips, or a branch gets pruned — drawn out, step by step, until the whole algorithm is laid bare in front of you.

---

## What is this?

`dsa-visualizer` is a [Claude Skill](https://www.anthropic.com) — a set of instructions that teaches Claude how to generate clean, pedagogically-sequenced SVG diagrams for Data Structures & Algorithms on demand. Ask Claude to "show me how merge sort works" or "draw the recursion tree for this," and instead of a wall of text, you get a diagram built specifically to teach *that* concept, *that* way.

It's not a generic diagram generator. It's opinionated about how algorithms should be taught visually — and it enforces that opinion rigorously, every single time.

## The problem it solves

Most algorithm explanations fall into one of two traps:

- **Pure code** — technically complete, but you have to mentally execute every line to understand what's actually happening to the data.
- **A single before/after image** — shows you the destination, skips the journey. The *interesting* part — the comparison, the swap, the branch that got pruned — never makes it onto the page.

`dsa-visualizer` refuses both shortcuts. Every diagram it produces is a sequence of snapshots, one per meaningful operation, so you can watch the algorithm *think*.

---

## Design Philosophy — Four Pillars

Every diagram, regardless of topic, is built on the same four non-negotiable principles:

| Pillar | What it means |
|---|---|
| 🧠 **Algorithmic Comprehension** | The algorithm is mentally executed in full *before* a single shape is drawn. The pattern (DFS, two-pointer, DP table…) is identified first — the drawing comes second. |
| 🪶 **Cognitive-Load Reduction** | Every step is one snapshot in time. Variable and index states are always shown explicitly. You're never asked to infer hidden state. |
| 📏 **Line-wise Step Sequencing** | Steps flow top → bottom, one per row, never crammed into competing box panels. One row = one logical operation, clearly labeled. |
| ☀️ **Light Aesthetics** | Soft pastels only — greens, blues, pinks, peach tints — on a white or near-white background. Nothing dark, nothing loud. |

---

## What it can visualize

| Category | Topics |
|---|---|
| **Sorting & Searching** | Bubble, Selection, Insertion, Merge, Quick Sort · Binary Search |
| **Linked Lists** | Traversal · Reversal (full pointer-state view) · Floyd's cycle detection · Merging two sorted lists |
| **Trees & Graphs** | DFS / BFS / BST operations · Dijkstra & Bellman-Ford shortest path · Weighted graphs |
| **Heaps** | Insert, extract-min/max, heapify — array and tree views kept in sync |
| **Tries** | Insert, search, prefix search — with character-labeled edges |
| **Union-Find** | Union, find, and path compression, shown as a forest with a parallel parent array |
| **Dynamic Programming** | 1D and 2D table-filling, with dependency highlighting |
| **Two Pointer / Sliding Window** | Window growth and pointer movement, shaded inline |
| **Recursion & Backtracking** | Recursion trees · N-Queens, permutations, subsets — with pruned branches clearly marked |

If it's a core DSA concept, there's a dedicated visual grammar for it — not a generic box-and-arrow fallback.

---

## The Visual Language

Every diagram speaks the same color language, so once you've read one, you can read them all:

| Color | Meaning |
|---|---|
| 🟦 Light blue | Headings, unvisited nodes, structural elements |
| 🟢 Green | Visited, sorted, reversed/done, or successfully completed |
| 🩷 Pink | Currently active — the comparison, swap, or branch happening *right now* |
| 🟡 Amber/Yellow | Heap elements, linked-list nodes |
| 🟠 Peach | Stack frames, backtracked states |
| ⬜ Gray | Eliminated, untouched, or not-yet-reached |
| 🔴 Red (dashed) | Pruned or invalid — explicitly ruled out |

No element's meaning ever depends on you remembering a legend from three diagrams ago.

---

## Anatomy of a Diagram

Every output follows the same predictable skeleton:

```
┌─────────────────────────────┐
│   Title (light blue)        │
└─────────────────────────────┘
          ↓
  Step 1 — description, state, variables
          ↓
  Step 2 — description, state, variables
          ↓
         ...
          ↓
┌─────────────────────────────┐
│   Final State (light green) │
└─────────────────────────────┘
```

Each step row carries everything you need and nothing you don't: a colored step number, a short action label, the data structure's current state inline, and any relevant variables (`lo=2, mid=4, hi=7`) — never hidden, never implied.

---

## Precision Engineering

This is the part most diagram tools skip, and it's where most of this skill's iteration time actually went.

- **Edges touch nodes exactly.** Every connector between two circular nodes is computed from real circle-boundary trigonometry — not eyeballed coordinates — so there's never a visible gap or an overlapping line.
- **Trees are always centered.** The root sits at the exact horizontal center of the canvas, with children fanned out symmetrically beneath it. No lopsided, off-balance trees.
- **Weighted edge labels never sit on the line.** They're offset perpendicular to the edge, on a small white pill, so they stay legible even when edges cross.
- **Every node always shows its full pointer state.** A linked-list reversal, for example, never hides a node's outgoing arrow mid-explanation — done links, the active flip, and untouched links are all visible at once, color-coded.
- **Nothing stray survives.** Every line, every circle, every shape is required to be load-bearing. Leftover artifacts from an earlier draft of the same diagram get deleted before anything ships.

## Quality Bar

Before any diagram is considered finished, it has to clear a non-negotiable checklist — no dark backgrounds, no overflowing text, no partial state, no overlapping shapes, no stray lines, legible fonts at every size, and a tree/graph layout that's been mathematically verified, not approximated.

---

## Try it

You don't need special syntax — just ask, naturally:

> *"Show me how merge sort works"*
> *"Visualize heapify on this array"*
> *"Draw a trie for these words"*
> *"Trace the N-Queens backtracking for n=4"*
> *"Walk me through reversing this linked list"*
> *"Show union-find with path compression"*

If a diagram would teach the concept better than a paragraph would, this skill steps in automatically.

---

*Built iteratively, refined diagram by diagram, with a fairly stubborn insistence that lines should touch the things they're connecting to.*
