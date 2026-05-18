---
title: "SoB Week 0"
date: 2026-05-18
---

## Overview

The program Kick-Off and Onboarding Period ran from May 11 to May 15, 2026. After handling the required paperwork, I got an early start on the project, kicking things off with an initial meeting with my mentors, Matt and Nishant. Ultimately, I invested the majority of my time this week in solving the implicit IR dependency issue.

## Goals Accomplished

- **Got up to speed with Rust:** It had been a while since I last used Rust (you could say I was a bit rusty on Rust 😉), so I spent the first few days of the Onboarding Period (before my meeting with Matt and Nishant) solving LeetCode-style problems. While I would have liked to tackle a few more, this practice proved to be quite useful.

- **Responded to feedback on `InstructionDeleteMutator`:** I addressed the feedback Matt provided on the new [`InstructionDeleteMutator` PR](https://github.com/morehouse/smite/pull/60), which I had pushed upstream before the program started. However, during this process, we discovered an implicit dependency issue in Smite's IR that would cause the mutator to invalidate the program's semantics. Merging this PR is currently blocked until we resolve the issue.

- **Responded to feedback on `OperationParamMutator` tests:** I also received feedback on the unit tests I introduced for OperationParamMutator prior to the program's start (see PR [here](https://github.com/morehouse/smite/pull/55)). I had to weed out a large portion of the tests I initially wrote; fortunately, they were duplicating behavior, so nothing of value was lost. I believe the work for this PR is now complete, but time will tell.

- **Created a GitHub for the IR dependency problem:** The first step toward solving the blocker for advanced structural mutators was to formulate and describe it clearly enough for other contributors to weigh in. I opened a new issue ([Issue #75](https://github.com/morehouse/smite/issues/75)) in the repository detailing the background, the problem, and our goals for resolving it, complete with references to the original discussions where the issue was first identified.

- **Formulated a solution for the IR dependency problem:** Finding a solution for the aforementioned issue took up the bulk of my time last week. After brainstorming multiple ideas, I finally settled on utilizing the existing input-output dependency graph alongside affine state-tokens.

  I tested the proposed solution against various scenarios, and it holds up well, though there may be edge cases I missed. I have posted the solution in the issue thread and am waiting for feedback to catch any potential oversights. Additionally, I laid out an implementation plan that should serve both as a roadmap if the solution is accepted and as a clear indicator of the necessary changes for the reviewers.

- **Finished the paperwork:** I signed the necessary starting agreements and updated my Summer of Bitcoin profile with my latest information to formalize my participation. With the administrative tasks out of the way, I can now focus entirely on delivering milestones during the contribution period.

- **Streamlined goals and expectations:** During my meeting with Matt and Nishant, I ironed out some confusing details regarding the program, specifically concerning the Effectiveness Evaluation Framework and the overall expectations for this project. I informed Matt of my goal to eventually publish the results as a formal paper, and he agreed to help find someone to assist me with that process. While we haven't had much luck yet, I remain hopeful we will find someone before I need to actively use the framework.

## Next Week's Goals

- **Advance the work on Effectiveness Evaluation Framework:** I am currently waiting for someone with an academic background to review my plan for statistically analyzing the effectiveness of our new structural mutators; further work is pending until this review is complete. I will try to reach out to more potential reviewers this week, but if I do not hear back, I will spend next week streamlining the framework myself to the best of my ability. Ultimately, the framework needs to be posted as a GitHub issue so other contributors can use it to evaluate their own mutator configurations. 

- **Finalize the solution to the IR dependency issue:** This remains the single biggest hurdle to the project. If we cannot resolve it, there is a very real possibility that the project could be scrapped entirely. I have already proposed a solution and am hoping the other contributors are on board. I will make sure to respond quickly to any feedback on the plan, aiming to finalize it this week so I can begin implementation.

- **Start working on `GenerationInsertionMutator`:** In my proposal, `GenerationInsertionMutator` was the first advanced mutator I planned to tackle during the contribution period. I will start this right away because, unlike some others, it can be tested immediately, even without a large pool of IR programs currently available. Having already laid out the logic for this mutator in my proposal, the implementation shouldn't take more than a couple of days.

- **Add improvements to mutator tests**: While addressing the feedback on my new `InstructionDeleteMutator` PR, I realized that much of the critique could be applied to our existing mutator tests as well. I plan to implement these improvements and create a new PR for them next week.

## Challenges

The IR dependency problem turned out to be far more complicated and time-consuming than I initially anticipated. Regardless, I believe I have identified the core of the necessary solution: introducing specific state tokens to the existing IR. While the finer details are still a bit hazy and I wish I had spent more time brainstorming alternatives, I am glad I managed to figure out the essential mechanism. Once finalized, implementing the solution shouldn't be too difficult.

Meanwhile, work on the Effectiveness Evaluation Framework has stalled, primarily because we haven't found an academic reviewer yet. This delay is largely due to my ambition to publish the results as a formal paper, which would be immensely helpful for my dissertation later on. However, if no one responds soon, I will consider proceeding on my own. My primary objective remains completing the project within the scope defined in my proposal, everything else is secondary.

_Till next time,_

_Chandra._
