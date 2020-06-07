---
layout: post
title:  "Review - Compositional CompCert"
categories: PL review
---

[Paper](https://doi.org/10.1145/2775051.2676985)


Overall merit - 4. Accept

Reviewer expertise - 1. No familiarity


Paper Summary

This paper is about Compositional CompCert, a verified separate compiler from Clight to x86 assembly. Compositional CompCert builds on CompCert to support certification of separate compilation of multi-module programs that might access shared memory locations, overcoming the restriction that proof of correctness apply only to whole programs. The main contributions of the paper include language-independent linking and structured simulations. Coq implementation and proofs of the compiler are provided.

Comments for author

The paper is quite abstract and assumes knowledge of Coq. In general technical terms are well defined and theorems are stated clearly. The authors have done a good job laying out the background on interaction semantics and logical simulation relations (LSR) with great attention to formal details. I was surprised at first that the compiler phases of Compositional CompCert are similar to CompCert’s, as shown in Figure 13. It could be because the compiler passes (vertical composition) are orthogonal to linking (horizontal composition), so not much needs to be modified. I found it an interesting idea that multithread programs and multi-module programs share similar interaction protocols, and I think the related work section hints on an open problem of separate compilation of multithread racy programs. It would be nice to have some evaluation of compilation time or performance of compiled code. One complaint is that their code repo doesn’t seem to be up-to-date. The authors wrote "see the code that accompanies this paper for the complete definition" of the semantics, but the links are broken. There were only 7 stars for their Github repo, which makes me doubt how many people actually reviewed their code.
