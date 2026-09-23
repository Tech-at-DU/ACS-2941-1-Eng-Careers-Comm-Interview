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
>
> Trace it with `s = "ab"`, `t = "abc"` — a false-case guess like `"rat"`/`"car"` won't expose this bug, so use the input given here for your "good/normal" case.

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
>
> Trace it with `s = "leetcode"` (expected `0`). An input with no unique character, like `"aabb"`, returns the right answer by accident and won't expose this bug.

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

## Refresher: What a Variable Table Actually Looks Like

If it's been a while — a variable table is just a table you fill in by hand, one row per step, showing what every variable holds *at that exact point* in the code. No running it, no guessing: you write down what you're sure of, line by line.

Worked example, tracing this (correct, no bug) function with `s = "aba"`:

```js
function countChar(s) {
  const counts = {};
  for (const char of s) {
    counts[char] = (counts[char] || 0) + 1;
  }
  return counts;
}
```

| Step | Line executed | `char` | `counts` before | `counts` after |
| ---- | -------------- | ------ | ---------------- | --------------- |
| 1 | `const counts = {}` | — | — | `{}` |
| 2 | `counts[char] = ...` | `'a'` | `{}` | `{a: 1}` |
| 3 | `counts[char] = ...` | `'b'` | `{a: 1}` | `{a: 1, b: 1}` |
| 4 | `counts[char] = ...` | `'a'` | `{a: 1, b: 1}` | `{a: 2, b: 1}` |
| 5 | `return counts` | — | — | `{a: 2, b: 1}` |

Return value: `{a: 2, b: 1}`.

That's it — one row every time a line runs that changes state, tracking every variable that's live at that point. For today's three problems, that means a column for the loop variable and a column for the hash map (`seen`/`counts`), updated row by row, so a bug shows up as the exact row where the value stops matching what you worked out by hand beforehand.

**Strategy for finding the bug:**

- Know the expected output *before* you trace — pick an input, work out the right answer by hand first, then compare against what the code actually produces.
- Trace every line, don't skim to the part that "looks suspicious." The bug is often in a line that looks fine at a glance.
- For a hash map specifically, check the *order* of operations at each step: does this line read from the map or write to it? Is it doing that before or after the check that depends on it? Most hash map bugs are an insert and a check happening in the wrong order, not a wrong data structure.
- If your first input doesn't expose a mismatch, don't assume the code is correct — try an input with a repeated value or a value that could match itself, since those are exactly where insert/check-order bugs hide.
- Found a mismatch? Don't guess-fix. Go back to the variable table and find the exact line where the traced value first diverges from what you expected.

## Activity: Code Tracing

1. Choose one problem from the [Code-Tracing Set](#code-tracing-set) above. Each solution contains at least one bug that you will be tasked with fixing.
1. Read over the problem statement and the code. **Before tracing, say out loud what pattern the code is using and why.**
1. Create a “good/normal” input for the function.
1. Use a variable table to trace through the code to find the error — **no AI tools, no running the code yet.**
1. Check your work with [Python Tutor](https://pythontutor.com) or Node (see [Checking Your Work](#checking-your-work) below).
1. If you spot the error right away, still go through the steps of the variable table!

This is the one skill an AI assistant can't do for you live on a whiteboard or shared screen: interviewers watch how you trace state by hand, because it's exactly what breaks down when someone has only ever debugged with a tool doing it for them.

### Checking Your Work

Only after you've finished your trace by hand. The problems are written in JS, so you have two options, neither requires rewriting the code:

**Option 1: Node.** Save the function to a file, add a call at the bottom that prints the result, and run it:

```js
// twosum.js
function twoSum(nums, target) {
  // ...the function from above, with your fix...
}

console.log(twoSum([3, 2, 4], 6));
```

```bash
node twosum.js
```

Compare the printed output to what your variable table predicted. Try the input you traced *and* one or two others.

**Option 2: Python Tutor.** [pythontutor.com](https://pythontutor.com) supports JavaScript — on the "Write code" page, change the language dropdown from Python to **JavaScript**, paste the function plus a call at the bottom (same as above, `console.log` optional), and step through. It shows the hash map's contents changing line by line, which is a good way to compare against your own table.

Working in Python? You can rewrite the problem in Python and use Python Tutor's default mode, but that's extra work. Not required.

### Deliverable

A working fix isn't the deliverable — an AI tool can produce that in one prompt with zero understanding of hash maps. What you submit has to prove you did the trace, not just that the code runs. Push to a GitHub repo:

1. **Your variable table** — photo or scan of the paper version, or a typed recreation if you worked digitally. This has to show the actual state you traced, not a clean redo after the fact.
1. **The fixed code.**
1. **A short written explanation (3-5 sentences)**, in your own words, covering:
   - What line was wrong, and what it was doing instead of what it should've done
   - Why this problem calls for a hash map in the first place — what signal in the problem statement pointed there
   - What input exposed the bug, and why a "normal-looking" input might not have
1. Submit the repo link via the course tracker.

You can use AI to double-check your fix once you've found it — that's fine. The variable table and the explanation have to be yours: if you can't reproduce that explanation out loud with no notes when your instructor asks, that's the same gap as submitting an AI-written resume bullet you can't defend.

## Homework

1. From the [Tiered Problem Bank](../Assignments/Tiered-Problem-Bank.md), solve [Two Sum](https://leetcode.com/problems/two-sum/) and [Valid Anagram](https://leetcode.com/problems/valid-anagram/) (Tier 1, both hash map problems). Add a one-line comment at the top of each solution naming the pattern and why it fits.
1. After you’ve written the code, use a variable table to trace through the code. Check your work using [Python Tutor](https://pythontutor.com).
1. Commit your solution code and test cases to a GitHub repo and submit the link via the course tracker.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.