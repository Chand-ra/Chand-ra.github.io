It has been around two weeks since the start of GSoC's Community Bonding period. As I mentioned in the previous post, my primary goal for this period is to familiarize myself with the reftable sub-project's codebase and gain an understanding of reftable's underlying workings. I covered just about everything else I had planned for the Community Bonding period last week, so this week was entirely dedicated to this one goal.

## Goals accomplished
- What I did up until last week.

My latest approach towards understanding reftable's codebase was to debug the already present tests for reftable and step through the call stack to see what each function is supposed to do and how. This proved to be a better approach than the last one (debug the codebase as a user), but it still has some holes. I decided to apply this method on the stack tests first and that ended up being a poor decision because:
i) the stack tests have more test-cases than any other tests 
ii) the stack is a higher-level component of reftable compared to readers, writers, blocks, etc. due to which I was stuck debugging through a single function call in stack.c for multiple hours and the function call stack spanned multiple files like reader.c, blocksource.c, writer.c, making it difficult to keep track of the entire picture.

## Next week's goals
I believe my strategy of debugging through the tests is still pretty worthwhile, but I have decided to abandon `stack.c` for now and to shift my focus to a more fundamental part of reftable, `block.c` and `blocksource.c`. The block tests have a single test-case so it should be easy enough to knock out in a day or two, and since blocks are the 'building blocks' of reftable, understanding their innards will make understanding the rest of the codebase easier as well. Since this week is the last one in the Community Bonding period, I believe it will no longer be possible for me to go through every single test, so I have decided to cover as many tests as I can in the remaining days, and understand the rest of reftable's workings solely through the documentation for now.

## Challenges
I faced some difficulties with my new approach towards understanding reftable, but I have modified it again to suit me better. I hope the sailing goes smoother this time than it did last week. I can understand a lot more of reftable's [official documentation](https://git-scm.com/docs/reftable) than I did earlier but there are still some parts I have yet to fully grasp. I plan on seeking help from my mentors to push through those parts. Besides that, the previous week's challenge of finding a suitable reftable patch to work on still remains but it's in the backseat for now, and I don't plan on actively tackling it this week.


_Till next time,_

_Chandra_.
