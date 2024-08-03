This week marks week 10 of GSoC's official Coding Period. Similar to the previous few, the majority of my time this week was devoted to writing code for the reftable tests in the unit testing framework. Due to academic reasons, I was unable to write a blog post for week 9 of GSoC's Coding Period, so this post includes the blog-points for that week as well, alongside the past one (week 10).

## Goals accomplished
- **Finish porting readwrite test to the unit testing framework**: Most of the work for this test was completed last week, but there were still a few finishing touches that I wished to add. These are completed now and the commit series is in a good enough position to see the mailing list.
- **Work on feedback from the mailing list**: I sent the patch series for pq and tree test migration to the mailing list and received feedback on them. The patch series for pq test was merged with 'next'. As for tree test, I will send the updated patch series back to the mailing list next week. Hopefully it's in a good enough position to be merged to upstream by now.

With the readwrite tests finished, I have completed most of the planned work for this GSoC project, and it's only a matter of back and forth on the mailing list before the changes reach upstream. Since that doesn't require a lot of time and there is still a while to go before this year's GSoC reaches completion, I will try to find some other reftable-related tasks to work on.

## Next week's goals
I have finished the work for eight tests (readwrite, stack, merged, tree, pq, record, block and basics) until now, but only four (basics, merged, pq and record) have been merged with upstream. Hence, similar to the last week, my primary goal for the next week is to get more tests reviewed and merged with upstream. Other than that, I will try to find and work on some other tasks related to the reftable sub-project.

## Challenges
Like last week, this one was more or less a smooth sailing as well and I faced little to no issues, thanks to the experience I accumulated from the work I performed in the last few weeks.

_Till next time,_

_Chandra_.
