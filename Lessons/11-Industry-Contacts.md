# Industry Contacts

## Learning Outcomes

By the end of today, you should be able to...

1. Identify the importance & benefits of reaching out to industry contacts.
1. Identify fears & misconceptions around connecting with industry as well as finding a solution around them.
1. Use resources available to get the information of relevant contacts. 
1. Compose a message to either start a conversation or following up with an existing contact.
1. Trace a fixed-size and a variable-size sliding window by hand.
1. Recognize when an array problem needs in-place rewriting with two pointers — one reading, one writing — rather than a search.

## Warm-Up: Personal Odyssey (15 minutes)

**What this is and why it matters:** a Personal Odyssey is your prepared answer to the question you'll get asked in almost every interview and every networking conversation — "tell me about yourself" or "walk me through your background." It's not your whole life story. It's a tight 2-3 minute narrative: where you started, what pulled you into tech, and what you're looking for next.

Without a prepared version, most people either freeze or ramble for eight minutes and lose the room. With one, you control the first impression instead of scrambling for it live. And it's not theoretical today — later this class, in the informational interview activity, if a contact replies with "sure, tell me about yourself," this is what you say.

1. Partner A: Share your Personal Odyssey (a 2-3 minute narrative about your path into tech and what you're looking for next) with a partner.
1. Partner B: Give feedback and suggestions. Start by giving positive feedback.
1. Switch roles! 

## Coding Block (45 min)

[Lesson 10](10-Resume-Lab-II.md) introduced two pointers and sliding window. Today goes deeper on sliding window specifically, plus a related technique that looks like nothing you've done yet: rewriting an array in place.

### Walkthrough: Fixed-Size Sliding Window (15 min)

Instructor-led — trace along, don't code yet.

**Maximum Sum Subarray of Size K:** given an array of positive integers and an integer `k`, find the maximum sum of any `k` contiguous elements.

> Example: `nums = [2, 1, 5, 1, 3, 2]`, `k = 3` → answer `9` (the window `[5, 1, 3]`)

The naive approach recomputes the sum of every window from scratch — for each of the `n - k + 1` windows, add up `k` elements, so O(n·k). The sliding-window trick: you already know the sum of the previous window, so sliding right by one means *subtracting the element that just left* and *adding the element that just entered* — no re-summing. O(n) regardless of `k`.

| Step | Window | Removed | Added | Sum | Max so far |
| ---- | ------ | ------- | ----- | --- | ---------- |
| build | `[2,1,5]` | — | — | 8 | 8 |
| slide | `[1,5,1]` | 2 | 1 | 7 | 8 |
| slide | `[5,1,3]` | 1 | 3 | 9 | 9 |
| slide | `[1,3,2]` | 5 | 2 | 6 | 9 |

Answer: `9`. That "subtract what left, add what entered" move is the entire idea — everything else is bookkeeping.

```js
function maxSubarraySum(nums, k) {
  let windowSum = 0;
  for (let i = 0; i < k; i++) windowSum += nums[i];
  let maxSum = windowSum;
  for (let i = k; i < nums.length; i++) {
    windowSum += nums[i] - nums[i - k];
    maxSum = Math.max(maxSum, windowSum);
  }
  return maxSum;
}
```

### Practice: Variable-Size Sliding Window (15 min)

Trace this one together as a class first, using the table format above — then students code it solo, then compare with a partner.

**Longest Substring Without Repeating Characters** ([source](https://leetcode.com/problems/longest-substring-without-repeating-characters/)) — *Real interview time: 20-25 min (this one's a step up).*

> Given a string `s`, find the length of the longest substring without repeating characters.
>
> ```
> Example: s = "pwwkew" → answer 3 (the substring "wke")
> ```

This time the window isn't a fixed size — it grows by moving `right` forward, and shrinks by moving `left` forward whenever the new character is already inside the window.

| `right` | char | already in window? | window after | length | max |
| ------- | ---- | ------------------- | ------------- | ------ | --- |
| 0 | p | no | `"p"` | 1 | 1 |
| 1 | w | no | `"pw"` | 2 | 2 |
| 2 | w | yes — shrink `left` until it's gone | `"w"` | 1 | 2 |
| 3 | k | no | `"wk"` | 2 | 2 |
| 4 | e | no | `"wke"` | 3 | 3 |
| 5 | w | yes — shrink `left` until it's gone | `"kew"` | 3 | 3 |

Answer: `3`.

```js
function lengthOfLongestSubstring(s) {
  const seen = new Set();
  let left = 0, maxLen = 0;
  for (let right = 0; right < s.length; right++) {
    while (seen.has(s[right])) {
      seen.delete(s[left]);
      left++;
    }
    seen.add(s[right]);
    maxLen = Math.max(maxLen, right - left + 1);
  }
  return maxLen;
}
```

```python
def length_of_longest_substring(s):
    seen = set()
    left = 0
    max_len = 0
    for right in range(len(s)):
        while s[right] in seen:
            seen.remove(s[left])
            left += 1
        seen.add(s[right])
        max_len = max(max_len, right - left + 1)
    return max_len
```

This is the exact problem you'll see again as homework in [Lesson 12](12-Complexity-Analysis.md) — today's the walkthrough, that's the retention check.

### New Technique: In-Place Array Rewriting (15 min)

This one will feel unfamiliar — it's not a search, it's *rearranging the array using its own space*, with no second array.

**Like you're 5:** you're organizing books on a single shelf, left to right, in one pass. You keep two fingers: one (`insertPos`) marks the next open "front" slot, the other (`i`) scans forward one book at a time. Every time the scanning finger finds a real book, you swap it into the marker finger's slot and move both fingers forward. If the scanning finger finds a gap instead, only it keeps moving — the marker finger stays put, waiting for the next real book to swap into place.

**Move Zeroes** ([source](https://leetcode.com/problems/move-zeroes/)) — *Real interview time: 15-20 min.*

> Given an integer array `nums`, move all `0`s to the end while keeping the relative order of the non-zero elements — and do it in-place, no new array.
>
> ```
> Example: nums = [0, 1, 0, 3, 12] → [1, 3, 12, 0, 0]
> ```

| `i` | `nums[i]` | action | array after |
| --- | --------- | ------ | ------------ |
| 0 | 0 | zero — skip | `[0,1,0,3,12]` |
| 1 | 1 | nonzero — swap with `insertPos=0` | `[1,0,0,3,12]` |
| 2 | 0 | zero — skip | `[1,0,0,3,12]` |
| 3 | 3 | nonzero — swap with `insertPos=1` | `[1,3,0,0,12]` |
| 4 | 12 | nonzero — swap with `insertPos=2` | `[1,3,12,0,0]` |

```js
function moveZeroes(nums) {
  let insertPos = 0;
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] !== 0) {
      [nums[i], nums[insertPos]] = [nums[insertPos], nums[i]];
      insertPos++;
    }
  }
}
```

**What's swapping with what:** this is a one-line swap, no temp variable. Read the right side first — `[nums[insertPos], nums[i]]` builds a temporary pair holding the *old* values, `insertPos`'s value first, `i`'s value second. The left side then unpacks that pair back into the array in the same order: `nums[i]` gets the first item (old `nums[insertPos]`), `nums[insertPos]` gets the second item (old `nums[i]`). Net effect: the values at index `i` and index `insertPos` trade places. Without this shorthand, it'd be three lines:

```js
const temp = nums[i];
nums[i] = nums[insertPos];
nums[insertPos] = temp;
```

Both versions are O(1) per swap — different syntax, same Big-O, a preview of [Lesson 12](12-Complexity-Analysis.md).

```python
def move_zeroes(nums):
    insert_pos = 0
    for i in range(len(nums)):
        if nums[i] != 0:
            nums[i], nums[insert_pos] = nums[insert_pos], nums[i]
            insert_pos += 1
```

Trace it by hand with the table above before you run it — the swap is easy to get backwards on a whiteboard.

## Break (10 min)

## Activity: Request an Informational Interview

1. Find a Contact: Open up LinkedIn (or X, GitHub, a company's engineering blog) and search for keywords for people you’d like to connect with.
1. Write a message: Keep it short, sweet, to the point, and specific to something real about them (a project, a post, a talk) — generic or obviously AI-generated cold messages get ignored.
1. Send your message! 
1. Be sure to follow up if you receive a reply.

## Homework

1. Complete the [Resume, Portfolio & LinkedIn Checklist](../Assignments/Resume-Portfolio-LinkedIn-Checklist.md) and submit via the course tracker.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.
