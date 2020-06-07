---
layout: post
title:  "Review - Formal certification of a compiler back-end or: programming a compiler with a proof assistant"
categories: PL review
---

[Paper](https://doi.org/10.1145/1111037.1111042)

Overall merit - 3. Weak accept

Reviewer expertise - 2. Some familiarity

Paper summary

The paper presents a compiler backend from Cminor (a subset of C) to powerPC assembly implemented with the Coq proof assistant. The correctness of the compiler is also proved using Coq. The compilation passes can be summarized as:

External Cminor → Internal Cminor → RTL → optimizations → LTL → Linear → Mach → PowerPC

* External Cminor is translated to internal Cminor to account for processor-specific constructs
* Structured control flow in internal Cminor is encoded as control flow graph (CFG) in RTL
* Optimizations based on data flow analysis is performed at the RTL level
* RTL is translated to LTL. Register allocation, spill and reload insertion, and calling convention enforcement are performed
* Control-flow graph is linearized in the translation from LTL to Mach
* Stack frame layout is made explicit in the translation rom Linear to Mach
* Mach code is expanded to PowerPC instructions

Proofs of correctness of the compiler passes are given as simulation diagrams that are claimed to be proven. The details of the proofs are however omitted.

Comments for author

Reading this paper gives me a headache, because the authors used a lot of terms that I don’t know or understand, such as "Curry-Howard isomorphism" (see questions below). It seems bizarre to me that a "mixed step" semantics (a combination of small-step and big-step semantics) is used for intermediate languages. I know it might be due to page limits, but I don’t like the fact that the proofs of correctness are just presented as several diagrams and the the details of the proofs are mostly left out. The authors describe programming in Coq to be "pleasant" and how "addictive" building proof scripts can be, yet due to my lack of knowledge of the language, I failed to relate personally with that kind of feelings.

Comments for PC(hidden from authors)
Some questions/notes:

p43.
1. What does it mean for two languages to be “observationally equivalent”?

Two terms M and N are observationally equivalent if and only if, in all contexts C[...] where C[M] is a valid term, it is the case that C[N] is also a valid term with the same value. - wikipedia
2. What is “Curry-Howard isomorphism”?

Based on what I read, it is the correspondence between proving mathematical theorems and program type checking.

p49.
3. Apparently there is a typo in section 4.3, it should be “Kildall’s worklist algorithm” instead of
“Kidall’s worklist algorithm”. There is no citation for this. What is the algorithm anyways?
4. What is the George-Appel heuristic? Chaitin’s rules?

P50.
5. For linearization, what is “trace picking”?

p52.
6. What is “global CSE” and “SSA”?
7. What is “Noetherian induction” and how is it different from structural induction?(It seems to have something to do with well-founded relations.)

Noetherian induction, also called well-founded induction, a proof method for binary relations that satisfy the descending chain condition. - wikipedia

8. Why don’t you need to verify Coq, or has it been verified already?
