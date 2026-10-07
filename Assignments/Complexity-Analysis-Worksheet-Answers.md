# Complexity Analysis Worksheet — Answer Key

Instructor-only. Don't link this from the lesson or hand it out — it's for checking student answers, not for students to self-check before they've traced it themselves.

## Part 1

| # | Time | Space | Why |
|---|------|-------|-----|
| 1. `reverseString` | O(n) | O(n) | Loops once over `s`; builds a new `result` string of length n. |
| 2. `hasDuplicateHashMap` | O(n) | O(n) | Single pass; `seen` can grow to hold up to n entries. |
| 2b. `hasDuplicateNestedLoop` | O(n²) | O(1) | Nested loop checks every pair; no extra structure, just loop counters. |
| 3. `isPalindrome` | O(n) | O(1) | Single pass inward with two pointers; only `left`/`right` vars, no extra structure. |
| 4. `binarySearch` | O(log n) | O(1) | Halves the search range each iteration; only `low`/`high`/`mid` vars. |
| 5. `allPairs` | O(n²) | O(n²) | Nested loop *and* the output array itself grows to n² entries. |

**Caveat on #1:** taught as O(n) time at this level, which is the right answer to accept. In reality, `result += s[i]` in a loop can be O(n²) in engines where strings are immutable and each `+=` reallocates. Don't volunteer this unless a student pushes on it — it's a simplification, not an error, for this course's level.

## Part 2 — Time-Space Tradeoff

1. **2** (hash map) is faster — O(n) vs O(n²). **2b** uses less memory — O(1) vs O(n).
2. Expected answer: "I can trade memory for speed — using a hash map gets this to O(n) time at the cost of O(n) space."
3. Prefer 2b when memory is genuinely scarce (embedded/constrained environment), or when n is small enough that O(n²) time doesn't matter but any extra allocation isn't worth it.

## Part 3 — Sketch It

No fixed answer. Check against the reference curves given at the top of the worksheet — flag anyone who draws O(log n) rising as steeply as O(n), or O(n log n) as steep as O(n²); those are the two mix-ups to watch for.
