# Complexity Analysis

### Slides

## ELI5: What Is Time Complexity? (8 min)

Forget seconds and milliseconds for a minute. Big O isn't about how fast your computer is — it's about **how much more work you have to do when the input gets bigger.**

Picture three ways to find your name:

- **A sticky note with your name on it, on your own monitor.** One glance, done. Doesn't matter if the office has 10 people or 10,000 — still one glance. That's **O(1)**: constant, input size doesn't matter.
- **An unsorted sign-in sheet with everyone's name on it, in no particular order.** You scan row by row until you find yours. 10 people, up to 10 rows. 10,000 people, up to 10,000 rows. The work grows exactly as fast as the input. That's **O(n)**.
- **Checking a seating chart for duplicate names by comparing every name against every other name.** 10 people means roughly 10×10 = 100 comparisons. 100 people means 100×100 = 10,000. Double the input, and the work doesn't double — it roughly quadruples. That's **O(n²)**, and the numbers grow scary fast:

| Input size (n) | O(n) work | O(n²) work |
| -------------- | --------- | ---------- |
| 10 | 10 | 100 |
| 100 | 100 | 10,000 |
| 1,000 | 1,000 | 1,000,000 |

Same growth in input, wildly different growth in work. That gap is the entire reason this topic exists — it's the difference between code that still runs fine at real-world scale and code that quietly falls over.

## Active Learning: Count the Operations (15 min)

Don't guess the Big O — count it. Below are four short functions. For each one, trace through by hand with `n = 4`, `n = 8`, and `n = 16`, and tally how many times the marked line actually runs. Fill in the table as you go, *then* match each one to a complexity class.

**A**

```js
function first(nums) {
  return nums[0]; // <- count this line
}
```

**B**

```js
function sumAll(nums) {
  let total = 0;
  for (let i = 0; i < nums.length; i++) {
    total += nums[i]; // <- count this line
  }
  return total;
}
```

**C**

```js
function hasPair(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) return true; // <- count this line
    }
  }
  return false;
}
```

**D**

```js
function countHalvings(n) {
  let steps = 0;
  while (n > 1) {
    n = Math.floor(n / 2); // <- count this line
    steps++;
  }
  return steps;
}
```

| Function | n=4 | n=8 | n=16 | Complexity class |
| -------- | --- | --- | ---- | ----------------- |
| A | | | | |
| B | | | | |
| C | | | | |
| D | | | | |

Once your table's filled in: which function barely notices `n` growing? Which one explodes? If `n` were 1,000,000, which one would you be worried about shipping to production?

<details>
<summary>Answers (check after you've filled in your own table)</summary>

A: 1, 1, 1 — O(1). B: 4, 8, 16 — O(n). C: 16, 64, 256 — O(n²). D: 2, 3, 4 — O(log n), since halving `n` repeatedly reaches 1 in roughly log₂(n) steps.

</details>

## Check for Understanding (5 min)

Now that you've counted real operations, define each of these in your own words and sketch a rough growth curve for each: O(1), O(log n), O(n), O(n log n), O(n²). (We didn't cover O(n log n) above — it shows up in sorting. Think of it as "like O(n), but each of the n elements costs you an O(log n) step" — worse than O(n), nowhere near as bad as O(n²).)

## Pattern Focus: Two Pointers & Sliding Window (8 min)

Function C above — the nested loop checking every pair — is exactly the O(n²) shape to watch for. Two pointers (and its sliding-window variant) is the pattern that turns that kind of brute force into a single O(n) pass, which is why it's the natural pairing for this lesson. Watch for:

- Working on a **sorted array** and looking for a pair/triple that meets some condition (move pointers from both ends inward).
- Working on a **substring/subarray** and tracking a running window that grows and shrinks (sliding window).

When you catch yourself about to write a nested loop over an array or string, stop and ask: could one pointer (or two, moving toward each other) do this in one pass instead?

## Activity 1: Worksheet (35 min)

Work through the [Complexity Analysis Worksheet](../Assignments/Complexity-Analysis-Worksheet.md): time and space complexity for 5 fresh functions, a direct time-space tradeoff comparison, and your own growth-curve sketches.

## Activity 2: Rapid-Fire Breakouts

1. Find a partner and choose one of the below problems. You will go through the problem as if you were in an actual interview. Before coding, state out loud which pattern you're using (hash map, two pointer, sliding window, or other) and why. Your partner will play the interviewer, and will have a checklist to make sure you're following the proper steps, including naming the pattern.
1. Swap roles and do the other problem.

**Pay attention to time/space complexity.** Write notes on the back of the checklist for improvements in this particular area.

Practice Problems:

1. Given a number k and a list of numbers, find the k largest elements in the list and return them in sorted order.
1. Given a number k and a list of numbers, find the kth most common element. *(Pattern: hash map — review from Lesson 9.)*
1. Given a string, find the length of the longest substring without repeating characters. *(Pattern: sliding window.)*
1. Given two sorted arrays, merge them into a single sorted array. *(Pattern: two pointers.)*

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.

## Homework

- From the [Tiered Problem Bank](../Assignments/Tiered-Problem-Bank.md), solve [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) (Tier 2, sliding window) and [3Sum](https://leetcode.com/problems/3sum/) (Tier 2, two pointers).
- Analyze the time and space complexity of your solution code and annotate this in comments, along with a one-line note naming the pattern used.
- Commit your solution code and annotations to a GitHub repo and submit the link via the course tracker.