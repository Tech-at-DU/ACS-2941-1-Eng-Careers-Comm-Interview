# Test Cases

## Minute-by-Minute

| Elapsed | Time | Activity | Format |
| ------- | ---- | -------- | ------ |
| 0:00    | 0:10 | Overview: Proving It Works | Whole class |
| 0:10    | 0:10 | Warm-Up #1: Problem Solving Strategy Recap | Solo → Pair |
| 0:20    | 0:10 | Warm-Up #2: Types of Test Cases | Solo → Pair |
| 0:30    | 0:30 | Activity 1: Generate Test Cases | Solo → Pair |
| 1:00    | 0:10 | BREAK | — |
| 1:10    | 1:10 | Activity 2: Interview Breakouts | Pair (role play) |
| 2:20    | 0:10 | Debrief | Whole class |
| 2:30    | 0:10 | Exit Ticket | Solo |
| 2:40    | 0:05 | Wrap-Up | Whole class |
| **Total** | **2:45** | | |

## Instructor Setup

*For whoever is teaching — students can skip to Overview.*

- Both activities today use the same 4 Practice Problems below — no new problems to introduce for Activity 2.
- Pre-assign partners for Activity 2 (2 rounds, swap roles each round).
- Round 2 counts toward 6-of-8 — Interviewer submits via the [Peer Interview Rubric form](https://forms.gle/m8j2nLWB3HbgnGGx9), Interviewee submits via the [Self-Assessment form](https://forms.gle/6cWUACVPmBtaY4jV8).
- Exit Tickets submit to the [Exit Ticket form](https://forms.gle/hLLsHySp2BT7qXAZ7).

## Overview: Proving It Works (10 min)

Lessons 1-3 built how you talk through and plan a solution. Lesson 4 built the judgment to read code closely enough to trust it. This lesson is the last piece before you write code in a live interview: proving your solution actually works, out loud, using the right test cases — not just "looks right to me." Good/normal, bad/unusual, and edge case inputs are what separates "I think this works" from "I checked."

## Learning Outcomes

By the end of this class, you will be able to...

1. **Define** good/normal, bad/unusual, and edge case test inputs, and explain why interviewers care about each
1. **Generate** examples of each type live, for a problem you just solved
1. **Test a live solution out loud**, walking an interviewer through inputs rather than just saying "I think this works"

## Warm-Up #1: Problem Solving Strategy Recap (10 min)

Explain the **purpose** and **value** of each step of the problem solving strategy presented in Lesson 3:

1. Generate reasonable test inputs
1. Solve the problem by hand
   - Simplify the problem if needed
1. Find a pattern in your solution
1. Make a plan – Write pseudocode
1. Follow your plan – Write real code
1. Check your work – Test your code

Write in your notebook, then share with 1 or 2 partners.

## Warm-Up #2: Types of Test Cases (10 min)

In your own words, write down definitions for the following types of test cases:

1. Good/Normal Input
1. Bad/Unusual Input
1. Edge Case Input

Write in your notebook, then share with 1 or 2 partners.

**One tool worth knowing for bad/unusual and edge cases specifically:** if a problem has multiple boolean flags or conditions (e.g. a function that behaves differently based on 2-3 independent yes/no inputs), a truth table — every combination of true/false across those conditions — is a systematic way to make sure you haven't missed one. It won't help for most problems (today's practice problems aren't condition-based), but when a problem *is* shaped that way, it beats guessing at combinations.

## Practice Problems

Used across both Activity 1 and Activity 2 today.

1. Find the k largest values in an array of n numbers. Return them in a new array sorted in decreasing order.
1. Given an array a of numbers and a target value t, find two numbers that sum to t (that is, a[i] + a[j] = t).
1. Given a list of n strings with mixed casing, return a new list of all strings that start with a capitalized letter.
1. Find the longest substring of unique letters in a given string of n letters.

<details>
<summary><strong>Interviewer answer key</strong> — for Activity 2, don't peek if you're about to be interviewed</summary>

**Problem 1 (k largest, sorted descending):** Assume `k <= n`. Array may contain duplicates — they count individually. Array is unsorted; numbers can be negative.

**Problem 2 (two-sum):** Assume exactly one valid pair unless asked. Array is unsorted. Can't use the same element twice.

**Problem 3 (capitalized strings):** "Starts with a capitalized letter" means the first character specifically is uppercase A-Z. Case of the rest of the string doesn't matter. Assume standard English letters unless asked.

**Problem 4 (longest substring of unique letters):** "Substring" means contiguous. "Unique" means no repeated character within that substring. Case-sensitive unless they ask, in which case say yes. An empty string is valid input — answer is length 0.

If they ask something not covered here, make a reasonable call and stay consistent for the rest of the round.

</details>

## Activity 1: Generate Test Cases (30 min)

**Alone first (15 min):** for 2 of the problems above, come up with 3 of each: Good/normal inputs, bad/unusual inputs, and edge case inputs.

**Then, with a partner (15 min):** compare. Did you both think of the same edge cases, or did your partner catch something you missed?

## Break (10 min)

## Activity 2: Interview Breakouts (1 hour 10 min)

**Before you start — the full checklist:**

*Communication + Strategy (Lessons 1-3):* restate, clarify, assumptions, think out loud, simplify, find a pattern, pseudocode before code

*Today's addition:* once you have working code, test it out loud against Good/Normal, Bad/Unusual, and Edge Case inputs — don't just say "I think this works"

**Instructions:**

1. Your instructor will assign your partner. One will play interviewer, one interviewee.
1. Pick a problem from the list above. Work through it as if in an actual interview: pseudocode, then real code.
1. Once you have working code, step through it out loud with at least one input from each category: Good/Normal, Bad/Unusual, Edge Case. For each input:
   1. Say the input out loud and which category it represents.
   1. Say what output you *expect*, before tracing anything.
   1. Walk through your code's key steps, narrating what happens to your variables as that specific input moves through them.
   1. Say the actual result and confirm it matches what you expected — if it doesn't, debug out loud rather than going quiet.

   *Example, for two-sum with `a = [2, 7, 11, 15]`, `t = 9`:* "This is a good/normal input — a small unsorted array with one valid pair. I expect indices 0 and 1, since 2 + 7 = 9. Walking through: I check 2 against the rest of the array first... 2 + 7 is 9, that's a match, so I'd return [0, 1]. That matches what I expected."
1. Interviewer gives feedback on which test case types were covered and which were missed.
1. Swap roles, pick a new problem.
1. **Round 2:** the interviewer fills out the [Peer Interview Rubric](../Assignments/Sample_Rubric.md) — this round counts toward your 6-of-8 in-class peer interview rubrics. Interviewer submits via the [Peer Interview Rubric form](https://forms.gle/m8j2nLWB3HbgnGGx9); interviewee submits via the [Self-Assessment form](https://forms.gle/6cWUACVPmBtaY4jV8).

## Debrief (10 min)

As a class: which test case type — good/normal, bad/unusual, or edge case — did you most often forget to check until reminded? Why do you think that one especially slips people's minds?

## Exit Ticket (10 min)

**Students:** individually, no partner — submit via the [Exit Ticket form](https://forms.gle/hLLsHySp2BT7qXAZ7) before you go.

> Think of one bug a test case would have caught in your Activity 2 solution (real or hypothetical). Which category — good/normal, bad/unusual, or edge case — would have caught it, and why didn't you think of it until now?

**Instructor:** if "edge case" dominates the answers, that's expected — it's the hardest category to generate on your own. If "good/normal" shows up often, that's a bigger flag; it means students aren't testing at all until prompted.

## Homework

- Find 2 new problems on [Exercism](https://exercism.org) and solve them following the problem solving strategy covered in Lesson 3 to guide your thinking.
- Run your solution code on at least 2 inputs for each type of test case covered in this class.
- Commit your solution code and test cases to a GitHub repo and submit the link via the course tracker.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.
