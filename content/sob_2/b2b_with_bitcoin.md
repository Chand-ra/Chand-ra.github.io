---
title: "Going Back to Back with Bitcoin"
date: 2026-05-06
---

## Introduction

Last summer, I participated in Summer of Bitcoin with the Lightning Network organization, working on the project "[Improving fuzz testing for Core Lightning](https://chand-ra.github.io/sob/)" under [Matt Morehouse](https://github.com/morehouse)’s mentorship. That experience served as my introduction to the worlds of Bitcoin, security, and fuzz testing: a path I’ve continued since by contributing to the fuzzing suites of [Bitcoin Core](https://github.com/bitcoin/bitcoin) and [Core Lightning](https://github.com/ElementsProject/lightning/).

While I didn't initially plan on participating in Summer of Bitcoin 2026, when the organizations list was announced, the [Smite project](https://github.com/morehouse/smite/) immediately caught my eye, prompting me to submit a proposal for "Advanced IR Mutators with Effectiveness Evaluation" track. I’m thrilled to announce that my proposal was selected as the top submission. This summer, I’ll be diving back into Bitcoin with the Smite organization, once again under Matt’s mentorship, to work on the project **Enhancing Smite: Advanced IR Mutation and Effectiveness Evaluation**.

## About the project

Smite is a coverage-guided [snapshot fuzzing](https://appsec.guide/docs/fuzzing/snapshot-fuzzing/) framework for the Lightning Network, similar to what [fuzzamoto](https://brink.dev/blog/2026/01/07/fuzzamoto-introduction/) provides for Bitcoin full-node implementations. It is designed to solve a major limitation in traditional fuzzing: the lack of structure-awareness. This deficiency often prevents standard byte-level fuzzing from reaching the deep logic paths of complex protocols.

By becoming structure-aware, a fuzzer can generate and mutate sequences of valid messages that successfully bypass initial parsing checks. Smite (and fuzzamoto) achieve this by utilizing a custom [Intermediate Representation (IR)](https://en.wikipedia.org/wiki/Intermediate_representation). This IR encodes the necessary type and structural knowledge of the protocol, enabling the fuzzer to generate "short programs" that are executed within a Virtual Machine.

My project aims to improve Smite’s effectiveness by adding advanced mutators for this custom intermediate representation (IR) and then measuring the said increase in effectiveness using various statistical techniques. Greater details of the project can be viewed in the [full proposal](https://drive.google.com/file/d/1m6s2ECo6btTNTuRzqphuQppiSY7Pm-pj/view?usp=sharing).

## Goals

Unlike my previous experience with Summer of Bitcoin, which involved a more open-ended project, this year’s stint comes with specific "hard requirements" for success. My primary objective is to implement at least four advanced IR mutators: `InstructionDeleteMutator`, `InstructionReorderMutator`, `GeneratorInsertionMutator`, `SpliceMutator` and develop an evaluation framework to measure their effectiveness. I made significant progress for [`InstructionDelete`](https://github.com/morehouse/smite/pull/60) and [`InstructionReorder`](https://github.com/morehouse/smite/pull/61) mutators before the start of the program, leaving the other two to be implemented, which happen to be the more complex ones.

Because I anticipate completing the core mutators and evaluation framework ahead of schedule, I have included several ambitious stretch goals for the second half of the program:

- Implementation of additional structural mutators like `InstructionCloneMutator` and `InstructionHoistMutator`.

- Replacing the current Uniform Random Scheduler with an adaptive version, modeled after AFL++’s [MOpt](https://github.com/puppet-meteor/MOpt-AFL).

Again, technical specifics are available in the project [proposal](https://drive.google.com/file/d/1m6s2ECo6btTNTuRzqphuQppiSY7Pm-pj/view?usp=sharing).

This is a tall order, but I’ve embraced it as a personal challenge. I am confident that with consistent focus, I can deliver these results.

- **May 11 – May 15, 2026**: Kick-off and Onboarding. I’ll be finalizing implementation details, meeting schedules, and logistics with Matt.

- **May 18, 2026**: Official start of the project period.

In the days leading up to the program, I will be finishing my build and test environments, finalizing paperwork, and streamlining my other commitments to ensure I can dedicate myself entirely to the project once the contribution period begins.

_Till next time,_

_Chandra_.
