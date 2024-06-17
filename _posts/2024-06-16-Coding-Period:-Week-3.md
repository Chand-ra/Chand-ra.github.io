This week marks week 3 of GSoC's official Coding Period. Similar to the previous few, the majority of my time this week was devoted to writing code for the reftable tests in the unit testing framework.

## Goals accomplished
- **Finish porting record test to the unit testing framework**: Most of the work for this test was completed last week, but there were still a few finishing touches that I wished to add. I was able to completely finish the work for these tests by this week, and plan on sending the patch for this to the mailing list next week.
- **Work on porting block test to the unit testing framework**: I decided to work on block test next. Surprisingly, this test took me an entire week to complete and that is mostly because the improvements that I had in mind for this test ended up being more difficult to implement than anticipated. In any case, I was able to finish a large part of my planned work for these tests in this week, and the work should be finished by the next week.
- **Work on feedback from the mailing list**: I sent the patches for tree test and pq test migration to the mailing list this week and received feedback on them. I addressed almost all the feedback received, and both these patches are now in a good enough position to be merged with upstream.
- What I did up until last week.

## Next week's goals
I have finished the work for four tests (tree, pq, record and basics) until now, but only one (basics) has been merged with upstream. Hence, similar to last week, one of my goals for the next week is to get tree test and pq test merged with upstream. I will try to get record test merged as well, but since it has more changes (which translates to a bigger patch) and I have not received any feedback on it yet, I am not getting my hopes too high. Other than that, I will work on readwrite test and revisit the official reftable documentation to iron out the parts that I cannot grasp yet, which is something I planned on but could not do last week.

## Challenges
Like last week, this one was more or less a smooth sailing as well. I did not face any particular roadblocks but that was mostly due to the fact that I was working on tests that I had already studied. In the upcoming weeks, the tests will become more unfamiliar and simultaneously grow in complexity and I am sure I will encounter more roadblocks than I did this week, but I won't stress out too much about that for now and tackle these problems as I encounter them.

_Till next time,_

_Chandra_.
