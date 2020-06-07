---
layout: post
title:  "Review - TIL: A Type-direct optimizing compiler for ML"
categories: PL review
---

https://doi.org/10.1145/249069.231414

Overall merit
4. Accept

Reviewer expertise
1. No familiarity

Paper summary

The paper describes TIL (Typed Intermediate Languages), a compiler from Standard ML to the ALPHA assembly language. The technologies used by TIL and the compilation phases are presented. The technologies include intensional polymorphism, conventional and loop-oriented optimizations, and nearly tag-free garbage collection. TIL uses ML Kit as the front-end to compile SML to an intermediate language called Lambda, which then gets converted to an intensionally polymorphic language, Lmli. After type-directed optimizations, TIL translates Lmli to a subset of Lmli (Bform), and then does conventional and loop optimizations. TIL then does closure conversion to convert Lmli-Bform into Lmli-Closure, followed by a conversion to untyped Ubform. Ubform is then translated to RTL and finally to ALPHA. The paper compares the performances of TIL compiled programs to those compiled by SML/NJ using 8 benchmark programs. Results suggest that TIL compiled programs generally run faster, require fewer heap allocation, and are more memory efficient, but they also require longer compilation time, as compared to SML/NJ compiled programs.

Comments for author

The paper is well-structured which makes it not too difficult to follow. There are many technical terms used in this paper and generally their meanings are explained. I found section 3.3 to be interesting, because many optimization techniques are introduced. Although an example compilation is given, the paper does not specify the full syntax and semantics of the intermediate languages and the translation rules are not shown, which makes the discussion of the compilation phases a bit too abstract. Only 8 programs that seem to be chosen arbitrarily are used as benchmarks, so I don’t know if this sample size is appropriate and whether they are representative or not. I doubt that it is impossible to have certain program that runs slower relative SML/NJ, or at least the paper does not show any effort in constructing such an counterexample.
