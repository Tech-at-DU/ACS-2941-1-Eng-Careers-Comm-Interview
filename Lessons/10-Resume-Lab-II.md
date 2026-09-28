# Resume/Career Lab II

### Slides

*(Add link to slide deck)*

## Coding Block (60 min)

Today's coding time runs longer than a real interview would allow for any one of these problems — that's on purpose, to leave room for discussion. Each problem below is tagged with the real interview time budget so you can feel the difference between "class pace" and "interview pace."

### Warm-Up: Hash Map Review (20 min)

One easy problem you haven't seen yet, to keep [Lesson 9's pattern](09-Whiteboard-Coding.md) warm without re-covering the same ground. Solo first, then compare with a partner — say the pattern out loud and why it fits before either of you starts coding.

**Like you're 5:** picture a coat check at a theater. Hand over your coat, get a numbered ticket back. Hours later, hand back the ticket, and the attendant walks straight to the right hook instead of checking every coat in the building. That's a hash map — a label you can hand over to get the right thing back instantly, instead of searching.

Counting is the same idea with a twist: imagine sorting a big bag of mixed candy into labeled jars — one jar per color. Once it's sorted, "how many red?" is just reading the label on the red jar, not recounting the whole bag. That's exactly what Ransom Note below needs: instead of scanning `magazine` over and over for each letter in `ransomNote`, sort `magazine`'s letters into jars once, then just check each jar's count.

**Ransom Note** ([source](https://leetcode.com/problems/ransom-note/)) — *Pattern: hash map. Real interview time: 10-15 min.*

> Given two strings `ransomNote` and `magazine`, return `true` if `ransomNote` can be constructed by cutting letters out of `magazine`, and `false` otherwise. Each letter in `magazine` can only be used once — if `magazine` has one `"a"`, it can't cover two `"a"`s in `ransomNote`.
>
> ```
> Example 1: ransomNote = "a", magazine = "b"   → false
> Example 2: ransomNote = "aa", magazine = "ab"  → false
> Example 3: ransomNote = "aa", magazine = "aab" → true
> ```

```js
function canConstruct(ransomNote, magazine) {
  // your code here
}
```

```python
def can_construct(ransom_note, magazine):
    # your code here
    pass
```

With the extra time: once you've got a working solution, compare pace with your partner — who used the full 15 min, who finished in 5? If you finished fast, use the rest of the time to state the complexity and defend it, the way you would if an interviewer asked "can you do better?"

### Pattern Focus: Two Pointers & Sliding Window (10 min)

New pattern, starting today. Two pointers (and its sliding-window variant) is what replaces a nested loop with a single pass when you're working on an **array or string** — especially a **sorted** one.

**Like you're 5:** picture a sorted row of cups on a table, numbered low to high, and you're looking for two cups whose numbers add up to a target. The slow way: pick up every cup and check it against every other cup, one at a time. The two-pointer way: put your left hand on the first cup and your right hand on the last cup. Sum too small? Slide your left hand in — you need a bigger number. Sum too big? Slide your right hand in. Your hands walk toward each other and meet in the middle, and you've never touched most cups twice.

Sliding window is the same idea stretched into a window instead of two hands: imagine counting the longest stretch of green lights on a drive. You keep a "start" and "end" marker. Hit a green light, push "end" forward. Hit a red one, drag "start" forward until you're back to all-green. You're never restarting the count from the beginning of the street — just adjusting the two edges of your current window.

Watch for:

- Looking for a pair/triple in a **sorted array** that meets some condition — move one pointer from each end inward instead of comparing every pair.
- Tracking a **substring/subarray** that grows and shrinks as you scan — a window with a left and right edge, instead of re-scanning from the start each time.

```js
// JS — two pointers converging on a sorted array
function hasPairWithSum(nums, target) {
  let left = 0, right = nums.length - 1;
  while (left < right) {
    const sum = nums[left] + nums[right];
    if (sum === target) return true;
    if (sum < target) left++;
    else right--;
  }
  return false;
}
```

```python
# Python — same idea
def has_pair_with_sum(nums, target):
    left, right = 0, len(nums) - 1
    while left < right:
        total = nums[left] + nums[right]
        if total == target:
            return True
        elif total < target:
            left += 1
        else:
            right -= 1
    return False
```

The tell, same as with hash maps: a brute-force version of this needs a nested loop (O(n²)) checking every pair. Two pointers does it in one pass (O(n)) — no extra memory needed, unlike a hash map's tradeoff. We'll go deeper on the complexity comparison in Lesson 12.

### Activity: Two Pointer Practice (30 min)

For both problems: state the pattern out loud before coding, and the complexity out loud when you finish. You have more time than a real interview would give you — use the extra time to discuss with your partner, not just to code slower.

**1. Merge Sorted Array** ([source](https://leetcode.com/problems/merge-sorted-array/)) — *Pattern: two pointers. Real interview time: 15-20 min.* Work with a partner.

> You're given two integer arrays `nums1` and `nums2`, both sorted in non-decreasing order, plus two integers `m` and `n` — the number of real elements in each. `nums1` has length `m + n`: the first `m` slots hold its real values, and the last `n` slots are just `0` placeholders, there to leave room for `nums2` to be merged in. Merge `nums2` into `nums1` so `nums1` becomes one sorted array of length `m + n`.
>
> ```
> Example: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
>          → nums1 becomes [1,2,2,3,5,6]
> ```
>
> *Hint: why would merging from the back of both arrays, instead of the front, avoid overwriting values you still need?*

```js
function merge(nums1, m, nums2, n) {
  // your code here — modify nums1 in place, return nothing
}
```

```python
def merge(nums1, m, nums2, n):
    # your code here — modify nums1 in place, return nothing
    pass
```

**2. Valid Palindrome** ([source](https://leetcode.com/problems/valid-palindrome/)) — *Pattern: two pointers. Real interview time: 10-15 min.* Solo, then compare with your partner.

> A phrase is a palindrome if, after lowercasing everything and removing all non-alphanumeric characters, it reads the same forwards and backwards. Given a string `s`, return whether it's a palindrome.
>
> ```
> Example 1: s = "A man, a plan, a canal: Panama" → true
> Example 2: s = "race a car"                     → false
> ```

```js
function isPalindrome(s) {
  // your code here
}
```

```python
def is_palindrome(s):
    # your code here
    pass
```

## Activity: Resume Peer Reviews (30 minutes)

Choose Partners A and B. Partner A will:
- Verbally talk through each part of their resume. (Make sure to **share your screen**!)
- Explain any points of improvement they’d like to make.

Partner B will:
- Give constructive feedback using the [Resume, Portfolio & LinkedIn Checklist](../Assignments/Resume-Portfolio-LinkedIn-Checklist.md).

After 15 minutes, switch partners.

## Break

## Activity: Portfolio Peer Reviews

Choose Partners A and B. Partner A will:
- Explain each of your portfolio projects: What is it?, What did you learn?, What was hard?

Partner B will:
- Give constructive feedback on the portfolio projects’ READMEs, using the Portfolio section of the checklist.

After 10 minutes, switch partners.

## Homework

- Before next class: Write your Personal Odyssey (a 2-3 minute narrative about your path into tech and what you're looking for next) and be ready to share with a partner
- Complete the [Resume, Portfolio & LinkedIn Checklist](../Assignments/Resume-Portfolio-LinkedIn-Checklist.md) in full and submit via the course tracker
