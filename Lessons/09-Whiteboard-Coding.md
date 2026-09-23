# Whiteboard Coding

## Learning Outcomes

By the end of this class,  you should be able to...

1. Recognize the importance of manually testing your code before running it with an interpreter.
1. Use a variable table to keep track of program state at any given point in your program.
1. Recognize when a problem calls for a hash map, and explain why it beats the brute-force alternative.

## Pattern Focus: Hash Maps (8 min)

A hash map is the right tool when a problem needs fast lookup, needs to count how often something appears, or needs to check whether something's been seen before. Watch for phrasing like:

- "Have you seen this value before?"
- "How many times does X appear?"
- "Find a pair/group that adds up to / matches something."

The tell: a brute-force version of these needs a nested loop (O(n²)) to compare every item against every other item. A hash map trades that for one pass and O(1) lookups, at the cost of extra memory — that trade-off is worth saying out loud in an interview.

**"Hash map" is jargon for something you've already used.** In JS, it's a plain object (or `Map`). In Python, it's a `dict`. Same key → value lookup you've used for months, just with new vocabulary for the interview:

```js
// JS — counting how many times each value appears
const counts = {};
for (const num of nums) {
  counts[num] = (counts[num] || 0) + 1;
}
// counts[5] is now an O(1) lookup, not a loop through nums
```

```python
# Python — same idea with a dict
counts = {}
for num in nums:
    counts[num] = counts.get(num, 0) + 1
# counts[5] is now an O(1) lookup, not a loop through nums
```

Two Sum is the clearest example: brute force checks every pair (`nums[i] + nums[j] == target`, O(n²)). The hash map version stores each number as a key while looping once — for each `num`, check if `target - num` is already a key you've seen. One pass, O(n).

## Code-Tracing Set

Each problem below has exactly one bug. All three use a hash map — the bug is never "wrong pattern," it's an off-by-one, a wrong comparison, or a typo in how the map is used. That's deliberate: this is what hash map bugs actually look like in practice.

### 1. Two Sum

> Given an array of integers `nums` and an integer `target`, return the indices of the two numbers that add up to `target`.
>
> Trace it with `nums = [3, 2, 4]`, `target = 6` — a canonical example like `[2, 7, 11, 15]`/`9` won't expose this bug, so use the input given here for your "good/normal" case.

```js
function twoSum(nums, target) {
  const seen = {};
  for (let i = 0; i < nums.length; i++) {
    seen[nums[i]] = i;
    const complement = target - nums[i];
    if (seen[complement] !== undefined) {
      return [seen[complement], i];
    }
  }
  return [];
}
```

### 2. Valid Anagram

> Given two strings `s` and `t`, return whether `t` is an anagram of `s`.

```js
function isAnagram(s, t) {
  const counts = {};
  for (const char of s) counts[char] = (counts[char] || 0) + 1;
  for (const char of t) counts[char] = (counts[char] || 0) - 1;
  for (const key in counts) {
    if (counts[key] > 0) return false;
  }
  return true;
}
```

### 3. First Unique Character

> Given a string `s`, return the index of the first character that appears exactly once. Return `-1` if there is none.

```js
function firstUniqChar(s) {
  const counts = {};
  for (const char of s) {
    counts[char] = (counts[char] || 0) + 1;
  }
  for (let i = 0; i < s.length; i++) {
    if (counts[s[i] === 1]) return i;
  }
  return -1;
}
```

Working in Python instead? Translate whichever problem you pick — same bug, same logic, `dict` in place of the object.

## Activity: Code Tracing

1. Choose one problem from the [Code-Tracing Set](#code-tracing-set) above. Each solution contains at least one bug that you will be tasked with fixing.
1. Read over the problem statement and the code. **Before tracing, say out loud what pattern the code is using and why.**
1. Create a “good/normal” input for the function.
1. Use a variable table to trace through the code to find the error — **no AI tools, no running the code yet.**
1. Use [Python Tutor](https://pythontutor.com) to check your work.
1. If you spot the error right away, still go through the steps of the variable table!
1. Submit your solution when finished.

This is the one skill an AI assistant can't do for you live on a whiteboard or shared screen: interviewers watch how you trace state by hand, because it's exactly what breaks down when someone has only ever debugged with a tool doing it for them.

## Homework

1. From the [Tiered Problem Bank](../Assignments/Tiered-Problem-Bank.md), solve [Two Sum](https://leetcode.com/problems/two-sum/) and [Valid Anagram](https://leetcode.com/problems/valid-anagram/) (Tier 1, both hash map problems). Add a one-line comment at the top of each solution naming the pattern and why it fits.
1. After you’ve written the code, use a variable table to trace through the code. Check your work using [Python Tutor](https://pythontutor.com).
1. Commit your solution code and test cases to a GitHub repo and submit the link via the course tracker.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.