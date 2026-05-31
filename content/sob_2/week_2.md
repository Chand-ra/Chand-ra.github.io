---
title: "SoB Week 2"
date: 2026-05-31
---

## Overview

In week 2 of SoB, my primary focus was on refining the solution for the implicit dependency issue I tackled last week and finalizing the Effectiveness Evaluation Framework.

## Goals Accomplished

* **Implemented the initial solution to the IR dependency issue:** The bulk of the implementation for this issue was completed last week, but I finished a couple of remaining minor tweaks this week and pushed the resulting PR upstream as [PR #97](https://github.com/morehouse/smite/pull/97).

* **Updated IR documentation:** A major lingering step from last week's IR dependency work was updating the existing IR design and implementation plan. Since the original plan was outlined in a GitHub issue, I couldn't simply edit the main post. I discussed the best approach with Matt during our Tuesday meeting, and per his suggestion, I left the changes as a comment in the issue thread, which you can see [here](https://github.com/morehouse/smite/issues/5#issuecomment-4551877206).

* **Finalized the Effectiveness Evaluation Framework:** This consumed the largest portion of my time this week. My initial evaluation plan required significant revisions and fine-tuning, but I am glad to report that I finally have a concrete structure. While a few minor issues might still surface, I do not foresee needing to revise the core architecture again. I can now finally shift my focus to actual implementation.

* **Implemented `GeneratorInsertionMutator`:** To stay aligned with my proposal timeline, I dedicated half a day to building the `GeneratorInsertionMutator`. As I suspected, this was plenty of time since I had already mapped out the core logic in my proposal. The only task remaining is to add tests for the mutator, after which it will be ready to merge upstream.

* **Responded to feedback on my upstream PRs:** I received some feedback on my upstream PRs, so I spent time addressing and incorporating those changes.

## Next Week's Goals

* **Get the solution to the IR dependency issue merged:** After considerable back-and-forth regarding the future of Smite's IR architecture, we decided to remove the validator. Instead, mutators will now act as sources of truth, similar to generators, meaning they are no longer permitted to mutate programs into invalid structural or semantic states. This was just one of several necessary adjustments, requiring heavy revisions to both the solution's architecture and its implementation.

  Fortunately, these aren't additive changes; for the most part, I just need to downgrade some of the logic I had previously added. I have already begun redoing the implementation and hope to finish by Monday so we can get it merged as quickly as possible.

* **Triage the CLN memory crash:** I discovered a potential memory bug in Core Lightning prior to SoB, but it is highly flaky and difficult to reproduce deterministically, even for the fuzzer. I originally planned to lightly investigate this last week but ran out of time, so I am carrying it over. Realistically, between the evaluation framework and the implicit dependency issue, I might not have much time for it next week either, but I will keep it in the back of my mind.

* **Document the Evaluation Framework:** With the architecture decided, I need to formally document it as a GitHub issue, following my previous discussions with Matt and Nishant. I will sync with them to clarify exactly what details they want included before drafting the write-up.

* **Implement the initial steps of the Evaluation Framework:** Having the architecture locked down is great, but the hard part remains: actually building it. There are numerous trials to run and a significant amount of prep work required before we can execute even a single trial. I absolutely must start on these initial steps next week.

* **Implement tests for `GeneratorInsertion` and `InstructionReorder` mutators:** The implementation for both mutators is complete, but their unit tests are still pending. I will dedicate some time next week to finishing these final pieces so I can offload these mutators from my cognitive bandwidth.

## Challenges

I knew merging the IR dependency solution upstream wouldn't be easy, given that it's a massive PR making fundamental changes to critical parts of the codebase. The first round of feedback came from Matt, and the required revisions proved to be more demanding than I initially thought. Nevertheless, I have implemented most of the changes; primarily, only the tests remain. I am fully committed to seeing this through to completion.

The Effectiveness Evaluation Framework took a massive amount of time, largely because I want it to be comprehensive enough to publish as a formal paper if the results are promising. Achieving that standard requires pinning down extreme levels of detail and anticipating edge cases in statistical frameworks: honestly, a bit beyond what I could brainstorm entirely on my own. I leaned heavily on LLMs to help bridge the gaps, but I believe I've finally gotten the framework into a strong state. I am hoping the most difficult part is behind me, and the sheer amount of effort I've already invested makes me want to see the rest of it through.

_Till next time,_

_Chandra._
