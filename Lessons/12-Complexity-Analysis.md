# Complexity Analysis

### Slides

*(Add link to slide deck)*

## Warm-Up

Define what each of the following Big O complexity classes represents, and sketch a rough growth curve for each: O(1), O(log n), O(n), O(n log n), O(n²).

## Pattern Focus: Two Pointers & Sliding Window (8 min)

Two pointers (and its sliding-window variant) is the pattern that turns an O(n²) nested-loop brute force into a single O(n) pass — which makes it the natural pairing for a Big O lesson. Watch for:

- Working on a **sorted array** and looking for a pair/triple that meets some condition (move pointers from both ends inward).
- Working on a **substring/subarray** and tracking a running window that grows and shrinks (sliding window).

When you catch yourself about to write a nested loop over an array or string, stop and ask: could one pointer (or two, moving toward each other) do this in one pass instead?

## Activity 1: Worksheet

Make a copy of the complexity analysis worksheet *(add link)*. Analyze each of the problems on the worksheet and provide the Big O for runtime and space complexity.

## Activity 2: Rapid-Fire Breakouts

1. Find a partner and choose one of the below problems. You will go through the problem as if you were in an actual interview. Before coding, state out loud which pattern you're using (hash map, two pointer, sliding window, or other) and why. Your partner will play the interviewer, and will have a checklist to make sure you're following the proper steps, including naming the pattern.
1. Swap roles and do the other problem.

**Pay attention to time/space complexity.** Write notes on the back of the checklist for improvements in this particular area.

Practice Problems:

1. Given a number k and a list of numbers, find the k largest elements in the list and return them in sorted order.
1. Given a number k and a list of numbers, find the kth most common element. *(Pattern: hash map — review from Lesson 9.)*
1. Given a string, find the length of the longest substring without repeating characters. *(Pattern: sliding window.)*
1. Given two sorted arrays, merge them into a single sorted array. *(Pattern: two pointers.)*

## Homework

- From the [Tiered Problem Bank](../Assignments/Tiered-Problem-Bank.md), solve [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) (Tier 2, sliding window) and [3Sum](https://leetcode.com/problems/3sum/) (Tier 2, two pointers).
- Analyze the time and space complexity of your solution code and annotate this in comments, along with a one-line note naming the pattern used.
- Commit your solution code and annotations to a GitHub repo and submit the link via the course tracker.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.