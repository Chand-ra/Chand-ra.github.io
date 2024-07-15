This week marks week 7 of GSoC's official Coding Period. Similar to the previous few, the majority of my time this week was devoted to writing code for the reftable tests in the unit testing framework.

## Goals accomplished
- **Work on porting readwrite test to the unit testing framework**: Most of the work for this test was completed last week, but there were still a few finishing touches that I wished to add. These are still in-progress and should not take too long to complete.
- **Finish porting tree test to the unit testing framework**: The patch for this test was already reviewed by Patrick and Christian some weeks ago but wasn't merged to upstream for some reason. I've modified the patch again to include test renames and plan on sending the updated patch next week.
- **Finish porting stack test to the unit testing framework**: Most of the work for this test was completed last week, but there were still a few finishing touches that I wished to add. I finished all my planned work for this test this week and the patch is ready to be sent to the mailing list.
- **Work on feedback from the mailing list**: I sent the patch series for merged test migration to the mailing list this week and received feedback on it. I addressed almost all the feedback received, and sent the patch series back to the mailing list. Hopefully it's in a good enough position to be merged to upstream by now.

## Next week's goals
I have finished the work for six tests (merged, tree, pq, record, block and basics) until now, but only two (basics and record) has been merged with upstream. Hence, similar to last week, one of my goals for the next week is to get more tests merged with upstream. Other than that, I will try to finish the work on the remaining tests.

## Challenges
Like last week, this one was more or less a smooth sailing as well. I did face some small issues here and there but was able to get over them due to the experience I accumulated from the work I performed in the last few weeks. Hopefully I can continue to do the same in the future.

_Till next time,_

_Chandra_.
