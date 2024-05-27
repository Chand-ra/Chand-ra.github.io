It only feels like a few days since the start of GSoC 2024 but with the past week, the Community Bonding Period came to an end. This week, I continued with my last week's goal of understanding the reftable backend and feel I have made good progress towards that.

## Goals accomplished
- **Finish reading Patrick's blog material**: A few days ago, my mentor Patrick Steinhardt (@ GitLab) provided me with material for a new blog about the reftable backend that he is currently working on. The blog consists of a .md file and various graphics explaining reftable's sub-parts. I worked over the blog and graphics this week and it helped me a lot in my quest to understand the reftable backend.
- **Finish reading reftable documentation**: At the start of the Community Bonding period, I struggled to understand a large part of Git's [reftable documentation](https://git-scm.com/docs/reftable#Update-transactions). But with my mentors' help (especially the blog material by Patrick), I believe I understand around 80% of the documentation now. This is a big milestone for me because it has made understanding the codebase a lot easier.
- **Finish understanding the block tests**: Last week, I decided to change my strategy and employ my plan of 'understanding reftable's codebase through the existing tests' on the block tests instead of the stack tests, and I'm happy that I did. Blocks are a lower-level component of reftable than stacks which made debugging and understanding their tests a lot easier. I was able to complete the block tests by the middle of the week.
- **Finish understanding the record tests**: Since I was done with the block tests by the middle of the week, I decided to go through the record tests because records, akin to blocks, form a low-level component of the reftable backend. I was able to cover these tests this week as well.
- What I did up until last week.

## Next week's goals
Since the official coding period starts in the upcoming week, I plan to divide my time into incrementally porting those tests to the unit testing framework that I have already skimmed over, and using my earlier plan of understanding reftable's codebase through tests to cover the parts that I haven't yet. Because my project is about improving the reftable tests as much as moving them to the new testing framework, I plan to work on improving the tests in all ways that I can currently think of, like harmonizing the coding style, adding more documentation, adding tests for functions that don't have any, alongside porting them. I hope to finish the first iteration of the reftable tests migration patch before the midterm evaluation.

## Challenges
I faced some difficulties with formulating an appropriate plan to accomplish my goal of understanding the reftable codebase, but I believe that through my work in the Community Bonding Period, I have arrived at a good approach and have used it to understand a good portion of the codebase by now. There's still quite a bit that I do not understand, but I believe I can incrementally work towards those parts as I did with the rest of the codebase. Besides that, I am excited to finally write some code in the upcoming weeks. It is surely going to be challenging but I believe I can push through those challenges.

_Till next time,_

_Chandra_.
