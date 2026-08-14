# AI-Assisted Coding and Interviewing

## Why This Matters

By the time you're interviewing, AI coding tools (Copilot, Claude Code, Cursor, and similar) will be a normal part of a working developer's toolkit — employers expect you to know how to use them. But hiring pipelines have adapted: many technical interviews now explicitly restrict or ban AI assistance during live rounds, take-homes often *require* you to disclose what you used, and interviewers increasingly ask pointed follow-up questions specifically designed to check whether you understand code an AI helped you write. Being fluent with AI tools and being able to code and reason without them are both things you'll be evaluated on — often in the same interview loop.

## Learning Outcomes

By the end of this session, you will be able to...

1. Identify when AI coding assistance is expected, allowed-with-disclosure, or banned in a given interview format
1. Disclose AI tool use honestly and confidently, without undermining your own credibility
1. Explain and defend code you produced with AI help, including lines you didn't type yourself
1. Use AI tools productively during *practice* without shortcutting the learning you need for live, unassisted rounds

## Warm-Up (10 minutes)

With a partner, discuss:

- What AI coding tools do you currently use, if any? For what kinds of tasks?
- Have you ever used one during a timed practice problem or an actual interview? What happened?
- Would you trust code you generated with AI help if you had to explain it line-by-line to someone right now, with no tool open?
- Do you have a paid AI subscription (ChatGPT Plus, Claude Pro, Copilot, Cursor Pro), or are you on free tiers? Has that made a noticeable difference in what you can do?

**A note on access:** paid tools aren't required for this course or for interviews. Free tiers of Claude.ai and ChatGPT are genuinely capable for problems at this level, and GitHub's Student Developer Pack gives verified students free Copilot access — worth checking if you haven't. If cost is a barrier for today's activities, use a free tier or pair with a partner who has one. What an interviewer evaluates is whether you can use *a* tool competently and explain the result — not which tool, and not whether you've never touched one before today. If that's you, say so to your partner up front and work through the prompting together for Activity 2.

## Activity 1: Know the Format (15 minutes)

Interview formats handle AI differently, and getting this wrong is an easy way to look either naive or dishonest. As a class, sort these formats into **AI banned**, **AI allowed with disclosure**, and **it depends — ask** :

1. A live coding round on a shared screen with an interviewer watching
1. A timed assessment on a proctored platform (e.g. CodeSignal, HackerRank, Karat) with lockdown browser/webcam
1. A take-home project with a multi-day deadline
1. A system design conversation
1. Debugging someone else's code during a pairing round
1. A personal portfolio project you're asked to walk through

**Discuss:** Proctored platforms increasingly detect AI use directly (tab switching, paste volume, phone/second-screen detection). Assuming you can get away with unauthorized AI use is a bad bet — and even where it's technically undetectable, getting caught later (e.g. failing to explain your own solution) costs you more than a slower, honest answer would have.

## Practice Problems

You'll use these across Activity 2 and tonight's homework — between the two, plan on all four getting solved by the end of the day.

1. [Two Sum](https://leetcode.com/problems/two-sum/): Given an array of integers and a target, return the indices of the two numbers that add up to the target.
1. [Group Anagrams](https://leetcode.com/problems/group-anagrams/): Given an array of strings, group the anagrams together.
1. [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/): Find the longest common prefix string amongst an array of strings.
1. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/): Find the contiguous subarray with the largest sum.

## Activity 2: The Explain-It-Back Drill (35 minutes)

This simulates the single most common way interviewers catch candidates who over-relied on AI: asking them to explain, modify, or extend code they didn't fully understand. **This is the failure mode that sinks more candidates than any actual bug does** — producing working code you can't defend. If you get through this drill and realize you couldn't explain your own solution when a partner read it back to you, that's not a fun surprise to save for a real interview. That's exactly why this drill exists.

**Instructions:**

1. Pick one of the four practice problems above.
1. Solve it **using an AI tool** as you would for a take-home — prompt it, accept/edit its output, get to a working solution. (No AI tool set up yet? See the access note in the Warm-Up.)
1. Swap with a partner. You now have *their* AI-assisted solution, not your own.
1. Without asking them anything first, read their code and prepare to:
   - Explain what each function/section does, in your own words
   - Identify the time and space complexity
   - Propose one edge case their solution might not handle
   - Suggest one alternative approach
1. Present your explanation to your partner (the original author). They grade you on accuracy — did you actually understand it, or fake it?
1. Switch roles and repeat with your partner explaining your solution back to you.

**Debrief:** What was hard to explain? Where did you (or your partner) end up guessing? That gap is exactly what a live "why did you write it this way" follow-up question will expose.

## Activity 3: Disclosure Language (15 minutes)

Practice saying these out loud with a partner, then adapt them into your own words:

- *"I used [tool] to help scaffold this function, then reviewed and adjusted the logic myself — happy to walk through any part of it."*
- *"For this take-home, I used AI to help me look up the syntax for X, but the approach and logic are mine."*
- *"I didn't use any AI assistance for this round, per the instructions — let me know if you'd like me to think out loud more as I go."*

Notice these are short, factual, and don't apologize or over-explain. Practice one for a take-home and one for a live round.

## Homework

Solve the 3 practice problems from above that you didn't already use in Activity 2.

1. Solve 2 of them **without any AI assistance** — pseudocode, code, and test cases entirely your own.
1. Solve the 3rd **with AI assistance**, and write a short reflection (3-5 sentences) submitted via the course tracker:
   - What did the AI tool get right or wrong?
   - What would you have done differently on your own?
   - **Which line(s) of the AI-assisted solution could you *not* confidently explain or defend if asked right now?** Naming this honestly is the actual point — most candidates who get caught didn't lie, they just never checked.
   - Write the one-sentence disclosure you'd give an interviewer for this solution.
1. Commit all solution code, your reflection, and your test cases to a GitHub repository and submit the link via the course tracker.

## Wrap-Up

Fill out the class feedback form with any thoughts & feelings from class today that you'd like your instructors to know.
