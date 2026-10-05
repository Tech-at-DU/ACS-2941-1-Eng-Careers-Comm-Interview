# Complexity Analysis Worksheet

Work through Part 1 on your own before comparing with a partner. For each function, give **both** the time complexity and the space complexity — interviewers ask for both, and they're not always the same.

## Reference: Growth Curves

Rough shape of each class as `n` grows (flattest to steepest):

```
work
 ^                                              O(n²)
 |                                          ,·'
 |                                      ,·'
 |                                 ,·'          O(n log n)
 |                            ,·'    ,··'
 |                       ,·'   ,··'
 |                  ,·'  ,··'              O(n)
 |             ,·'··'
 |         ,·'·'                      O(log n)
 |     ,·'··  _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
 | ,·'·· _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _  O(1)
 +--------------------------------------------------> n
```

O(1) and O(log n) stay near-flat as `n` grows. O(n) rises steadily. O(n log n) rises a bit faster than O(n). O(n²) curves upward and gets steep fast. Keep this shape in mind while you work — you're deciding which curve each function belongs on.

## Part 1: Time & Space, Solo (20 min)

For each function: trace through it, then write the time complexity, the space complexity, and a one-sentence reason for each (what line or structure drives it).

**1.**

```js
function reverseString(s) {
  let result = "";
  for (let i = s.length - 1; i >= 0; i--) {
    result += s[i];
  }
  return result;
}
```

Time: _____ Reason: _____________________________
Space: _____ Reason: _____________________________

**2.**

```js
function hasDuplicateHashMap(nums) {
  const seen = {};
  for (const num of nums) {
    if (seen[num]) return true;
    seen[num] = true;
  }
  return false;
}
```

Time: _____ Reason: _____________________________
Space: _____ Reason: _____________________________

**2b.** Same problem, different approach:

```js
function hasDuplicateNestedLoop(nums) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length; j++) {
      if (i !== j && nums[i] === nums[j]) return true;
    }
  }
  return false;
}
```

Time: _____ Reason: _____________________________
Space: _____ Reason: _____________________________

**3.**

```js
function isPalindrome(s) {
  let left = 0, right = s.length - 1;
  while (left < right) {
    if (s[left] !== s[right]) return false;
    left++;
    right--;
  }
  return true;
}
```

Time: _____ Reason: _____________________________
Space: _____ Reason: _____________________________

**4.**

```js
function binarySearch(nums, target) {
  let low = 0, high = nums.length - 1;
  while (low <= high) {
    const mid = Math.floor((low + high) / 2);
    if (nums[mid] === target) return mid;
    else if (nums[mid] < target) low = mid + 1;
    else high = mid - 1;
  }
  return -1;
}
```

Time: _____ Reason: _____________________________
Space: _____ Reason: _____________________________

**5.**

```js
function allPairs(nums) {
  const pairs = [];
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length; j++) {
      pairs.push([nums[i], nums[j]]);
    }
  }
  return pairs;
}
```

Time: _____ Reason: _____________________________
Space: _____ Reason: _____________________________

## Part 2: The Time-Space Tradeoff (10 min)

Look back at **2** and **2b** — same problem, same result, different cost.

1. Which one is faster? Which one uses less memory?
1. In an interview, if you wrote 2b first and the interviewer asked "can you do better?", what would you say?
1. Is there ever a situation where you'd actually *prefer* 2b over 2? (Hint: think about `nums.length` and how much memory is actually available.)

## Part 3: Sketch It (5 min)

Using the reference curves above as a guide, sketch your own rough growth curve for each, in your own hand, no tracing: O(1), O(log n), O(n), O(n log n), O(n²).

## Partner Check (after Part 1)

Swap answers for problems 1-5 with a partner. Where did you disagree? If you disagreed on a space complexity answer, talk through it out loud until you agree — that's usually the one people get wrong first, not time.
