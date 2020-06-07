---
layout: post
title:  "Review - From System F to Typed Assembly Language"
categories: PL review
---

https://doi.org/10.1145/319301.319345

Overall merit
5.  Strong accept

Reviewer expertise
2.  Some familiarity

Paper summary

The paper presents the type-preserving compilation from a variant of System F to typed assembly language (TAL). The source language is a high level functional language, while the target language is a RISC based assembly language augmented with a type system.The compilation is done through five phases of translations between six typed languages, in the following order: CPS conversion, closure conversion, hoisting, allocation, and code generation. CPS conversion makes control flow explicit and eliminates the need for a stack. Closure conversion makes functions no longer contain free variables. The paper proposes a simple type-erasure approach to deal with polymorphic closure conversion. Hoisting places all closed functions to the top level. The allocation step allocates space and initializes tuples. The code generation step generates instructions in TAL.

Comments for author

The paper goes in great detail explaining how the compilation works, and the factorial program serves as a nice example to demonstrate it. Yet it is unclear to me why the whole compilation process is designed like so. I wish the authors could discuss a bit more about the design rationale behind the phases of the compilation. It is also kind of sketchy when it comes to explaining why type correctness is preserved between two intermediate languages, as such properties are merely stated as Lemmas without proof. The operational semantics of the source language is omitted, but for completeness and for clarity, I think it would be better to include them. Since the source language is strictly speaking "a variant of" System F, I am not sure if the title of the paper is appropriate. Also there is a typo on page 532, section 3, System F, "operated on by by".
