# Summer of Bitcoin '25: Final Report

This report summarizes the work performed by me in my project, **Improve the fuzz testing for Core Lightning**, during Summer of Bitcoin ‘25 under the organization Lightning-Network, mentored by Matt Morehouse.

## Project summary

Bitcoin’s Lightning Network has experienced growing adoption and routing capacity with over $400 million in Bitcoin locked in public channels, making security a top priority.

Fuzz testing is a valuable tool for enhancing the security and robustness of various Lightning Network implementations, but it has received limited attention from LN maintainers. This project aimed at changing that by strengthening fuzz testing for the second most used LN implementation- Core Lightning (CLN).

This effort not only expanded test coverage but also led to the discovery and disclosure of **8 vulnerabilities**, including memory safety bugs and critical denial-of-service (DoS) vectors.

## Work done

The work done throughout this project can be broadly classified into two categories: _improvements to the existing fuzz tests_ for Core Lightning and _adding new ones_.

There's also  investigating, disclosing, and fixing the vulnerabilities uncovered by these efforts, but that is detailed separately in the **Outcomes Achieved** section.

The following is a list of all work performed, broken down by category. A few other targets were explored but ultimately deprioritized to focus on higher-impact areas.

### Improvements to existing tests
- [`fuzz-initial_channel`](https://github.com/ElementsProject/lightning/pull/8373) (status: un-ACKed)
- [`fuzz-bolt11`](https://github.com/ElementsProject/lightning/pull/8366) (status: ACKed)
- [`fuzz-bech32`](https://github.com/ElementsProject/lightning/pull/8311) (status: ACKed)
- [`fuzz-bigsize`](https://github.com/ElementsProject/lightning/pull/8301) (status: ACKed)
- [`fuzz-addr`](https://github.com/ElementsProject/lightning/pull/8297) (status: ACKed)
- [`fuzz-close_tx`](https://github.com/ElementsProject/lightning/pull/8397) (status: ACKed)
- [`fuzz-channel_id`](https://github.com/ElementsProject/lightning/pull/8386) (status: ACKed)
- [`fuzz-base32-64`](https://github.com/ElementsProject/lightning/pull/8183) (status: Merged)
- [`fuzz-bolt12-invrequest-decode`](https://github.com/ElementsProject/lightning/pull/8404) (status: Merged)
- `fuzz-hsm_encryption` (status: not pushed upstream, locally complete and awaiting final review)
- `fuzz-bolt12-offer_decode` (status: Not pushed upstream, locally complete and awaiting final review)

### New tests
- [`fuzz-full_channel`](https://github.com/ElementsProject/lightning/pull/8437) (status: un-ACKed)
- [`fuzz-gossipd_connectd`](https://github.com/ElementsProject/lightning/pull/8423) (status: un-ACKed)
- [`fuzz-open_channel`](https://github.com/ElementsProject/lightning/pull/8437) (status: un-ACKed)
- [`fuzz-wireaddr`](https://github.com/ElementsProject/lightning/pull/8324) (status: un-ACKed)
- [`fuzz-amount-arith`](https://github.com/ElementsProject/lightning/pull/8298) (status: un-ACKed)
- [`fuzz-codex32`](https://github.com/ElementsProject/lightning/pull/8390) (status: ACKed)
- [`fuzz-init_received`](https://github.com/ElementsProject/lightning/pull/8385) (status: ACKed)
- [`fuzz-funder-policy`](https://github.com/ElementsProject/lightning/pull/8312) (status: ACKed)
- [`fuzz-error-warning`](https://github.com/ElementsProject/lightning/pull/8304) (status: ACKed)
- [`fuzz-wire-closing_sig`](https://github.com/ElementsProject/lightning/pull/8244) (status: ACKed)
- [`fuzz-wire-closing_complete`](https://github.com/ElementsProject/lightning/pull/8216) (status: ACKed)
- [`fuzz-hmac-sha256`](https://github.com/ElementsProject/lightning/pull/8185) (status: Merged)
- `fuzz-handle_onion` (status: Not pushed upstream, locally complete and awaiting final review)
- `fuzz-open_channel2` (status: Not pushed upstream, pending feedback on related PRs)
- `fuzz-pong` (status: Not pushed upstream, locally complete and awaiting final review)
- `fuzz-route-calc` (status: Not pushed upstream, pending feedback on related PRs)

Besides adding and improving tests, I maintained a weekly blog of my SoB journey, starting with the initial onboarding and ending with week 13 of the contribution period, which can be found [here](https://chand-ra.github.io/).

## Outcomes achieved

The primary outcome of this project is the set of vulnerabilities discovered through the improvements made to the fuzzing suite. The increase in code-coverage, and hence the robustness of the codebase, is the secondary outcome.

The following is a comprehensive list of all confirmed vulnerabilities. A couple other potential issues were investigated but are not included, as they were ultimately determined to be non-issues or false positives.

- **`NaN` bug in route calculation**: Due to the imprecision of CLN's `fp16_t` type, the route score for a node can be set to `NaN` in some cases. This leads to a runtime error when CLN is compiled with UBSan. In production, this might prevent usable nodes from being included in the route calculations making the network inefficient. A fix has been devised [here](https://github.com/ElementsProject/lightning/pull/8357).

- **Out-of-bounds bug in the address parser**: When parsing a valid `DNS` name that is exactly 255 bytes long, the address parser tries to append a `NULL` terminator at the end of a 255-bytes long buffer, causing a runtime error when compiled with UBSan. In production, the port for the address gets corrupted. A fix has been implemented [here](https://github.com/ElementsProject/lightning/pull/8325).

- **Heap-buffer-overflow error in address formatter**: The address parser doesn't correctly format a `DNS` address that is exactly 255 bytes long, causing the corresponding address formatter to read out of bounds when trying to format this address. A deeper discussion of the issue is available [here](https://github.com/ElementsProject/lightning/pull/8324#issuecomment-3127327957).

- **Scaling with invalid factors**: `amount_sat_scale()` and `amount_msat_scale()` are used in various balance calculations in CLN, but can produce bogus values when scaling parameter is `-NaN` or negative. [Here](https://github.com/ElementsProject/lightning/pull/8306) is a fix for the issue.

- **Dangling memory allocation in `daemon_conn` allocator**: Use of incorrect context in `daemon_conn_new_()` results in a dangling `daemon_conn` object. A proposed fix exists [here](https://github.com/ElementsProject/lightning/pull/8424).

- **DoS vulnerability due to assertion failure**: A specifically crafted message can cause an assertion failure and hence, a crash. Further details are withheld pending a coordinated release. The vulnerability has been disclosed to the Core Lightning maintainers.

- **DoS vulnerability due to memory overflow**: A certain message can cause a node's memory consumption to grow unbounded resulting in a resource exhaustion vulnerability. Further details are withheld pending a coordinated release. The vulnerability has been disclosed to the Core Lightning maintainers.

- **(Possible vulnerability) DoS vulnerability due to memory leak**: A specific message may trigger memleak in a node. More details are witheld due to uncertain severity and possible fatal nature of the vulnerability.

## Future Work & Next Steps

My highest priority is to address feedback on the following pull requests to get them to an approved (ACKed) state:

- [`fuzz-initial_channel`](https://github.com/ElementsProject/lightning/pull/8373)
- [`fuzz-full_channel`](https://github.com/ElementsProject/lightning/pull/8437)
- [`fuzz-gossipd_connectd`](https://github.com/ElementsProject/lightning/pull/8423)
- [`fuzz-open_channel`](https://github.com/ElementsProject/lightning/pull/8437)
- [`fuzz-wireaddr`](https://github.com/ElementsProject/lightning/pull/8324)
- [`fuzz-amount-arith`](https://github.com/ElementsProject/lightning/pull/8298)

After that, I will push the following completed PR's, which have not yet been sent upstream, for review:

- `fuzz-hsm_encryption`
- `fuzz-bolt12-offer_decode`
- `fuzz-handle_onion`
- `fuzz-open_channel2`
- `fuzz-pong`
- `fuzz-route-calc`

Finally, the memleak vulnerability requires further investigation, which should be undertaken as soon as it becomes feasible.

## Closing thoughts

Before this program, I had little experience with fuzz-testing, security, or Bitcoin development. Now, I feel confident in my ability to contribute to this influential open-source community. I also learned valuable time management skills that improved my work-life balance, making this experience far more enjoyable than my past internships.

My biggest challenge came towards the end of the program, when my academic and internship commitments began to collide. Navigating these overlapping commitments was a valuable learning experience. This journey also taught me that understanding the Lightning-Network (or Bitcoin, in general) is a monumental task. The best way to make progress is to learn actively on the job and ask for help when you're stuck. Mentors are always more than happy to provide guidance.

Post SoB, my immediate priority is to see my remaining work through to completion until all tests are ACKed and merged. More importantly though, I’ll maintain my passion for open source and try to stay active in the Bitcoin community in any capacity I can. I’ll also try to be helpful to newcomers and help them ease their way into this wonderful community.

In closing, I want to say thank you to my mentor, Matt. Thank you to the Lightning Network community. And thank you, Summer of Bitcoin, for this incredible journey.

_Till next time,_

_Chandra_.
