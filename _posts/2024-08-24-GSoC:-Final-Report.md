A new unit testing framework written entirely in C was introduced to the Git mailing list last year (commit 8bf6fbd0, merge branch 'js/doc-unit-tests', 2023-12-09) with the aim of simplifying testing by offering a way to observe how low level implementation details, at the level of sequences of individual function calls, behave.

Git's reftable library comes with self tests, which are exercised as part of the usual end-to-end tests and are designed to observe the end-user visible effects of Git commands. What it exercises, however, is a better match for the unit-testing framework. Hence, this GSoC project was aimed at extending the unit-testing framework by moving the reftable tests from the old setup to the new unit testing framework, and then improving the tests themselves.

# What I've done

There are a total of eight reftable tests, and I worked on moving all of these to the unit testing framework during this GSoC project:
- basics test
- record test
- block test
- tree test
- pq test
- stack test
- merged test
- readwrite test

Following is the status, commits list, and mailing list link corresponding to the patches for each of these tests. Besides working on the reftable tests, I maintained a weekly blog of my GSoC journey, starting with the Community Bonding period and ending with week 12 of the Coding Period, which can be found [here](https://chand-ra.github.io/).

### basics test
**status:** merged to 'master' (commit 56346ba24e, Merge branch 'cp/reftable-unit-test')

**mailing list link:** https://public-inbox.org/git/20240529171439.18271-1-chandrapratap3519@gmail.com/

**commits:**

[1/5] t: move reftable/basics_test.c to the unit testing framework

[2/5] t: move tests from reftable/stack_test.c to the new unit test

[3/5] t: move tests from reftable/record_test.c to the new unit test

[4/5] t: add test for put_be16()

[5/5] t: improve the test-case for parse_names()

### record test
**status:** merged to 'master' (commit 9118e46e81, Merge branch 'cp/unit-test-reftable-record')

**mailing list link:** https://public-inbox.org/git/20240702074906.5587-1-chandrapratap3519@gmail.com/

**commits:**

[1/11] t: move reftable/record_test.c to the unit testing framework

[2/11] t-reftable-record: add reftable_record_cmp() tests for log records

[3/11] t-reftable-record: add comparison tests for ref records

[4/11] t-reftable-record: add comparison tests for index records

[5/11] t-reftable-record: add comparison tests for obj records

[6/11] t-reftable-record: add reftable_record_is_deletion() test for ref records

[7/11] t-reftable-record: add reftable_record_is_deletion() test for log records

[8/11] t-reftable-record: add reftable_record_is_deletion() test for obj records

[9/11] t-reftable-record: add reftable_record_is_deletion() test for index records

[10/11] t-reftable-record: add tests for reftable_ref_record_compare_name()

[11/11] t-reftable-record: add tests for reftable_log_record_compare_key()

### block test
**status:** merged to 'next' (commit 234d8701da, Merge branch 'cp/unit-test-reftable-block')

**mailing list link:** https://public-inbox.org/git/20240821124150.4463-1-chandrapratap3519@gmail.com/

**commits:**

[1/11] t: move reftable/block_test.c to the unit testing framework

[2/11] t: harmonize t-reftable-block.c with coding guidelines

[3/11] t-reftable-block: release used block reader

[4/11] t-reftable-block: use reftable_record_equal() instead of check_str()

[5/11] t-reftable-block: use reftable_record_key() instead of strbuf_addstr()

[6/11] t-reftable-block: use block_iter_reset() instead of block_iter_close()

[7/11] t-reftable-block: use xstrfmt() instead of xstrdup()

[8/11] t-reftable-block: remove unnecessary variable 'j'

[9/11] t-reftable-block: add tests for log blocks

[10/11] t-reftable-block: add tests for obj blocks

[11/11] t-reftable-block: add tests for index blocks

### tree test
**status:** merged to 'master' (commit 7b11e20bff, Merge branch 'cp/unit-test-reftable-tree')

**mailing list link:** https://public-inbox.org/git/20240804141105.4268-1-chandrapratap3519@gmail.com/

**commits:**

[1/5] reftable: remove unnecessary curly braces in reftable/tree.c

[2/5] t: move reftable/tree_test.c to the unit testing framework

[3/5] t-reftable-tree: split test_tree() into two sub-test

[4/5] t-reftable-tree: add test for non-existent key

[5/5] t-reftable-tree: improve the test for infix_walk()

### pq test
**status:** merged to 'master' (commit d65332f241, Merge branch 'cp/unit-test-reftable-pq')

**mailing list link:** https://public-inbox.org/git/20240801110453.5087-1-chandrapratap3519@gmail.com/

**commits:**

[1/7] reftable: remove unncessary curly braces in reftable/pq.c

[2/7] reftable: change the type of array indices to 'size_t' in reftable/pq.c

[3/7] t: move reftable/pq_test.c to the unit testing framework

[4/7] t-reftable-pq: make merged_iter_pqueue_check() static

[5/7] t-reftable-pq: make merged_iter_pqueue_check() callable by reference

[6/7] t-reftable-pq: add test for index based comparison

[7/7] t-reftable-pq: add tests for merged_iter_pqueue_top()

### stack test
**status:** in progress

**mailing list link:** https://public-inbox.org/git/20240823120514.11070-1-chandrapratap3519@gmail.com/

**commits:**

[1/6] t: move reftable/stack_test.c to the unit testing framework

[2/6] t: harmonize t-reftable-stack.c with coding guidelines

[3/6] t-reftable-stack: use Git's tempfile API instead of mkstemp()

[4/6] t-reftable-stack: use reftable_ref_record_equal() to compare ref records

[5/6] t-reftable-stack: add test for non-default compaction factor

[6/6] t-reftable-stack: add test for stack iterators

### merged test
**status:** merged to 'master' (commit 6c70d65712, Merge branch 'cp/unit-test-reftable-merged')

**mailing list link:** https://public-inbox.org/git/20240712055041.6476-1-chandrapratap3519@gmail.com/

**commits:**

[1/7] t: move reftable/merged_test.c to the unit testing framework

[2/7] t: harmonize t-reftable-merged.c with coding guidelines

[3/7] t-reftable-merged: improve the test for t_merged_single_record()

[4/7] t-reftable-merged: improve the const-correctness of helper functions

[5/7] t-reftable-merged: add tests for reftable_merged_table_max_update_index

[6/7] t-reftable-merged: use reftable_ref_record_equal to compare ref records

[7/7] t-reftable-merged: add test for REFTABLE_FORMAT_ERROR

### readwrite test
**status:** merged to 'next' (commit 8d68f73455, Merge branch 'cp/unit-test-reftable-readwrite')

**mailing list link:** https://public-inbox.org/git/20240813144440.4602-1-chandrapratap3519@gmail.com/

**commits:**

[1/4] t: move reftable/readwrite_test.c to the unit testing framework

[2/4] t-reftable-readwrite: use free_names() instead of a for loop

[3/4] t-reftable-readwrite: use 'for' in place of infinite 'while' loops

[4/4] t-reftable-readwrite: add test for known error

# What's left to do

- The stack test migration patch is the only one that is left to get merged with upstream, this is something that should be finished by the next week at most.
- `reftable/test_framework.{c, h}` and some other files corresponding to reftable test artefacts need to be removed from the `reftable/` directory. This should be done after the last test from `reftable/` has been migrated to the unit testing framework.
- More improvements may still be added to the reftable tests. I have added all the improvements to the reftable tests that I could think of, but it's more than likely that there are more possible which didn't cross my mind at the time.

# Closing remarks

Talking about what I've learnt from this GSoC journey, there are too many to be listed. I barely knew any of Git or Bash before GSoC, but now I can somewhat keep up with some of the work in one of the most influential open-source communities. I also learnt what it's like to work collaboratively on a project, especially with people far more experienced and knowledgeable than me. It was a pleasure learning from them.

The biggest challenge I faced during my GSoC journey was during the start, where I was trying to learn reftable's codebase and start off with the contributions. Learning the codebase of Git is like fighting a dragon with a fork for me. Every little change to be made requires researching, referencing, and asking a pile of questions. The only way to keep making progress is to learn actively on the work, and ask for help whenever you feel stuck. The rest of the journey was more-or-less smooth. There were a few difficulties that I faced in the Coding Period, but nothing that couldn't be overcome with the help of mentors.

Post GSoC, I'll finish whatever little work is left regarding the migration of reftable's tests. More importantly though, I’ll maintain my passion for open source technologies and stay active with Git as a contributor. I’ll also try to be helpful to newcomers of the community and help them ease their way into this wonderful project.

At the end, all I want to say is thank you to my mentors, Patrick and Christian. Thank you, Git and the community. Thank you, GSoC.

_Till next time,_

_Chandra_.
