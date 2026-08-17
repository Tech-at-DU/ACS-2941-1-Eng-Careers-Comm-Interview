# Problem Solving Strategy

## Minute-by-Minute

| Elapsed | Time | Activity |
| ------- | ---- | -------- |
| 0:00    | 0:10 | Overview: A Different Kind of Practice |
| 0:10    | 0:15 | Warm-Up: Simplify First |
| 0:25    | 0:30 | Activity 1: Strategy Walkthrough |
| 0:55    | 0:10 | BREAK |
| 1:05    | 0:25 | Activity 2: Silent Pseudocode Handoff |
| 1:30    | 0:55 | Activity 3: Interview Breakout |
| 2:25    | 0:10 | Debrief |
| 2:35    | 0:05 | Exit Ticket |
| 2:40    | 0:05 | Wrap-Up |
| **Total** | **2:45** | |

## Instructor Setup

*For whoever is teaching — students can skip to Overview.*

- This lesson is planning-heavy and light on live role-play by design (see Overview) — resist the urge to add more talk-time; the Silent Pseudocode Handoff depends on students staying quiet during the implementation step.
- Split the room roughly in half before Activity 2 (Silent Pseudocode Handoff) — half gets Problem 3, half gets Problem 4.
- Pre-assign partners for Activity 3 (two rounds: Problem 2, then whichever of 3/4 they didn't already do).
- Have the Peer Interview Rubric ([Sample_Rubric.md](../Assignments/Sample_Rubric.md)) ready for Activity 3's second round — submits via the [Peer Interview Rubric form](https://forms.gle/m8j2nLWB3HbgnGGx9) (interviewer) and [Self-Assessment form](https://forms.gle/6cWUACVPmBtaY4jV8) (interviewee).
- Exit Tickets submit to the [Exit Ticket form](https://forms.gle/hLLsHySp2BT7qXAZ7).

## Overview: A Different Kind of Practice (10 min)

Lessons 1 and 2 drilled *how you talk about* a solution — restate, clarify, assumptions, think out loud. Today shifts to *how you build one*: simplify the problem, find a pattern, plan before you code, check your work after. Same interview, different half of the skill. The activities today are shaped differently on purpose — less live role-play, more planning-on-paper — because that's the part this strategy actually lives in.

## Learning Outcomes

By the end of this session, you will be able to describe and practice each of the problem-solving setps of the technical interview process:

1. Generate reasonable test inputs
1. Understand & solve the problem
    1. Simplify the problem if needed
1. Find a pattern in your solution
1. Make a plan - write pseudocode
1. Follow your plan - write real code
1. Check your work - test your code

## Warm-Up: Simplify First (15 minutes)

_**Interview Question:** Find the 5th largest value in an array of n numbers._

That's hard to picture at full size. Simplify it first:

1. Alone: solve the smaller version by hand — find the **2nd** largest value in a 5-element array. Write out exactly what you did, step by step.
1. Generalize: how does your hand-solved approach extend from "2nd largest of 5" to "5th largest of n"? What stays the same, what has to change?
1. Share with 1-2 partners: compare how you simplified and generalized. Did you both shrink the problem the same way?

## Activity 1: Strategy Walkthrough (30 minutes)

**Problem:** Given an array `a` of numbers and a target value `t`, find two numbers that sum to `t` (that is, `a[i] + a[j] = t`).

Work through these steps **in order, on paper, solo** — no code yet:

1. **Simplify:** solve it by hand for a small sorted array (5-6 numbers).
1. **Find the pattern:** what did you notice while solving the small case that would work for any size array?
1. **Pseudocode:** write out your approach as pseudocode, precisely enough that someone else could follow it without asking you questions.

Pair up and compare pseudocode. Where is your partner's plan clear? Where would you have gotten stuck following it blind? You'll find out for real next.

## Break (10 minutes)

## Activity 2: Silent Pseudocode Handoff (25 minutes)

Your instructor will assign half the room Problem 3 and half Problem 4 below.

1. Alone: simplify, find the pattern, and write pseudocode for your assigned problem — same process as Activity 1, about 10 minutes.
1. Swap pseudocode (not partners you already worked with) with someone who solved a **different** problem than you.
1. Silently — no talking — implement code from your partner's pseudocode alone.
1. Once both of you have working (or stuck) code, talk: did it work? Where was the pseudocode ambiguous or missing a step? Would you have caught that mistake if you'd been narrating it out loud instead of writing it down?

## Activity 3: Interview Breakout (55 minutes)

**Before you start — the full checklist, communication and strategy together:**

*Communication:* restate the problem, ask clarifying questions, state your assumptions, think out loud (brainstorm solutions, explain your rationale, discuss tradeoffs, suggest improvements)

*Strategy:* generate test inputs, simplify the problem if needed, find a pattern, pseudocode before code, check your work after

From here on, this is the full list an interviewer is listening for — not just the communication half from Lessons 1-2.

**Instructions:**

1. Your instructor will assign your partner. One will play interviewer, one interviewee.
1. Work through **Problem 2** as if in an actual interview, hitting the full strategy: test inputs, simplify/pattern, pseudocode before code, check your work at the end.
1. **Interviewer:** note which strategy steps you saw and didn't, then give one specific piece of feedback. **Interviewee:** before swapping, individually jot one line — which step did you skip or rush, and why?
1. Swap roles.
1. Your instructor will assign a new partner. Work through whichever of **Problem 3 or 4** you didn't already do in Activity 2. **This round:** the interviewer fills out the [Peer Interview Rubric](../Assignments/Sample_Rubric.md) — focus especially on the Problem Solving section, which is the strategy half of the checklist above — and this counts toward your 6-of-8 in-class peer interview rubrics. Interviewer submits via the [Peer Interview Rubric form](https://forms.gle/m8j2nLWB3HbgnGGx9); interviewee submits via the [Self-Assessment form](https://forms.gle/6cWUACVPmBtaY4jV8).

**Practice Problems:**

1. Given an array `a` of numbers and a target value `t`, find two numbers that sum to `t` (that is, `a[i]` + `a[j]` = `t`). *(used in Activity 1)*
1. Given 2 arrays of `n` numbers each, find a pair of numbers (one from each array) whose sum is closest to a given target value `t`.
1. Reverse a linked list by reusing the nodes (do not create new nodes).
1. Find the k largest numbers in an array of n numbers. Return them in an array sorted in decreasing order.

<details>
<summary><strong>Interviewer answer key</strong> — for Problems 2-4, don't peek if you're about to be interviewed</summary>

**Problem 2 (closest sum across two arrays):**
- Both arrays are unsorted, non-empty, and may be different lengths.
- Numbers can be negative.
- Assume exactly one closest pair unless they ask about ties — if they ask, say "return any one of them."

**Problem 3 (reverse a linked list in place):**
- Singly linked list unless they ask — if they ask, say "let's assume singly linked."
- List can be empty or have one node — in both cases, the "reversed" list is unchanged.
- No cycles in the input.

**Problem 4 (k largest, sorted descending):**
- Assume `k <= n` (valid input guaranteed).
- Array may contain duplicates — they count individually (e.g. `[5,5,3]`, k=2 → `[5,5]`).
- Array is unsorted; numbers can be negative.

If they ask something not covered here, make a reasonable call and stay consistent for the rest of the round.

</details>

## Debrief (15 minutes)

As a full class: which was harder — writing pseudocode clear enough for someone else to code from blind, or coding from someone else's pseudocode? What does that tell you about how precise your planning needs to be before you start typing in a real interview?

## Exit Ticket (5 minutes)

**Students:** individually, no partner — submit via the [Exit Ticket form](https://forms.gle/hLLsHySp2BT7qXAZ7) before you go.

> In your own words, what's the difference between "finding a pattern" and "writing pseudocode"? Which one do you personally tend to skip or rush?

**Instructor:** watch for students who describe the two steps identically — that usually means they're pattern-matching the vocabulary without actually doing the strategy differently step to step.

## Homework: Strategy Audit

Pick one solution you committed for Lesson 1 or 2's homework. Revisit it the way a real engineer revisits old code — as a pull request, not a rewrite you just paste over the top of.

1. **Branch:** create a new branch off your existing repo (e.g. `strategy-audit`).
1. **Redo it properly**, committing as you go so the steps show up in your history — don't squash into one commit:
   - a commit for your simplified case / pattern-finding notes (a comment or short `.md` file is fine)
   - a commit for your pseudocode
   - a commit (or a few) for the real implementation
   - a commit for tests
1. **Open a pull request** from your branch back to main. Title it like a real one (e.g. "Rewrite: two-sum with proper planning"). In the PR description, write your self-assessment:
   - **Before:** what did past-you actually do? (Probably: started typing immediately.)
   - **After:** where did simplifying, finding the pattern, or pseudocode actually change the outcome — faster, cleaner, fewer bugs?
   - **What I'd tell past-me:** one sentence.
1. **Submit the PR link** via the course tracker. Leave the PR open, don't merge it — it's the artifact.

This doubles as portfolio material: a real PR with a real diff and a real write-up is exactly the kind of GitHub activity the [Resume, Portfolio & LinkedIn Checklist](../Assignments/Resume-Portfolio-LinkedIn-Checklist.md) tells you to have.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.


