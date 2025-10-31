# 07_roadmap: the path forward

tiny lento v0.1 represents the frozen core specification.  
this version establishes the philosophical groundwork—minimalism, strict left-to-right evaluation, and the nt-closure law.  
the future roadmap is focused entirely on hardening the language into a self-sufficient, production-ready core.

---

## v0.1: the frozen foundation

**status:** frozen core specification.  
**focus:** establishing the minimal, deterministic syntax, arithmetic word-ops, symmetric control flow (`fn/ntfn`, `whlp/ntwhlp`), and the initial i/o primitive (`sh`).  
**deliverables:** the full lexical and grammar definition documented across the v0.1 handbook.

---

## v0.2: containers, modules, and self-hosting groundwork

v0.2 is the critical next major step, transforming tiny lento from a language primitive into a practical scripting tool.  
this version will introduce the necessary data and structural capabilities for self-hosting.

| feature category | v0.2 planned features | impact |
|------------------|------------------------|---------|
| **data structures** | native container types: lists (arrays) and dictionaries (maps). | enables complex data modeling and efficient data manipulation. |
| **string operations** | robust built-in functions for string manipulation, indexing, and comparison. | necessary for real-world file i/o and data processing. |
| **program structure** | module and import system. | allows code organization, separation of concerns, and library development. |
| **stability** | introduction of a structured exception and error handling mechanism. | enforces code robustness and predictable error recovery. |
| **stdlib hardening** | fully implemented `len`, `to_num`, `to_str` functions. | completes the utility layer of the standard library. |

---

## beyond v0.2: future architecture

following the successful implementation of v0.2, the focus will shift towards performance optimization, potential external ffi (foreign function interface) support, and expanding the language's utility layer based on real-world usage feedback.  

the goal remains a small, fast, and philosophically pure runtime.  

the commitment to the nt-closure law and zero operator precedence will remain absolute throughout all future versions.
