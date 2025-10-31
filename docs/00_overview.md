# 00_overview: the tiny lento vision

tiny lento is being built as a minimalist, speakable, and deterministically simple language.  
its core design rejects complexity, aiming for code that is clear, symmetrical, and behaves exactly as written.

---

## the core philosophy

the driving force behind tiny lento is speakable code.  
the language is engineered so that code sounds like direct instructions when read aloud, minimizing symbolic noise in favor of word-ops (like `ad`, `sb`, `xs`).

### key philosophical commitments

- **minimal syntax:** words carry the meaning; symbols are sparse and often optional.  
- **determinism:** evaluation is strictly left-to-right, which eliminates hidden operator precedence. any grouping must be achieved explicitly using functions.  
- **symmetry (nt-closure law):** every control block adheres to the nt-closure law, closing with a mirrored `nt<keyword>` pair (e.g., `fn ... ntfn`, `whlp ... ntwhlp`). this provides crystal-clear scope boundaries.

---

## a fresh approach to flow

tiny lento incorporates control flow as a deliberate, opt-in feature, rather than a hidden mechanism.

- **dual-use et:** the word `et` (equal) serves as both the assignment statement (`x et 5`) and the equality comparison expression (`a et b`).  
- **inclusive ranges:** the `folp` (for loop) uses a range syntax that is inclusive (`start to end [by step]`), making boundary conditions easier to reason about.  
- **directional control:** the language includes directives like `revfile` (right-to-left parsing) and `retro` (bottom-to-top ast execution). this allows developers to safely and intentionally experiment with reversed execution flows without physical "reading upwards".

---

## the path forward (v0.2+)

v0.1 established the language's fundamental architecture: expressions, assignment, core control flow, and functions. this foundation is now frozen.

the focus is shifting entirely toward a production-ready tiny lento core, achieved in planned versions:

- **v0.2 (planned):** the critical next step will introduce native container types (lists/dicts), robust built-in string operations, a proper module/import system, and exceptions. this stage is the necessary groundwork for a self-sufficient core.

the language documentation is definitive for the current specification.
