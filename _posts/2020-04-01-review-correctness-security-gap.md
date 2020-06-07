---
layout: post
title:  "Review -  The Correctness-Security Gap in Compiler Optimization"
categories: PL review
---

[Paper](https://dl.acm.org/doi/10.5555/2867541.2867769)


Overall merit - 4. Accept

Reviewer expertise - 2 Some familiarity

Paper summary

The paper identifies the correctness-security gap in compiler optimizations. This gap arises because an optimization that correctly preserves semantics doesn’t necessarily preserve security properties. Case studies have been conducted to show instances of optimization techniques that result in this gap and make programs vulnerable to attacks that exploits persistent state, undefined behaviour, and side channels. The structure of compiler correctness proof is summarized as proving the existence of a winning strategy for a observational equivalence game between security analyst and a compiler writer. The correctness-security gap is analyzed and inaccuracies with the standard machine execution model are identified. Refinements of the execution model are proposed and open problems are raised to further investigate the correctness-security gap.

Comments for author

This paper belongs to a different genre as compared to the other papers we have read. Most of the papers that we've seen so far introduce new compiler and/or language designs, whereas the contribution of this paper is mainly identifying a research niche. I think the question raised is intriguing and tricky to deal with. We want compiler optimizations to be semantically correct, to generate efficient code, and at the same time to preserve security guarantees. These are a lot to ask all at once so I think some tradeoff must be involved. The authors does a great job introducing the three classes of security weaknesses in section III. The definitions of optimization techniques are clear and the vulnerabilities after optimization are well explained so it is fairly comprehensible and educative for people with little previous knowledge on compiler optimizations (like me). The code listings of the case studies are also very helpful in understanding the problem. I got somewhat confused by the notations used in the definitions in section IV, but I found the idea of using winning strategies from game-theory to model observational equivalence to be interesting. I don't understand what Borel determinacy theorem is though.

Comments for PC(hidden from authors)

* The Common Weakness Enumeration (CWE) cited in the paper is interesting to look at, but I think maintaining this list is a double edged sword. It could be used for prevention and mitigation but on the other hand attackers can use it as a recipe to exploit programs.
* The notations in section IV are introduced without proper definitions. For example, on page 79 near the bottom, what is S and E in (S, E, l)?
* On page 73, they mentioned three much debated questions, I might have missed it but I am not sure what the authors’ stance on these questions is, and also what do people think about these questions?
