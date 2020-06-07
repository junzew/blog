---
layout: post
title:  "Review - A dependently typed assembly language"
categories: PL review
---

[Paper](https://www.cs.cmu.edu/~rwh/papers/dtal/OGI-CSE-99-008.pdf)

Overall merit - 4. Accept

Reviewer expertise - 2. Some familiarity

Paper summary

The paper presents a dependently typed assembly language (DTAL), which is based on TAL introduced by Morrisett et al.. A dependent type system is designed to preserve the properties of type safety and memory safety at assembly level. The type system allows compiler optimizations including the elimination of run-time array bound checking and tag checking. The syntax, dynamic semantics (as an abstract machine), and static semantics of TAL are shown. Issues with type equality and type coercion due to dependent type system are discussed. Additional typing rules are presented as an extension to support polymorphic sum types. The type soundness for DTAL is stated as a theorem and a brief explanation is given. The authors have implemented a type-checker for DTAL and a compiler from Xanadu to DTAL.

Comments for author

There are a lot of formal details in this paper and the example programs are informative. The paper is generally well structured, but I think there are some problems with presentation. For example, the paper does not explain what dependent types are in the introduction section, and an intuitive explanation, that dependent types are types which depend on the values of expressions, is postponed to section 2, which makes it confusing to read at first. It is an interesting idea to design a different type system for TAL, and I wonder what other type systems are out there that potentially could be used with assembly language. Also it seems this kind of dependent system is not widely used, and I am curious about why that is the case.

Comments for PC(hidden from authors)

Some comments/questions:
* In the second paragraph of the introduction, an example property
P of an expression, "e is terminating" is given. I don’t think the example is appropriate. How do we decide if e is terminating or not? Wouldn’t we run into the halting problem from computability theory?
* I am not sure why the authors decide to put the extension on sum types section after the type soundness section. Does it imply that with the such extensions the type soundness no longer holds?
