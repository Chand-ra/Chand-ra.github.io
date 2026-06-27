---
title: "SoB Week 6"
date: 2026-06-27
---

## Overview

This week, most of my time was devoted to formally enlisting bugs for each target into the evaluation framework. Beyond that, I got all of my remaining upstream PRs merged, filled out the mid-term SoB evaluation form, and wrote the corresponding mid-term blog post.

## Goals Accomplished

- **Created final vulnerability lists for all the targets:** Last week, I compiled the initial bug lists for all four targets. Following up on that, this week's task was to evaluate those bugs, integrate the eligible ones into our framework, and prune the rest. Triage and integration took about a day per target, meaning the entire process took until Thursday to complete. The good news is that the work is finally done, and our evaluation framework is more or less ready for actual experiments! The final bug counts for the targets are: CLN-11, LND-7, LDK-7, and Eclair-6.

- **Got `GeneratorInsertionMutator` merged:** After pushing this upstream late last week, it has already been merged into `master`. It was surprising that this mutator didn't require nearly as many rounds of feedback as the others, but that is likely because its core logic is relatively straightforward compared to the previous mutators. You can view the merged PR [here](https://github.com/morehouse/smite/pull/126).

- **Got the evaluation script merged:** This script was also pushed upstream last week and had already undergone substantial discussion. I ironed out a few remaining minor details at the very start of the week, and the PR has now been merged. You can view it [here](https://github.com/morehouse/smite/pull/125).

- **Started `SpliceMutator` implementation:** With about a day left in the week after finishing bug integration, I finally got started on the final mutator: `SpliceMutator`. I focused on building the necessary infrastructure to support it and managed to wrap that up in a single day. All that remains now is implementing the core mutation logic and writing tests, which shouldn't take more than a couple of days. Once finished, I will have formally completed all "mergeable" code for my project, leaving only the experiments.

- **Filled the mid-term evaluation form:** This week marks the halfway point of the program, and mid-term evaluation forms were sent out to all contributors. I spent some time detailing the work I've completed so far, outlining current blockers, providing links to my artifacts, and answering the related evaluation questions.

- **Created SoB mid-term blog post:** A new initiative this year is that SoB encouraged contributors to write a mid-term blog post about their progress for the official SoB blog. I took the opportunity to draft a post detailing my project's scope and my achievements so far. You can view the corresponding PR [here](https://github.com/SummerOfBitcoin/summerofbitcoin.github.io/pull/14).

## Next Week's Goals

- **Finish implementing the `SpliceMutator`:** This is my primary objective for next week, as it will officially conclude my core coding obligations. As mentioned, the remaining tasks are implementing the core mutation logic and writing unit tests. It shouldn't take more than a couple of days to knock out.

- **Start working on the initial sections of the paper**: Running the actual evaluation framework for the IR scenario is still a ways off, as it hasn't matured enough yet to detect interesting bugs. While other contributors continue working on that, I plan to start drafting the first few sections of the actual research paper. Hopefully, the IR will be fleshed out enough by the time I need it.

- **Port the orchestration script to Smite:** I have already created a few orchestration scripts for the formal evaluation framework to run trials automatically. I discussed the possibility of writing something similar for Smite in Rust with Matt; he wasn't aware of similar built-in functionality in Rust and noted that Python is perfectly fine as long as it gets the job done.

  With that in mind, I plan to port the orchestration script to Smite, which will be a huge relief for developers. Once integrated, users will just need to run the two scripts in sequence without worrying about underlying directory structures. I am currently waiting for a `smitebot run` command to land in `master`, which will make the script even easier to formulate. I will create the orchestration script as soon as that lands.

- **Create documentation for evaluation script:** The evaluation script itself is cleanly and vividly documented inline, ensuring anyone using it can easily understand how to run it and interpret the output. However, this documentation currently lives inside the script file itself, meaning a newcomer wouldn't know it exists unless they hunt for it. I want to create external documentation pointing developers to this feature, so I will discuss the best format with Matt and hopefully get to work on it.

- **Test vulnerability patches:** While the vulnerabilities are integrated into our evaluation framework, I haven't had time to test whether they all compile end-to-end, as spinning up 31 separate Docker instances takes too much time. It should be fine to do this right before running the campaigns, but I plan to manually test some of the more break-prone changes before deploying them on the actual test machine.

- **Triage the CLN memory crash:** Couldn't find the time for this (yet again), so I am carrying it over to next week (yet again).

## Challenges

Triaging the bugs turned out to be just as much of a headache as finding them. Many of them reside in areas like RPC APIs, on-chain logic, or pure business logic, which a fuzzer cannot easily discover without highly sophisticated oracle mechanisms. I originally curated 10–15 bugs per target, but after pruning the non-relevant ones, I was left with an average of about 8 per target. While that is perfectly fine for a rigorous ground-truth analysis, I was really hoping to see around 40 bugs make it into the final framework. Oh well, I can always devote some time to sourcing more bugs later if the need arises (though I probably won't).

_Till next time,_

_Chandra._
