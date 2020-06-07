---
layout: post
title:  "Review - Typed closure conversion preserves observational equivalence"
categories: PL review
---

[Paper](https://doi.org/10.1145/1411204.1411227)


Overall merit
- 4. Accept

Reviewer expertise
- 2. Some familiarity

Paper summary

The paper presents a method to prove fully abstract compilation for languages with existential types and recursive types. In particular, the authors showed that the typed closure conversion from System F to TAL is fully abstract, that is, it both reserves and reflects observational equivalence. The proofs are based on a step-index logical relation.

Comments for author

The paper is pretty well written. Definitions, lemmas and theorems with detailed proofs are presented clearly. I am intimidated by the number of symbols so I skimmed most part of the paper. I am kind of lost when they talk about recursive types. I think it would be helpful in the introduction to show some code examples in System F to demonstrate observational equivalence (like what the Securing the .NET Programming Model paper does).
