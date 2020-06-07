---
layout: post
title:  "Review - Bringing the web up to speed with WebAssembly"
categories: PL review
---

[Paper](https://doi.org/10.1145/3062341.3062363)

Overall merit - 3. Weak accept

Reviewer expertise - 2. Some familiarity

Paper summary

The paper presents the WebAssembly language, an alternative to JavaScript that addresses the problem of executing safe, fast, portable and compact low-level code on the Web. WebAssembly is not dependent on a Web environment and has use cases out the context of the Web. It can be embedded into an execution environment, but a stand-alone implementation is not yet available. The abstract syntax, small-step reduction rules, and typing rules are presented. Soundness properties of WebAssembly are stated as Preservation and Progress theorems with a brief justification. The authors developed implementations of WebAssembly for major browsers inside JavaScript engines. A reference interpreter is also implemented using OCaml. The performance of WebAssembly is compared with that of native code and asm.js using benchmarks, and it is concluded that WebAssembly is competitive with native code and in general runs faster than asm.js.

Comments for author

It is very satisfying to read a paper that is motivated by industry need. The design goals are well explained in the introduction, and the authors did a good job in subsequent sections justifying that WebAssembly has the desired properties, namely, safe, fast, portable, and compact. Some features of WebAssembly are of particular interest to me. For example, the use of structured control flow instead of simple jumps allows validation and compilation in a single pass, and is also easier for human to read. The presentation of the paper is good, and there is a great amount of formal details. I found it hard to follow sometimes because the discussions of the instructions seem to be abstract and scattered all over the place. The authors talk a lot about the WebAssembly language itself, but I wish they explain more about how embedding works, or really, about how to use it in different contexts. I would also like to see some example programs and how it can be used with the JavaScript engine.
