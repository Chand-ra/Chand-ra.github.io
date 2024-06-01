GSoC's Community Bonding period came to an end last week, marking the start of the official coding period. As such, the majority of my time this week was devoted to writing actual code and a small part towards reading up on those parts of the codebase that I haven't covered yet.

## Goals accomplished
- **Finish porting basics test to the unit-testing framework**: The first test that I worked on in my project of 'moving and improving reftable tests to the unit testing framework' was the basics test. It was the easiest test of them all and hence a good candidate for the first test to port. The coding part was not very difficult, and I think I knocked it out in a day, but what consumed most of my time was breaking up the overall work into appropriate commits, writing a good patch cover letter, writing better commit messages, and other tasks of the sort. I received a lot of help and feedback from my mentors Christian (@GitLab) and Patrick (@GitLab) and thank them for being patient with me. The patch for this port has been merged with 'seen' as of now.
- **Work on porting tree test to the unit testing framework**: This was another easy test to work on that I completed within this week as well. The experience from working on the basics test helped me a lot here. However, I wasn't able to send the patch for this test to the mailing list because Patrick informed me that one of his patches is about to add a dedicated function for pointer-comparison to the unit testing library, and that is something I could use in the new tree test. So I decided to put this patch on hold and work on something else until Patrick's patch hits master.
- **Finish reading around pq test**: pq test exercises the priority queue functionality of reftable as defined by `reftable/pq.{c, h}`. As a part of my earlier approach to understanding reftable's codebase through the existing tests, I finished reading around the pq test this week as well. This was easy work as well because I was already familiar with the concept of a priority queue through the Data Structures & Algorithms course in my college.
- **Work on porting pq test to the unit testing framework**: This was another easy test that I was able to complete around 90% of within this week. There is still some polishing that I wish to add, but I'm pretty sure I can finish that on the first day of the upcoming week.
- What I did up until last week.

I have to admit, I'm having a lot more fun in the Coding Period of GSoC than I did in the Community Bonding period. I remember struggling to put in around 30 hours of work per week during the Community Bonding Period, but it felt like nothing to me in the past coding week. I'll have to attribute that to the fact that writing code is way more fun than reading code.

## Next week's goals
I plan on using the same strategy for the next week that I used this week, which is to divide my time into incrementally porting the tests to the unit-testing framework and reading up on those parts of reftable that I haven't seen yet. I hope to finish the patch for the tree test and pq test and get them merged to 'seen' in the upcoming week while simultaneously working on either block tests or record tests. I also hope to finish understanding a good part of the readwrite test within this period.

## Challenges
I struggled a bit with using `git send-mail` for my patches because I used [GitGitGadget](https://gitgitgadget.github.io/) for all of my patches pre-GSoC, but I think I'm comfortable with it now. I also faced some difficulties with appropriately structuring my patches, but my mentors helped me overcome that. Last week was a smooth sail because the tests that I worked on were the easiest of the whole bunch, but in the upcoming weeks, the tests will grow in complexity, and I am sure to hit more roadblocks than I did this week. There is also the fact that I haven't touched upon stack test, merged test, refname test, and read-write test yet, and these are some of the larger and more complex tests. I will probably allocate more time towards the goal of understanding the codebase than I did last week to combat this.

Besides all that, we have a meet for GSoC with all the interns and mentors in the upcoming week, which I really look forward to.

_Till next time,_

_Chandra_.
