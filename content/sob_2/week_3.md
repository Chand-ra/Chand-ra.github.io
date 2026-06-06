---
title: "SoB Week 3"
date: 2026-06-6
---

## Overview

During week 3 of SoB, the majority of my time was spent addressing feedback on the PR for the implicit dependency issue and implementing the initial steps of the Effectiveness Evaluation Framework.

## Goals Accomplished

- **Got the solution to the implicit dependency issue merged:** This consumed a large chunk of my time last week, but I finally saw it through to completion (yay!). Quite a few changes had to be made to my initial solution and framework, but I am glad to finally have this issue resolved. You can view the merged PR [here](https://github.com/morehouse/smite/pull/97). I also left a brief comment on the original issue detailing exactly what was implemented and what was left out, just in case we need to revisit it in the future (see it [here](https://github.com/morehouse/smite/issues/75#issuecomment-4637418789)).

- **Refactored the `GeneratorInsertionMutator` code to be easily extensible:** Most of the work for this mutator was finished the week prior, but I was unsatisfied with the architecture because it wasn't easily extensible for new Generators. After spending some time revising the code, I feel much better about its current state. The only remaining task is to add tests.

- **Created a developer-facing version of the Evaluation Framework:** While the Effectiveness Evaluation Framework has been more or less complete for a while, it was written from a research perspective, making it cognitively draining for most developers to parse. I discussed the practical use cases with Matt and Nishant, who clarified that its primary purpose would be evaluating the effectiveness of newly added mutators. Consequently, I spent time extracting the relevant components and redesigning the framework to optimize for this specific scenario using coverage analysis.

  I ultimately published a detailed GitHub issue that walks through the problem, explains each statistical tool in necessary detail, and provides clear examples (view it [here](https://github.com/morehouse/smite/issues/115)). Matt liked the overall framework and left some comments, which I have already addressed. At this point, I can safely assume the core framework is finalized.

- **Responded to feedback on mutator tests improvement PR:** A while ago, I pushed a small [PR](https://github.com/morehouse/smite/pull/95) with minor improvements to the existing mutator tests. Matt recently provided some feedback on it, which I have now addressed. Hopefully, it will be merged soon.

- **Started implementing the Evaluation framework:** I started with actually implementing the Effectiveness Evaluation Framework, specifically the orchestration parts. I'm first trying to pick a small, known vulnerability and building the end-to-end pipeline for that vulnerability rather than tackling everything at once. This hopefully makes things easier. I have already implemented the initial parts of this end-to-end pipeline, hope to finish it in the upcoming week. 

## Next Week's Goals

- **Implement tests for `GeneratorInsertion` and `InstructionReorder` mutators:** The implementation for both mutators is complete, but their unit tests are still pending. I intended to write them this week but couldn't find the time. Now that the blocking implicit dependency issue is out of the way, I am rolling this task over to next week, where I hope to finally complete it.

- **Update `InstructionDeleteMutator` to respect affine rules:** We decided to have the mutators respect affine rules by construction, rather than letting them bend the rules and catching the errors in the validator. There was a lot of back-and-forth on this; I was personally against it, but I ultimately conceded to Matt, as he understands the Lightning Network and Smite's future better than I do. Hopefully, he is right and we won't need to revisit the IR's architecture again.

- **Continue implementing the Evaluation Framework:** The initial orchestration steps for the single pilot bug are done, but there is still a massive amount of work required to finish the single-bug pipeline and eventually extend it to the entire Smite target suite. It is a tall order, but I will try to tackle a good portion of it in the upcoming week.

- **Create the developer-facing evaluation script:** With the architecture for the developer-facing evaluation framework finalized, the next step is to create the script that will execute the end-to-end evaluation. I plan to write this in Python, so the coding itself shouldn't be too heavy, though the actual data gathering will require some wrestling. For now, I will focus solely on writing the evaluation script; integrating it with the existing fuzzing orchestration isn't strictly necessary yet, but I will attempt it if time permits.

- **Start implementing the `SpliceMutator`:** I probably won't get to this next week, but I want to jot it down as a reminder. The `SpliceMutator` is the only mutator left to implement, and it happens to be the most complex one. Based on my work with the other mutators so far, I have high hopes for this one, I suspect it will end up being the most significant mutator of all. I will definitely aim to complete it by the end of the month.

- **Triage the CLN memory crash:** I discussed this with Matt, and he had a few ideas. I investigated it lightly this week but to no avail. I will try to give it another go next week.

## Challenges

I originally planned for the entire project (writing new mutators + the Effectiveness Evaluation Framework) to take about 1.5 months, but I now realize I may have underestimated its scope. This is partly because the implicit dependency issue sprang up out of nowhere, and partly because I decided to pursue structuring this project as a formal research paper. At this rate, it is unlikely I will be able to address the "stretch goals" from my proposal. However, I think that is perfectly fine; the depth of the project ultimately matters more than the breadth. Besides, the custom scheduler mentioned in the stretch goals would probably be more enjoyable as a standalone project anyway.

---

[Mike Schmidt from Brink](https://www.linkedin.com/in/mschmidty) saw my vulnerability disclosure post on [delvingbitcoin.org](https://delvingbitcoin.org/) and invited me to discuss it on the [Bitcoin Optech Podcast](https://bitcoinops.org/) (specifically, the [Newsletter #407 Recap Podcast](https://bitcoinops.org/en/podcast/2026/06/02/)). It was my first time appearing on a podcast, so I was pretty nervous and pretty sure I bombed it, but I had a fun time nonetheless.

_Till next time,_

_Chandra._
