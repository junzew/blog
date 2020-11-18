---
layout: post
title:  "[Review] Securing the .NET programming model"
categories: PL review
---

[Paper](https://dl.acm.org/doi/10.1016/j.tcs.2006.08.014)


Overall merit - 3. Weak accept

Reviewer expertise - 1. No familiarity

Paper summary

This paper identifies 6 failures of full abstraction in the compilation from C# to the Intermediate Language (IL) run by the .NET platform, and explains how to fix the issues raised. There are 3 ways of fixing the issues: change the translation, increase expressivity of source language, and decrease expressivity of the target language. The failures are:
1. **Overridden methods are exposed**: In IL you can call overridden method directly to gain access to methods are are supposed to be hidden from client.
2. **Boxing breaks encapsulation**: The `unbox` instruction in IL can be used to mutate boxed data.
3. **Exceptions are not `Exception`s**: IL allows the throwing of non-`Exception` objects that will slip through a `catch`.
4. **`bool`s are not two-valued**: Passing a `byte` value other than `0`/`1` for translated `false`/`true` can break full abstraction.
5. **`this` can be `null`**: IL can pass a `null` instance to a method so that `this` becomes `null`, which isn’t possible in C#.
6. **`out` parameters are also `in`**: IL can't distinguish between an `out` parameter and ordinary call-by-reference parameter.

Comments for author

The paper is very concise and it is nice that each problem description is accompanied by a concrete code example showing how an attacker can exploit the program. The examples all seem to be contrived but I guess that is just what security analysis is about. I think they could have included the compiled IL code for the small equivalence examples at the end of each problem description in section 2 to elaborate on how equivalences are broken. One minor complain about writing style, I think it would make more sense to talk about the fix for each problem right after describing what the problem is. It was kind of inconvenient scrolling and jumping between sections. The authors mentioned at the end that their goal is to ensure C# programmers can "think in C#", but I think what they have discussed in the paper is really about how to think in the IL. Also not sure if it's a red flag when a paper cites Wikipedia (problem 2, page 3).

Comments for PC (hidden from authors)

I don't know much about C# and the IL so there are a few points I don't understand.

For problem 2, (page 4) I don't know if `.salaries.Put` is a typo and should be `.salaries.Set`? But isn't `Set` internal to `StringDict`? What's the difference between an `internal`method in C# and  a `private` method in Java?

For problem 6, I don't get the meaning of the title "`out` parameters are also `in`". According to Microsoft’s documentation, `in` means an argument cannot be modified by the method,  which contradicts the sentence that says "`out` parameters, must be assigned by the callee before returning". Why is the example shown on top of page 8 equivalent?
