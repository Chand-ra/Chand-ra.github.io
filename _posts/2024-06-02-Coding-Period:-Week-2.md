This week marks week 2 of GSoC's official Coding Period. Similar to week 1, the majority of my time this week was devoted to writing code for reftable tests in the unit testing framework.

## Goals accomplished
- **Finish porting pq test to the unit-testing framework**: pq test exercises the priority queue functionality of reftable as defined by `reftable/pq.{c, h}`. I started working on this test the last week and was able to finish the first iteration of the migration patch this week. With feedback from Christian and Patrick on the first iteration, I finished the second iteration of this patch around the end of the week and was able to send it to the mailing list as well. I have yet to receive any feedback on the second iteration, but I hope it's good enough to be merged with upstream now.
- **Finish porting tree test to the unit testing framework**: Most of the work for this test was completed last week but I wasn't able to send the patch for this test to the mailing list because Patrick informed me that one of his patches was about to add a dedicated function for pointer-comparison to the unit testing library, and that could be used in the new tree test. So I decided to put this patch on hold and work on other tests until Patrick's patch landed master. Well, Patrick's patch hit master on Saturday and I was finally able to utilize the unit-testing library's new functionality in this patch. There were a few other small feedback points that I addressed as well, and the patch is now ready to be sent the mailing list next week.
- **Work on porting record test to the unit testing framework**: Since most of the other tests that I mentioned were carried on from the previous week, they were already finished to a good extent and I had quite some time to dedicate on porting a new test. The records test was a major one that I worked on in this week. I was able to almost finish this test within this week, but there is still some polishing that I wish to add. I'll probably finish this test by Tuesday of the upcoming week.
- **Review the readwrite tests**: I wasn't able to dedicate much time to this, but I finished understanding a small portion of the readwrite tests this week.
- What I did up until last week.

I'll probably drop my strategy of understanding the reftable codebase through tests from the upcoming week. It was definitely helpful when I started out and was unfamiliar with the codebase but after working with the code for some time now, I think I can make do without that strategy and utilize that time on better endeavours. I'll still keep it in my mind's backseat though, in case I come across a part of the codebase that I cannot understand through other means.

## Next week's goals
I have finished the work for 3 tests (tree, pq and basics) up until now but only one (basics) has been merged with upstream yet. Hence, my primary goal for the next week is to get tree test and pq test merged with upstream. I'll try to get record test merged as well but since it has more changes (which translates to a bigger patch) and there is still some work left to do, I'm not getting my hopes too high. Other than that, I'll revisit the official reftable documentation next week and try to iron out the parts that I cannot grasp yet.

## Challenges
Like last week, this one was more-or-less a smooth sail as well. I did not face any particular roadblocks but that's mostly due to the fact that I was working on tasks carried over from the last week. In the upcoming weeks, the tests will grow in complexity and I'm sure I'll encounter more roadblocks than I did this week, but I won't stress out too much about that for now and tackle these problems as I encounter them.

Besides that, we had our introductory meet for GSoC this week with the attendees being the interns and mentors for this cohort. I had a fun time meeting and chatting with everyone. A Slack channel with all the current GSoC members was set up as well, and I look forward to interacting with the everyone there.

_Till next time,_

_Chandra_.
