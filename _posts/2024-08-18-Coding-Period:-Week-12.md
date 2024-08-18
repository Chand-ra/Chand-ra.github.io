This week marks week 12 of GSoC's official Coding Period. Similar to the previous ones, the majority of my time this week was devoted to writing code for the reftable tests in the unit testing framework.

## Goals accomplished
- **Work on feedback from the mailing list**: I sent the patch series for block and readwrite test migration to the mailing list and received feedback on them. The patch series for readwrite has been merged with upstream and should land in the 'master' branch soon. As for block test, I sent the patch series to the mailing list and received feedback on it, reworked the commits and rerolled the updated version towards the end of the week. There is a small mistake that causes a leak in the CI which I'll fix along with incorporating new feedback in the next reroll.

## Next week's goals
I have finished the work for eight tests (readwrite, stack, merged, tree, pq, record, block and basics) until now, but only six (readwrite, tree, basics, merged, pq and record) have been merged with upstream. Hence, similar to the last week, my primary goal for the next week is to get more tests reviewed and merged with upstream.

## Challenges
Like last week, this one was more or less a smooth sailing as well and I faced little to no issues, thanks to the experience I accumulated from the work I performed in the last few weeks.

_Till next time,_

_Chandra_.
