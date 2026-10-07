# Interview Practice

## Pattern Focus: Stacks (25 min)

A stack is the right tool for anything about matching, nesting, or "undo": parentheses/bracket validity, matching opens to closes, or tracking the most-recent unresolved thing. The tell: the problem cares about *order of closing*, not just order of appearance — last one open needs to be the first one resolved.

**Like you're 5:** picture a stack of cafeteria trays. You can only ever take the top one, and any new tray you add goes on top of the pile — you can't grab one from the middle. That's a stack: **last one in is the first one out** (LIFO). Same idea as hitting "undo" over and over: the most recent action is always the first thing that gets undone, never something from three steps ago.

For bracket matching specifically: picture walking down a hallway opening doors. Each door you open needs to get closed eventually, and the last door you opened has to be the first one you close — otherwise the hallway doesn't make sense. That's exactly why `"([)]"` is invalid: you opened `(` then `[`, so `[` has to close before `(` does, but the `)` shows up first and tries to close the wrong one.

**Syntax — no new data structure needed.** A stack is just an array/list, used with one rule: only ever add or remove from the same end.

```js
// JS — array as a stack
const stack = [];
stack.push('(');   // add to top
stack.push('[');
stack.pop();       // removes and returns '[' — the most recent one
```

```python
# Python — list as a stack
stack = []
stack.append('(')  # add to top
stack.append('[')
stack.pop()         # removes and returns '[' — the most recent one
```

**Quick warm-up — predict before you check:**

```js
const stack = [];
stack.push('a');
stack.push('b');
stack.push('c');
console.log(stack.pop());
console.log(stack.pop());
stack.push('d');
console.log(stack);
```

<details>
<summary>Answer</summary>

`'c'`, then `'b'`, then `['a', 'd']`. Each `pop` removes whatever was most recently pushed — not the oldest item, not a specific index.

</details>

**Valid Parentheses** ([source](https://leetcode.com/problems/valid-parentheses/)) — *Pattern: stack. Real interview time: 15-20 min.*

> Given a string `s` containing just the characters `(`, `)`, `{`, `}`, `[`, `]`, return whether the brackets are valid: every open bracket is closed by the same type of bracket, and in the right order.
>
> ```
> Example 1: s = "()[]{}" → true
> Example 2: s = "([)]"   → false
> ```

Trace `"([)]"` to see exactly where it breaks:

| char | action | stack after |
| ---- | ------ | ------------ |
| `(` | push | `['(']` |
| `[` | push | `['(', '[']` |
| `)` | need to close — pop the top (`[`) and check it matches `)` | `['(']` — but `[` ≠ `)`'s partner, **mismatch, return false** |

```js
function isValid(s) {
  const stack = [];
  const pairs = { ')': '(', ']': '[', '}': '{' };
  for (const char of s) {
    if (char === '(' || char === '[' || char === '{') {
      stack.push(char);
    } else {
      if (stack.pop() !== pairs[char]) return false;
    }
  }
  return stack.length === 0;
}
```

```python
def is_valid(s):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    for char in s:
        if char in '([{':
            stack.append(char)
        else:
            if not stack or stack.pop() != pairs[char]:
                return False
    return len(stack) == 0
```

Note the final check: `stack.length === 0`. A string like `"(("` never hits a mismatch, but it also never finishes closing everything — that's the bug an incomplete solution misses.

**Backspace String Compare** ([source](https://leetcode.com/problems/backspace-string-compare/)) — second rep, *Real interview time: 10-15 min.*

> A string contains lowercase letters and `#`, where `#` means "backspace" — delete the character before it, if any. Given a string `S`, return the final string after processing every character.
>
> ```
> Example 1: S = "ab#c"  → "ac"
> Example 2: S = "a##c"  → "c"
> ```

```js
function processBackspaces(S) {
  const stack = [];
  for (const char of S) {
    if (char === '#') stack.pop();
    else stack.push(char);
  }
  return stack.join('');
}
```

```python
def process_backspaces(S):
    stack = []
    for char in S:
        if char == '#':
            if stack:
                stack.pop()
        else:
            stack.append(char)
    return ''.join(stack)
```

Same "undo" framing as the cafeteria-tray analogy: `#` is just pressing undo on whatever you typed most recently.

This class is cumulative — by now you've seen hash maps (Lesson 9), two pointers/sliding window (Lesson 12), and today, stacks. The list below mixes all three on purpose.

## Activity: Interview Practice

For each problem, **say the pattern out loud before you start coding** (hash map, two pointer/sliding window, stack, or other) — then solve it under time pressure.

1. [Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/): Determine if two strings are "isomorphic". *(hash map)*
1. [Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/): Remove all elements from a linked list that contain a given value.
1. [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/): Given 2 sorted arrays, merge them into 1 sorted array. *(two pointers)*
1. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/): Determine if a string of parentheses is valid. *(stack)*
1. [Roman Numeral to Integer](https://leetcode.com/problems/roman-to-integer/): Convert a Roman numeral to an integer.
1. [Valid Anagram](https://leetcode.com/problems/valid-anagram/): Given two strings, determine if one is an anagram of another. *(hash map)*
1. [Minimum Domino Rotations](https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/): Find the minimum number of domino rotations to make all rows equal.

## Pattern Recap: The Three Patterns (10 min)

This is the last new pattern of the course — worth pulling all three into one place before [Lesson 14](14-Original-Problems.md)'s final review.

| If the problem says... | Reach for... | Why |
| ----------------------- | -------------- | --- |
| "Have you seen this before?" / "How many times does X appear?" / "find a pair that matches/adds up to" | **Hash map** | Trade memory for O(1) lookup instead of rescanning |
| Sorted array, looking for a pair/triple; or a substring/subarray that grows and shrinks | **Two pointers / sliding window** | One pass instead of a nested loop — O(n) instead of O(n²) |
| Matching, nesting, or "undo" — order of *closing* matters, not just order of appearance | **Stack** | Last one in has to be the first one out |

None of these are the only tool that ever works — they're the fastest ones to reach for when the signal is there. In an interview, naming the pattern out loud *before* you code, the way you've been practicing all week, is doing half the interviewer's job for them.

## Homework

Write 2 Original Problems and bring them to class on Monday! At least one should be built around one of the three patterns from this course (hash map, two pointers/sliding window, or stack) — you'll need to be able to say which, and why, when you present it.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.