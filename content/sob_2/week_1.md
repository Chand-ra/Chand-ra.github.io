---
title: "SoB Week 1"
date: 2026-05-25
---

## Overview

This week marked the official start of Summer of Bitcoin. Week 1 was primarily focused on solving the implicit IR dependency issue. The final architecture for the solution has been approved, and the implementation is nearly complete.

## Goals Accomplished

- **Finalized the solution to the IR dependency issue:** This was the single biggest hurdle facing the project. Thankfully, my proposed solution was deemed viable by Matt and the rest of the community. While I initially wanted to iron out a few more details and edge cases before finalizing the architecture, Matt suggested we start small and implement the architecture as is. This initial version is sufficient to resolve the issues with the current mutators, and we can extend or modify it later if the need arises.

  The agreed-upon solution and the surrounding discussions can be found in [Issue #75](https://github.com/morehouse/smite/issues/75).

- **Implemented the solution to the IR dependency issue:** With the solution finalized by Wednesday, I dedicated the rest of the week to implementing the plan. The work turned out to be more involved than expected, taking up more time than I originally anticipated. However, as of writing this post, the implementation is nearly finished. Only a couple of minor improvements remain, which should be completed by tomorrow at the latest.

- **Tuned the effectiveness evaluation framework:** Last week, I decided that if I didn't hear back from any of the potential reviewers, I would streamline the framework myself. Since I haven't received any replies, I took the initiative to refine it on my own. To guide this effort, I comprehensively reviewed the Klees et al. paper on evaluating fuzzers and noted key points for building a robust framework. While there is still a lot of work left, I have made a solid start and hope to see it through to completion over the next couple of weeks.

- **Added improvements to mutator tests:** While addressing feedback on the [`InstructionDeleteMutator` PR](https://github.com/morehouse/smite/pull/60) last week, I realized much of the critique applied to our existing mutator tests as well. I implemented these broader improvements toward the end of the week, resulting in [PR #95](https://github.com/morehouse/smite/pull/95).

- **Got the `OperationParamMutator` tests PR merged:** I successfully addressed all the feedback on the [`OperationParamMutator` test improvements](https://github.com/morehouse/smite/pull/55) that I pushed upstream prior to SoB, and the PR was finally merged into `master`. It feels good to get one of the pending upstream tasks out of the way.

## Next Week's Goals

- **Advance the work on Effectiveness Evaluation Framework:** Diving into this framework has made me realize it is a much larger undertaking than I initially thought. While the statistical tests used to compare different runs aren't too difficult, and I have already noted them down, evaluating the different runs against a ground truth will require significant engineering effort. We will likely need to find a way to systematically isolate and introduce bugs into the various targets of our fuzzing campaigns.

- **Implement the `GenerationInsertMutator`:** I initially planned to implement the first custom mutator within the first two weeks of the program. Since the first week was entirely consumed by the implicit dependencies issue, I now have only one week left to stay on track with my original timeline. Fortunately, the mutator isn't overly complex to build, and I already have a solid mental model of my approach. I am confident I can complete its implementation in the upcoming week.

- **Get the solution to the IR dependency issue merged:** Although the implementation is done, I expect significant back-and-forth during the code review. It is a large PR (8 commits in total) that touches many different areas of the codebase. Responding to this feedback will be my top priority throughout the week, as getting this merged is absolutely pivotal for the rest of the project's success.

## Challenges

My relative inexperience with Rust proved to be quite a thorn, and I believe it is the primary reason the IR dependency solution took as long as it did to implement. However, I now feel much more comfortable with the language than I did at the start of the project. While using AI to write parts of the code might have sped up the process, I am glad I opted for the old-school approach. It was a lot more fun, and the hands-on experience means I can write code faster and better moving forward.

I am also feeling a bit anxious about the Effectiveness Evaluation Framework, as it is essentially a race against time. The sooner the framework is established, the more time I will have to run fuzzing campaigns. This is crucial for the project, as we have decided to run a large number of trials with 24-hour timeouts for each configuration. That said, I refuse to compromise on the framework's rigor; drawing incorrect conclusions from a flawed framework is worse than drawing no conclusions at all. To stay on track, I will need to switch gears and dedicate more time to this specific aspect of the project.

_Till next time,_

_Chandra._
