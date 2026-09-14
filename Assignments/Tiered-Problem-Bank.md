# Tiered Problem Bank & Skill Diagnostic

Problems are grouped into 4 tiers, from confidence-building basics through real hard-level interview questions. Two uses:

1. **Ongoing practice** — instead of hunting for your own problems, work from your current tier. Move up once a tier feels comfortable, not before.
2. **One-time diagnostic** — see [Diagnostic Session](#diagnostic-session) below.

No solutions provided — solve in whichever language you're more comfortable with, same as a real interview. Each problem lists what skill it's actually testing, which matters more than the difficulty label: someone stuck on Tier 2's sliding-window problem but fine with Tier 3's hash-based one has a specific, fixable gap, not a general "behind" problem.

## Tier 0: Foundations

Not really interview questions — these are floor-level confidence checks. If one of these is genuinely hard, start here, not with Tier 1.

- **Sum of an array** — *Tests: basic iteration*
- **Reverse a string** — *Tests: basic iteration, string/array handling*
- **Count vowels in a string** — *Tests: conditionals, iteration*
- **FizzBuzz** — *Tests: conditionals, modulo*
- **Check if a number is prime** — *Tests: loops, basic math reasoning*

## Tier 1: Easy

- [Two Sum](https://leetcode.com/problems/two-sum/) — *Tests: hash maps*
- [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) — *Tests: stacks*
- [Valid Anagram](https://leetcode.com/problems/valid-anagram/) — *Tests: hash maps / counting*
- [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) — *Tests: two pointers*
- [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) — *Tests: linked list pointer manipulation*
- [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) — *Tests: single-pass tracking*

## Tier 2: Moderate

- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) — *Tests: sliding window*
- [Group Anagrams](https://leetcode.com/problems/group-anagrams/) — *Tests: hash maps, grouping*
- [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) — *Tests: heaps / selection*
- [3Sum](https://leetcode.com/problems/3sum/) — *Tests: two pointers, dedup logic*
- [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) — *Tests: trees, BFS*
- [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) — *Tests: dynamic programming (Kadane's)*

## Tier 3: Hard

- [Merge Intervals](https://leetcode.com/problems/merge-intervals/) — *Tests: sorting, interval logic*
- [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) — *Tests: 2D dynamic programming*
- [Course Schedule](https://leetcode.com/problems/course-schedule/) — *Tests: graphs, topological sort/cycle detection*
- [LRU Cache](https://leetcode.com/problems/lru-cache/) — *Tests: design, combining a hash map with a doubly linked list*
- [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) — *Tests: two pointers or stack, edge-case-heavy*

## Diagnostic Session

### Part A: Take-Home Solve

Work through the tiers **in order**, starting at Tier 0, even if it feels too easy — speed through the ones that are trivial. Keep going until you hit a problem you genuinely can't solve, or can only solve partway.

**Stopping is the data, not a failure.** Where you stop tells your instructor exactly where to focus — that's the point of this being a diagnostic, not a test to pass.

For each problem you complete, note:
- Which tier and problem
- Roughly how long it took
- Whether you got it working cleanly, got it working messily, or didn't finish

### Part B: In-Class Explain-Back (15-20 min, next class)

Same drill as [Lesson 5](../Lessons/05-AI-Assisted-Coding-and-Interviewing.md)'s Explain-It-Back, applied here:

1. Pair up (assigned or self-select).
1. Swap your **highest-tier completed** solution with your partner.
1. Without asking them anything first, read their code and prepare to explain what it does, in your own words, plus its time/space complexity.
1. Present your explanation to your partner. They grade you on accuracy — did you actually understand it, or just get it working?
1. Switch, repeat with your partner explaining yours back to you.

If you can't explain your own highest-tier solution, that's more useful diagnostic information than the fact that it ran.

### Recording Results

Submit via the [Assignment Link Submission form](https://forms.gle/o2rLExrzRuJWi7Px7) — dropdown "Tiered Problem Bank — Diagnostic":
- Link to your solution code
- Highest tier you completed cleanly
- Where you got stuck (if anywhere) and on what specifically (the problem name, not just "it was hard")

## Instructor Notes

- Read results by *where* someone stopped, not just *how far*. Two students both stuck at Tier 2 for different reasons (one can't do hash maps at all, one can't do sliding window) need different support, even though they look identical on a difficulty scale alone.
- Worth using this to deliberately pair students for future in-class breakouts — pairing someone strong in a skill area with someone stuck on exactly that area is more useful than random pairing.
- Going forward, this bank can replace the generic "find 2 new problems on LeetCode/Exercism" homework instruction in later lessons — not wired in yet, flag if you want that done.
