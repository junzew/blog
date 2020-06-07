---
layout: post
title:  "Review -  Lightweight verification of separate compilation"
categories: PL review
---

[Paper](https://doi.org/10.1145/2837614.2837642)


Overall merit
- 4. Accept

Reviewer expertise
- 2. Some familiarity

Paper Summary

The purpose of the work is to come up with a simple and lightweight proof method
for verifying separate compilation. The authors achieved this goal by reusing proofs for whole-program compilations and developing several new proof techniques to show two levels of compositional correctness. The techniques have been applied to CompCert in less than two person-months by the authors, and the result is the SepCompCert compiler. The paper uses constant propagation as a running example. Two bugs with CompCert were caught while porting CompCert to SepCompCert.

Comments for author
The motivation of the paper is made clear. The authors took a different approach than Compositional CompCert. They are basically trading-off the ability to compile with different compilers for faster and easier implementations and proofs. I am not too convinced that person-month is a good criteria for evaluating proof effort but the reduction in lines of code is indeed impressive. I think the proof techniques may be given more meaningful names. In the paper they are just referred to as "trivial technique" and "non-trivial technique".

Comments for PC(hidden from authors)

The relation <a href="https://www.codecogs.com/eqnedit.php?latex=Behav($$s$$)&space;$$\supseteq$$&space;Behav($$t$$)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Behav($$s$$)&space;$$\supseteq$$&space;Behav($$t$$)" title="Behav($$s$$) $$\supseteq$$ Behav($$t$$)" /></a> seems ill-defined. What are some examples of observable behaviours? What does it mean for one behaviour to be contained in another behaviour?

How is <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{T}(s_1.l1)&space;\circ&space;\dots&space;\circ&space;\mathcal{T}(s_n.l1)&space;=&space;\mathcal{T}(s_1.l1&space;\circ&space;\dots&space;\circ&space;s_n.l1)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{T}(s_1.l1)&space;\circ&space;\dots&space;\circ&space;\mathcal{T}(s_n.l1)&space;=&space;\mathcal{T}(s_1.l1&space;\circ&space;\dots&space;\circ&space;s_n.l1)" title="\mathcal{T}(s_1.l1) \circ \dots \circ \mathcal{T}(s_n.l1) = \mathcal{T}(s_1.l1 \circ \dots \circ s_n.l1)" /></a> commutative? It looks more like distributive property to me.
