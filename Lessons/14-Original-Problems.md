# Stacks & Wrap-Up

## Minute-by-Minute

| Elapsed | Time | Activity | Format |
| ------- | ---- | -------- | ------ |
| 0:00    | 0:15 | Warm-Up: Original Problems | Pair |
| 0:15    | 0:10 | Stacks, Explained Like You're 5 | Whole class |
| 0:25    | 0:30 | Activity: Easy Stack Practice | Pair |
| 0:55    | 0:10 | BREAK | — |
| 1:05    | 0:45 | Mock Interview: Daily Temperatures | Pair, then whole class |
| 1:50    | 0:10 | Wrap-Up for the Term: What's Next | Whole class |
| 2:00    | 0:10 | Wrap-Up for the Term: End-of-Term Survey | Solo |
| 2:10    | 0:10 | Wrap-Up for the Term: Closing Circle | Whole class |
| 2:20    | 0:05 | Wrap-Up for the Term: Feedback | Solo |
| **Total** | **2:25** |  |  |

## Warm-Up: Original Problems (15 min)

Pull out the 2 Original Problems you wrote for homework after [Lesson 13](13-Interview-Practice.md). With a partner, pick one each — the one built around a pattern, if you have it — and take turns: about 7 minutes per person.

The presenter reads the problem out loud. The interviewer's job is to push, the way a real interviewer would:

- "Restate it — what's the input, what's the output?"
- "Which pattern is this, and why does it fit?" (hash map, two pointers/sliding window, stack, or other)
- "What's the brute-force version, and what does your pattern save you?"

No full solution needed in 7 minutes — a clear restatement, a named pattern, and a one-sentence approach is the goal. If the interviewer thinks a different pattern fits better, say so; that disagreement is the most useful part.

## Stacks, Explained Like You're 5 (10 min)

[Lesson 13](13-Interview-Practice.md) introduced stacks with a stack of cafeteria trays: you can only take the top one, and anything new goes on top. **Last in, first out** (LIFO). Today goes further — same tool, more kinds of problems.

**Like you're 5:** think about your browser's back button. Every page you visit goes on top of a pile. Hit "back," and you land on the page you were *just* on — not the first page you opened this morning. Hit it again, and you go one further back. The browser never needs to search the pile; the answer is always whatever's on top.

That's the whole trick of a stack: **the thing you need next is always the most recent thing that's still unfinished.** If a problem has that shape, you don't need to search — you just look at the top.

**When to reach for a stack.** Watch for:

- **Matching or nesting** — brackets, HTML tags, anything that opens and has to close in the right order.
- **Undo / cancel** — a backspace, a "remove the last one," an operation that wipes out whatever came right before it.
- **"Most recent unresolved thing"** — you're scanning left to right, some items are still waiting for an answer, and new items resolve the *most recent* waiting ones first.

The opposite shape is a **queue** — first in, first out, like a line at a coffee shop. If the oldest item gets handled first, it's not a stack.

**Quick round — stack or not?** Call it out as a class, and name the pattern if it's not a stack:

1. Check whether a string of HTML tags like `<div><p></p></div>` is properly nested.
1. Find two numbers in a list that add up to a target.
1. Process print jobs in the order they were sent to the printer.
1. Given a list of browser actions (`visit X`, `back`), return the page you end up on.
1. Find the longest substring with no repeating characters.

<details>
<summary>Answers</summary>

1. **Stack** — nesting; the last tag opened has to be the first one closed.
1. **Hash map** — "have I seen `target - num` yet?" ([Lesson 9](09-Whiteboard-Coding.md))
1. **Not a stack — a queue.** The oldest job prints first.
1. **Stack** — `back` undoes the most recent `visit`.
1. **Sliding window** — a substring that grows and shrinks ([Lesson 11](11-Industry-Contacts.md)).

</details>

## Activity: Easy Stack Practice (30 min)

With a partner. For each problem: one person drives, the other traces the stack on paper as you go. Swap drivers between problems. Do 1 and 2; 3 is a stretch if you finish early.

Before coding each one, answer out loud: **what goes on the stack, and what makes you pop?** That one sentence is most of the solution.

