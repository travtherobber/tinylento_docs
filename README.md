# tiny lento v0.1

tiny lento is a minimalist, speakable, and rigorously deterministic programming language.  
version 0.1 represents the frozen core specification for the language architecture, built on principles of maximum clarity and predictable flow.

---

## philosophy: speakable code, zero precedence

tiny lento is engineered for audibility.  
the design rejects symbolic noise, replacing it with word-ops such as `ad` for add and `xs` for multiply.  
the code should sound like a set of direct instructions when read aloud.

---

## key tenets

### deterministic evaluation
evaluation is strictly left-to-right, with no operator precedence.  
any operational grouping must be achieved explicitly by calling functions.

### symmetry (nt-closure law)
every block keyword has a mirrored closing keyword, enforcing clear scope boundaries.  
this is known as the **nt-closure law**, for example:

```tl
fn ... ntfn
whlp ... ntwhlp
if ... ntif
```

---

## core language features (v0.1)

the v0.1 specification defines the lexical, control flow, and functional primitives of tiny lento.

### lexical structure
- space-delimited tokens  
- strings wrapped in double periods `..text..`  
- booleans: `tr` and `nttr`

### assignment and equality
the word `et` (equal) serves a dual purpose:  
- **assignment:** when used in statements — `x et 5`  
- **equality:** when used inside expressions — `a et b`

### control blocks
structured keywords define flow and scope:

```tl
if / iffy  — conditional chains
whlp       — while
unlp       — until
dolp       — do-while
folp       — for (range or collection)
```

`folp` handles inclusive ranges `start to end [by step]` or iteration over collections.

### functions
function definitions use `fn ... ntfn`.  
they support positional arguments, defaults via `et`, and variadic capture using `nm et restname`.

### flow control
built-in directives enable controlled reversal of program flow:  
- `revfile` — reverse token parsing for the entire file  
- `retro` — reverse ast execution  

these allow intentional, predictable manipulation of execution order.

---

## documentation structure

this repository contains the definitive technical documentation for the tiny lento language.

| document | focus |
|-----------|--------|
| [00_overview.md](docs/00_overview.md) | high-level philosophy and architectural goals |
| [01_syntax.md](docs/01_syntax.md) | lexing rules and the complete list of reserved words |
| [05_grammar.md](docs/05_grammar.md) | readable ebnf-style grammar definition |
| [08_cheatsheet.md](docs/08_cheatsheet.md) | quick command reference for syntax and ops |

---

tiny lento is minimal by design.  
its clarity comes not from what it adds, but from what it refuses to need.