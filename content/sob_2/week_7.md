---
title: "SoB Week 6"
date: 2026-06-27
---

## Overview

This week, most of my time was spent writing the Design section of the research paper. I also pushed the final mutator, `SpliceMutator`, upstream.

## Goals Accomplished

- **Finished implementing SpliceMutator and pushed it upstream:** I managed to complete this by Monday. Having already finished the difficult infrastructural work for this mutator last week, only the core logic and unit tests remained, which I knocked out on the very first day. I pushed the resulting PR upstream, received some initial feedback, and responded to it promptly. It shouldn't be long before this final mutator is merged into the existing suite. You can view the open PR [here](https://github.com/morehouse/smite/pull/135).

- **Finished the design section of the paper:** I finally began drafting the paper, opting for an inside-out approach. The very first section I tackled was the IR Design. Since this was already more or less outlined in Smite's IR Design and Architecture plan, my main task was translating that prose into a more formal, academic register. This section comprised about five subsections, and I was able to knock all of them out this week, a huge milestone. Next up is the Implementation section, which I hope to finish just as quickly.

## Next Week's Goals

- **Continue working on the paper**: Finishing the Implementation section is my immediate priority for the upcoming week. This will be more difficult than the Design section because there is no readily available documentation to pull from; I will have to scour the actual codebase to detail this part accurately. Hopefully, it takes no longer than a week.

- **Test vulnerability patches:** While the vulnerabilities are integrated into our evaluation framework, I haven't had time to test whether they all compile end-to-end, as spinning up 31 separate Docker instances takes too much time. It should be fine to do this right before running the campaigns, but I plan to manually test some of the more break-prone changes before deploying them on the actual test machine.

- **Triage the CLN memory crash:** Couldn't find the time for this (yet again), so I am carrying it over to next week (yet again).

## Challenges

Writing the actual paper turned out to be harder than I anticipated. However, starting with the IR Design section was a smart move; because I am already deeply familiar with the material, I could focus my cognitive effort on refining the academic prose, structuring arguments, and clearly laying out design choices. The Design section ended up spanning five pages, and I am fairly certain I will have to trim it down significantly for the final draft. Still, I am happy that the core writing for this portion is done for now.

_Till next time,_

_Chandra._
