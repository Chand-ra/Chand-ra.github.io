---
title: "SoB Week 5"
date: 2026-06-20
---

## Overview

This week of SoB was more spread out than previous ones. I tackled a variety of areas across the project, making some very real progress in the process. This sprint brings me incredibly close to finishing my portion of the project.

## Goals Accomplished

- **Finished `InstructionReorderMutator` and got it merged**: Last week, I planned to finish writing the pending tests for this mutator. I managed to knock them out in a day or so, and after a couple of rounds of feedback, I am elated to say it has finally been merged upstream. This was the first custom mutator I wroteand something I had been working on since before SoB so I am thrilled to see it completed. You can view the merged PR [here](https://github.com/morehouse/smite/pull/61).

- **Got `InstructionDeleteMutator` merged:** The `InstructionDeleteMutator` was next to cross the finish line. Although I actually completed this one long before the `InstructionReorderMutator`, it was held up by the IR dependency issue and required significantly more feedback. Regardless, I am happy this work is finally wrapped up as well. The merged PR is available [here](https://github.com/morehouse/smite/pull/60).

- **Pushed `GeneratorInsertionMutator` upstream:** The only remaining task for this mutator was writing its tests. I finished them this week and pushed the code upstream toward the weekend. Because it went up later in the week, I haven't received any feedback yet, but I am hoping to get it merged soon. You can view the resulting PR [here](https://github.com/morehouse/smite/pull/126).

- **Created and pushed the developer-facing evaluation script:** This was a crucial piece of the project that had been pending until now, but exactly as planned, I finally completed it. I wrote the full end-to-end effectiveness evaluation script in Python, fully documented it, and pushed it upstream. The script ingests a structured directory of AFL++ output, automatically handles time-series interpolation, computes Mann-Whitney U tests and Vargha-Delaney A12 effect sizes for final coverage and AUC, and controls for family-wise error rates using the Holm-Bonferroni method. It then outputs a Markdown report, CSV metrics, and visual diagnostics.

  Matt reviewed it and was pleased with the output and overall architecture; we just have a few small details to iron out before it (hopefully) merges next week. The PR is [here](https://github.com/morehouse/smite/pull/125).

- **Created the formal evaluation framework's coverage evaluation script:** After finishing the developer version of the coverage-analysis script, I ported it over to the formal framework I will use for my research paper. It is essentially the same script, just with a few architectural tweaks to make it compatible with the rest of the formal framework. The actual script can be accessed [here](https://github.com/Chand-ra/smite-evaluation/blob/master/analysis/coverage_analysis.py).

- **Streamlined the evaluation framework's analysis pipeline:** I realized much of the feedback on the developer-facing pipeline applied directly to my formal framework's analysis pipeline as well. I took some time to incorporate those improvements, especially into the existing survival-analysis script, resulting in a much more robust and presentable pipeline.

- **Found the initial bug set for all the four targets:** The immediate next step for the actual evaluation experiments is curating real, historical vulnerabilities for all four targets. I completed the first pass of this curation this week. I now have a working list of relevant vulnerabilities; all that remains is determining which ones fit our ground-truth evaluation and pruning the rest.

## Next Week's Goals

- **Triage the found bugs to create the final corpus:** With the overarching bug set finalized for each target, I now need to filter out the ones that do not meet our strict criteria. During my pre-auditing, I found 10-15 relevant bugs per target. Next week, I will delve deeper to curate the final evaluation list and formally enlist these bugs into our framework.

- **Start implementing the `SpliceMutator`:** I haven't had time to start this yet, but the good news is that every other mutator is largely finished and merged upstream. Once `GeneratorInsertionMutator` merges, I can direct my full focus to this final mutator, making it much easier to knock out quickly.

- **Start working on the initial sections of the paper**: Running the actual evaluation framework for the IR scenario is still a ways off, as it hasn't matured enough yet to detect interesting bugs. While other contributors continue working on that, I plan to start drafting the first few sections of the actual research paper. Hopefully, the IR will be fleshed out enough by the time I need it.

- **Triage the CLN memory crash:** Couldn't find the time for this (again), so I am carrying it over to next week (again).

## Challenges

Finding vulnerabilities in the various Lightning implementations turned out to be a much bigger pain than I anticipated. The implementations rarely disclose every bug they fix, and many are patched silently under the hood. Ultimately, I had to resort to scouring changelogs and release notes to find enough candidates for my ground-truth framework. I'm not even entirely sure I have enough yet; I'm just hoping I do so I don't have to repeat this menial work.

_Till next time,_

_Chandra._
