---
title: "SoB Week 4"
date: 2026-06-14
---

## Overview

During week 4 of SoB, I spent most of my time finalizing the end-to-end pipeline for the ground-truth evaluation of the Effectiveness Evaluation Framework.

## Goals Accomplished

- **Got the mutator tests PR merged:** The small PR with minor improvements to the existing mutator tests that I pushed a while ago was finally merged upstream. You can view the merged PR [here](https://github.com/morehouse/smite/pull/95).

- **Finished the evaluation framework for ground-truth evaluation:** This consumed the lion's share of my time this week. After wrestling with build issues, Docker quirks, parallelization headaches, and a myriad of other challenges, I am happy to announce that I finally created the end-to-end evaluation pipeline for all four targets and verified the orchestration on a simulated bug. While the coverage analysis scripts and a few other minor details are still pending (and there are still a few things I'm unsure about( I am fairly confident I have completed the bulk of the required work. At most, only a few modifications remain. Hopefully, the pipeline runs smoothly on the actual test machine. You can view the current status of the framework [here](https://github.com/Chand-ra/smite-evaluation).

- **Updated `InstructionDeleteMutator`:** Last week, we decided that mutators should respect affine rules by construction, rather than allowing them to bend the rules and catching the errors later in the validator. I updated the `InstructionDeleteMutator` accordingly and have already pushed the resulting PR upstream. I also addressed some initial feedback on it and am now just waiting for it to be merged.

- **Created placeholders for `GeneratorInsertionMutator` tests:** While I couldn't find the time to write the entire test suite for this mutator, I did manage to map out the different edge cases and scenarios we will likely want to test—at least all the ones I could think of. I will implement the actual tests next week and push the resulting code upstream.

## Next Week's Goals

- **Implement tests for `GeneratorInsertion` and `InstructionReorder` mutators**: I originally planned to complete this during the current week, but I simply couldn't find the time due to the heavy investment required to pin down the evaluation framework. I have already set up the scaffolding for the `GeneratorInsertion` tests, so I just need to implement them. However, I will have to write the `InstructionReorder` tests from scratch. This will be a top priority for the upcoming week.

- **Create the developer-facing evaluation script:** I realized that this script could be utilized within my original framework, alongside its primary goal of serving Smite developers. As a result, I have delayed this task for now and will simply push the coverage analysis script, which I need to write for the original framework anyway.

- **Start curating bugs for ground-truth evaluation:** With the pipeline construction out of the way, I can finally start looking for historical bug candidates to use in the ground-truth evaluation. I have already discussed with Matt and Nishant which areas of the Lightning Network will be fuzzable by Smite in the near future, so I will focus my search there first. This process will also help me decide whether I should write the research paper now or delay it until Smite matures a bit more.

- **Start implementing the `SpliceMutator`:** As I anticipated last week, I didn't find the time to implement this mutator. I'm not overly worried about it, though, as it is the only mutator left on the docket. I do plan to start working on it in the upcoming week.

- **Triage the CLN memory crash:** I couldn't find the time for this, so I am carrying it over to next week.

## Challenges

Building the end-to-end pipeline turned out to be a nightmare; there were just so many unforeseeable complications. However, I have to admit it was a highly educational experience and something that will undoubtedly benefit me in the future. I am now slightly paranoid that the IR scenario isn't fully fleshed out enough to discover deeper bugs, but alas, that will become clear once I actually get down to bug-hunting.

_Till next time,_

_Chandra._
