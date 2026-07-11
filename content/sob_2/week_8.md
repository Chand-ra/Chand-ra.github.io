---
title: "SoB Week 8"
date: 2026-07-11
---

## Overview

This week, most of my time was spent writing various sections of the research paper and creating an orchestration script for the developer-facing evaluation framework.

## Goals Accomplished

- **Responded to `SpliceMutator` feedback:** I received and addressed the initial feedback on this mutator last week. After a couple more rounds of review this week, the code was deemed finalized. It hasn't been merged just yet, as we first need to prove its efficacy using the evaluation script, but it is ready to go. You can view the PR [here](https://github.com/morehouse/smite/pull/135).

- **Finished various sections of the paper:** After completing the Design section last week, my goal was to tackle the Implementation section. I managed to finish it this week, though it is still quite a rough draft; I will need to trim down a lot of unnecessary implementation details. In addition to that, I completed a good portion of the Evaluation and "Background and Related Work" sections.

- **Started implementation of the developer-facing orchestration script:** I discussed the idea of adding documentation for the evaluation script with Matt and Nishant during our meeting this week. Matt mentioned he would prefer to hold off on documentation until we figure out a way to automate the creation of the required results directory for the evaluation script. Since I already have a similar script in my formal evaluation framework, I decided to port it over for this exact purpose. The work is well underway, and while I believe I have overcome the major obstacles, there are still quite a few things left to do before the script can be considered "finalized."

## Next Week's Goals

- **Continue working on the paper**: Only a couple of sections remain before I reach the parts that require actual experimental data. I hope to finish drafting those by next week. Since this is a first draft, a lot of material will need to be trimmed, but editing should definitely be easier than writing it all from scratch.

- **Finalize the orchestration script:** While the major hurdles are cleared, there is still work to be done before this script is fully baked. I need to ensure it works seamlessly across all targets and possible scenarios, fixing any breakages along the way, before I can push it upstream.

- **Rent the fuzzing hardware:** It is finally time to rent the hardware I will use for the fuzzing trials. Even before the actual campaigns begin, there is a massive amount of prep work required, making this the right moment to secure the actual machine. I will run the baseline trials using the `encrypted_bytes` scenario first, allowing the IR to mature as much as possible before running trials on it.

- **Triage the CLN memory crash:** Couldn't find the time for this (yet again), so I am carrying it over to next week (yet again).

## Challenges

Implementing the developer-facing orchestration script turned out to be more of a pain than I anticipated. A major reason for this is my decision to use the `smitebot start` feature recently introduced to Smite, rather than porting my own `run_trial` script (which just runs a single trial). The `smitebot` feature does a whole bunch of unnecessary stuff that I am now forced to hack my way around. In hindsight, it probably would have been much easier to just port my `run_trial` script, but what's done is done. I will try to see the current script through as-is, unless a rewrite becomes absolutely necessary.

_Till next time,_

_Chandra._
