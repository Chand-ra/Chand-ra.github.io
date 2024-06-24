This week marks week 4 of GSoC's official Coding Period. Similar to the previous few, the majority of my time this week was devoted to writing code for the reftable tests in the unit testing framework.

## Goals accomplished
- **Finish porting record test to the unit testing framework**: Most of the work for this test was completed last week, but there were still a few finishing touches that I wished to add. I was able to completely finish the work for these tests by this week, and sent the resulting patch series to the mailing list.
- **Work on porting readwrite test to the unit testing framework**: I decided to work on readwrite test next. This test took me an entire week to complete and that is mostly because this is one of the larger reftable test files and the improvements that I had in mind for this test ended up being more difficult to implement than anticipated. In any case, I was able to finish a large part of my planned work for these tests in this week, and the work should be finished by the next week.
- **Finish porting block test to the unit testing framework**: Most of the work for this test was completed last week, but there were still a few finishing touches that I wished to add. I was able to completely finish the work for these tests by this week.
- **Work on porting stack test to the unit testing framework**: I had some extra time towards the end of the week where I did not wish to work on readwrite test, so I decided to start working on porting stack test to the unit testing framework. This test is the largest one in the `reftable/` directory, so it will take some time to see it to completion.
- What I did up until last week.

## Next week's goals
I have finished the work for five tests (tree, pq, record, block and basics) until now, but only one (basics) has been merged with upstream. Hence, similar to last week, one of my goals for the next week is to get more tests merged with upstream. Other than that, I will finish the work on readwrite test and start working on porting the next test to the unit testing framework.

## Challenges
Like last week, this one was more or less a smooth sailing as well. I did not face any particular roadblocks but that was mostly due to the fact that I was working on tests that I had already studied. In the upcoming weeks, the tests will become more unfamiliar and simultaneously grow in complexity and I am sure I will encounter more roadblocks than I did this week, but I won't stress out too much about that for now and tackle these problems as I encounter them.

_Till next time,_

_Chandra_.
