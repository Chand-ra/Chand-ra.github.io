# Hello, GSoC!

This is Chandra, and I have been selected for the Google Summer of Code 2024 program with Git. A part of me still cannot believe that I actually got in, while some other part thinks it is only reasonable given how much effort I put in for this. I also feel a bit of imposter syndrome, as there were a lot of good candidates for this year's GSoC and I was the one selected among them. In any case, I am absolutely excited to spend my summer vacation writing code for a project as big and impactful as Git. I hope to learn a lot and come out as a better programmer at the end of this project.

## About the project

The project that I'm going to work on is '_Move and improve reftable tests in the unit testing framework_' and the proposal that got me selected can be found [here](https://summerofcode.withgoogle.com/media/user/32192b2dae2b/proposal/gAAAAABmNHGwi8ZcoSyHE608hOpvoYzWfP8Nb_XsaVZB1Cj31aLcgdAusbX0c0pvFEW48U1H-8TguJwj_qpBbiX4yMFl4bG70Yj9p8L8qTmSLjFs3k7G5N4=.pdf). It is a large project and is expected to take around 350 hours to complete and my mentors for this project are Christian Couder (GitLab) and Patrick Steinhardt (Google). To give a synopsis of the proposal, my task for this internship is to move the parts of Git's unit tests that exercise Git's reftable backend from the current '.c files + shell scripts' setup to a new unit testing framework written entirely in C and then improve upon & extend those tests.

I already have some experience with porting tests to the new unit testing framework from the patches I worked on pre-GSoC where I tinkered with the reftable tests as well, so the work required in actually porting the tests is trivial compared to the improvements part. To make meaningful improvements to the reftable tests, I need to gain a substantial understanding of Git's reftable backend, which is something entirely new to me. Among all of my merged patches on Git's mailing list pre-GSoC, none were related to reftable or in it's vicinity, so this is an entirely uncharted territory for me. Nonetheless, I believe I can go past these challenges and make this project successful.

## Goals
The time period from May 1 to May 26 in GSoC is the 'Community bonding period'. During this time, GSoC contributors are expected to read up documentation, get familiar with the codebase and tools, set up expectations and milestones, start engaging with the community, complete the required paperwork and so forth. In my GSoC proposal, I outlined this time period to learn in-depth about reftable and contribute a few patches towards that goal. Keeping this in mind, here's a list of my goals for what's left of this week and the following one:
- Finish setting up this blog.
- Go through Git's [Coding Guidlines](https://github.com/git/git/blob/master/Documentation/CodingGuidelines) again to better understand the coding style errors that I need to be on the lookout for.
- Go through Pro Git book's ['Git Internals' chapter](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain) to re-familiarize myself with Git objects and references which reftable deals with.
- Finish reading up the [reftable documentation](https://git-scm.com/docs/reftable). (This might take some time because the document is technically dense so there is a lot to uncover).
- Find some suitable starting patches in the reftable sub-project.
- Finish setting up a Payoneer account.

_Till next time,_

_Chandra_.