**1. Baseball Game** ([source](https://leetcode.com/problems/baseball-game/)) — *Pattern: stack. Real interview time: 10 min.*

> You're keeping score for a game with strange rules. Given a list of operations, return the sum of all scores at the end:
>
> - An integer `x` — record a new score of `x`.
> - `"+"` — record a new score that's the sum of the previous two scores.
> - `"D"` — record a new score that's double the previous score.
> - `"C"` — cancel the previous score, removing it from the record.
>
> ```
> Example: ops = ["5", "2", "C", "D", "+"] → 30
> ```

Trace it before you code:

| op | action | stack after |
| -- | ------ | ----------- |
| `"5"` | push 5 | `[5]` |
| `"2"` | push 2 | `[5, 2]` |
| `"C"` | pop (cancel the 2) | `[5]` |
| `"D"` | push double the top | `[5, 10]` |
| `"+"` | push sum of top two | `[5, 10, 15]` |

Sum: `5 + 10 + 15 = 30`.

<details>
<summary>Solution</summary>

```js
function calPoints(ops) {
  const stack = [];
  for (const op of ops) {
    if (op === 'C') {
      stack.pop();
    } else if (op === 'D') {
      stack.push(stack[stack.length - 1] * 2);
    } else if (op === '+') {
      stack.push(stack[stack.length - 1] + stack[stack.length - 2]);
    } else {
      stack.push(Number(op));
    }
  }
  return stack.reduce((sum, score) => sum + score, 0);
}
```

```python
def cal_points(ops):
    stack = []
    for op in ops:
        if op == 'C':
            stack.pop()
        elif op == 'D':
            stack.append(stack[-1] * 2)
        elif op == '+':
            stack.append(stack[-1] + stack[-2])
        else:
            stack.append(int(op))
    return sum(stack)
```

`"C"` is the same "undo" move as the backspace problem from Lesson 13 — cancel whatever's most recent.

</details>

**2. Remove All Adjacent Duplicates in String** ([source](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)) — *Pattern: stack. Real interview time: 10-15 min.*

> Given a string `s`, repeatedly remove any two adjacent letters that are the same, until no more can be removed. Return the final string.
>
> ```
> Example 1: s = "abbaca" → "ca"
> Example 2: s = "azxxzy" → "ay"
> ```

The catch: removing `"bb"` from `"abbaca"` makes the two `a`s neighbors, so they get removed too. A naive "scan and delete" has to restart from the beginning every time something is removed. A stack doesn't — the top of the stack is always the letter that's currently "next door."

<details>
<summary>Solution</summary>

```js
function removeDuplicates(s) {
  const stack = [];
  for (const char of s) {
    if (stack.length > 0 && stack[stack.length - 1] === char) {
      stack.pop();
    } else {
      stack.push(char);
    }
  }
  return stack.join('');
}
```

```python
def remove_duplicates(s):
    stack = []
    for char in s:
        if stack and stack[-1] == char:
            stack.pop()
        else:
            stack.append(char)
    return ''.join(stack)
```

</details>

**3. Stretch: Make The String Great** ([source](https://leetcode.com/problems/make-the-string-great/)) — *Pattern: stack. Real interview time: 10-15 min.*

> A string is "bad" if it has two adjacent characters that are the same letter in different cases (like `"aA"` or `"Bb"`). Remove those pairs until the string is "good," and return it.
>
> ```
> Example 1: s = "leEeetcode" → "leetcode"
> Example 2: s = "abBAcC"     → ""
> ```

This is problem 2 with a different rule for "should these two cancel out?" — if you solved problem 2, change one line.

<details>
<summary>Solution</summary>

```js
function makeGood(s) {
  const stack = [];
  for (const char of s) {
    const top = stack[stack.length - 1];
    if (top !== undefined && top !== char && top.toLowerCase() === char.toLowerCase()) {
      stack.pop();
    } else {
      stack.push(char);
    }
  }
  return stack.join('');
}
```

```python
def make_good(s):
    stack = []
    for char in s:
        if stack and stack[-1] != char and stack[-1].lower() == char.lower():
            stack.pop()
        else:
            stack.append(char)
    return ''.join(stack)
```

</details>

## Break (10 min)

## Mock Interview: Daily Temperatures (45 min)

The last interview problem of the course — and a step up. The practice problems above all use the stack to *cancel* things. This one uses it to keep a list of things that are **still waiting for an answer**, which is the version of the stack pattern that shows up most often in real interviews.

**Daily Temperatures** ([source](https://leetcode.com/problems/daily-temperatures/)) — *Pattern: stack. Real interview time: 20-25 min.*

> Given an array of daily temperatures, return an array `answer` where `answer[i]` is the number of days you have to wait after day `i` to get a warmer temperature. If there's no warmer day coming, `answer[i]` is `0`.
>
> ```
> Example: temperatures = [73, 74, 75, 71, 69, 72, 76, 73]
>          answer       = [ 1,  1,  4,  2,  1,  1,  0,  0]
> ```

### Part 1: The Interview (25 min)

Pair up: one candidate, one interviewer. Candidate: run the full process — restate, clarify, assumptions, think out loud ([Lesson 1](01-Interviewing-Communication.md)), name your pattern, then code. **Start with brute force** and state its complexity before you look for something better; a working O(n²) answer said out loud beats a half-finished clever one.

Interviewer: you have the problem and the hint ladder below. Don't hand out hints early — wait until the candidate has been stuck for about 2 minutes, then give the next one. Note which hint they needed; that goes in your feedback.

<details>
<summary>Interviewer only: hint ladder</summary>

1. "What's the brute-force version? What's its time complexity?" — *(for each day, scan forward until you find a warmer one: nested loop, O(n²))*
1. "As you scan left to right, which days are still waiting for their answer?"
1. "When a warm day shows up, which waiting days does it answer — and which one does it check first?" — *(the most recent waiting day first — that's the stack)*
1. "Should the stack hold temperatures or something else?" — *(indices — you need the index to compute how many days apart they are)*

</details>

### Part 2: Walkthrough & Debrief (20 min)

Whole class. Trace the example together. The stack holds **indices of days still waiting** for a warmer day. On each new day, pop and answer every waiting day that's colder than today, then push today.

| Day `i` | Temp | Pops (and answers) | Stack after (indices) |
| ------- | ---- | ------------------ | --------------------- |
| 0 | 73 | — | `[0]` |
| 1 | 74 | day 0 (73) → `answer[0] = 1` | `[1]` |
| 2 | 75 | day 1 (74) → `answer[1] = 1` | `[2]` |
| 3 | 71 | — (75 isn't colder) | `[2, 3]` |
| 4 | 69 | — | `[2, 3, 4]` |
| 5 | 72 | day 4 (69) → `answer[4] = 1`, day 3 (71) → `answer[3] = 2` | `[2, 5]` |
| 6 | 76 | day 5 (72) → `answer[5] = 1`, day 2 (75) → `answer[2] = 4` | `[6]` |
| 7 | 73 | — | `[6, 7]` |

Days 6 and 7 are still on the stack at the end — no warmer day ever came, so their answer stays `0`.

```js
function dailyTemperatures(temperatures) {
  const answer = new Array(temperatures.length).fill(0);
  const stack = []; // indices of days still waiting for a warmer day
  for (let i = 0; i < temperatures.length; i++) {
    while (stack.length > 0 && temperatures[i] > temperatures[stack[stack.length - 1]]) {
      const waitingDay = stack.pop();
      answer[waitingDay] = i - waitingDay;
    }
    stack.push(i);
  }
  return answer;
}
```

```python
def daily_temperatures(temperatures):
    answer = [0] * len(temperatures)
    stack = []  # indices of days still waiting for a warmer day
    for i, temp in enumerate(temperatures):
        while stack and temp > temperatures[stack[-1]]:
            waiting_day = stack.pop()
            answer[waiting_day] = i - waiting_day
        stack.append(i)
    return answer
```

**Why is this O(n) when there's a loop inside a loop?** Same question as [Lesson 12](12-Complexity-Analysis.md): count the work, not the loops. Every index gets pushed exactly once and popped at most once, so the inner `while` runs at most n times *total* across the whole array — not n times per day.

**Debrief with your partner (last 5 min):** Interviewer, share which hint (if any) the candidate needed, and one thing they did well in communicating. Candidate, say what you'd do differently if you got this problem in a real interview tomorrow.

## Wrap-Up for the Term

### What's Next: Continuing the Work (10 min)

The course ends today; none of this ends today. Concretely, before you leave:

- **Study for the final** using the [Final Assessment Study Guide](../Assessments/final-assessment.md).
- **Keep solving problems.** The [Tiered Problem Bank](../Assignments/Tiered-Problem-Bank.md) doesn't expire — keep working up through the tiers on your own cadence. [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) (Tier 4) uses the same "waiting stack" idea as Daily Temperatures.
- **Follow up with your contact from [Lesson 11](11-Industry-Contacts.md).** If they replied, send one more message now — a thank-you, or an update on where your search stands. Don't let a real connection go cold because the course ended.
- **Revisit your resume and LinkedIn** before every new application cycle, not just once. The [checklist](../Assignments/Resume-Portfolio-LinkedIn-Checklist.md) still works after today.
- **Keep an eye out for the three patterns** — hash maps, two pointers/sliding window, stacks. They were the throughline of this course because they're the throughline of real interviews too; recognizing them is a habit, and habits need upkeep.

### End-of-Term Survey (10 min)

Please complete the course feedback survey via the course tracker.

### Closing Circle (10 min)

Go around the room. Each person: 20-30 seconds, no more — name one specific thing from this course that clicked for you, or one thing you're proud of having done. "I don't freeze up anymore" counts. "I finally get hash maps" counts. Specific beats polished.

### Feedback (5 min)

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.
