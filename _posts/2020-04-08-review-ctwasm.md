---
layout: post
title:  "[Review] CT-wasm: type-driven secure cryptography for the web ecosystem"
categories: PL review
---

[Paper](https://doi.org/10.1145/3291642)


Overall merit - 4. Accept

Reviewer expertise - 2. Some familiarity


Paper summary

Despite its popularity in web development, JavaScript is inadequate for implementing in-browser cryptography as it can leak information due to side-channels. This paper introduces the Constant-TimeWebAssembly (CT-Wasm) language, which is a typed extension to WebAssembly to allow secure implementation of cryptographic algorithms. The paper presents the syntax and semantics of CT-Wasm and proves several security properties such as the constant-time property. The authors contribute two implementations of CT-Wasm, a verified type checker, and developer tools ct2wasm that transpile CT-Wasm to Wasm (similar to TypeScript), and wasm2ct that uses an inference algorithm to rewrite Wasm code to CT-Wasm. Three cryptographic algorithms are implemented in CT-Wasm: the Salsa20 stream cipher, the SHA-256 hash function, and the TEA block cipher. The correctness and performances of the algorithms are evaluated.

The paper has a well-justified motivation and the work is quite impressive. Although the extension to Wasm looks minimal, they are based on solid design principles, and the authors go into great detail explaining how and why it works. It is made clear why it is difficult to reason about the constant-time property using a leakage model for JavaScript, and I like their succinct review of WebAssembly. It’s interesting that they made an analogy comparing CT-Wasm and TypeScript. What I understand is that unlike TypeScript, which is a syntactical superset of JavaScript, CT-Wasm is not a strict superset of Wasm but rather an extension. I think including some code snippets for the implemented crypto algorithms would have been helpful. It’s mentioned in section 4.2 that floating point types are vulnerable to timing attacks. Is there a way to mitigate that?
