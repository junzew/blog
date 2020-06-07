---
layout: post
title:  "Review - Proof-carrying code"
categories: PL review
---

[Paper](https://doi.org/10.1145/263699.263712)

Overall merit - 4. Accept

Reviewer expertise - 1. No familiarity

Paper summary

This paper introduces proof-carrying code (PCC), which is a mechanism that allows a system to safely execute untrusted program. The code consumer validates the safety proof supplied by the untrusted code producer so that it can verify that the program in question adhere to certain safety policy pre-defined by the code consumer.

In summary, a PCC binary has 3 life stages:

* Certification: the code producer generates the proof
* Validation: the code consumer validates the proof and loads native code component
* Code consumer executes the machine-code program
The safety policy is implemented with first order predicate logic, and a safety proof is encoded as a proof of verification condition predicate (VC). The paper also shows two case studies. One case study is about how to use PCC to develop safe DEC Alpha assembly language extensions to the TIL run-time system. Another case study is an experiment on using PCC to write network packet filters. The authors claim that their packet filters run faster while the run-time overhead of proof validation is negligible. Proof search for the experiments is done in the Elf programming language.

Comments for author

The paper does a good job explaining what PCC is, why it is useful, and how it is designed and implemented, though there are sections that are difficult to follow. It is an interesting idea that proof checking can be done by some form of type-checking. What I like about this paper is the great amount of details, especially the case studies, and the rigour of proving the soundness of using VC predicate certification. I found the section on the first case study to be quite hard to read though, due to my lack of knowledge on LF.

Some questions:
* In the introduction, what are some examples of the "invariants of the ML heap"?
* In section 2, for the last stage of PCC, why does the code consumer potentially need to execute the machine-code program multiple times?
* In section 2, for the paragraph that talks about the validation stage of PCC, what is the "straightforward algorithm" referring to?
* Is the INV instruction native to the assembly language or is it an extension?
* In section 5, what are "first order Horn clauses" and "Harrop formulas"?
