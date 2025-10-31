# 01_syntax: lexing rules and reserved words

tinylento's syntax is built for maximum clarity and minimal cognitive load, adhering to simple, space-delimited rules.

---

## lexing rules: the token foundation

the language parser sees the code as a stream of tokens separated by whitespace.

- **whitespace:** tokens are space-delimited.  
- **comments:** everything from `;;` to the end of the line is ignored.  
- **identifiers:** standard alphanumeric names starting with a letter or underscore. they cannot be reserved words.  
- **numbers:** supports integers (`123`, `-4`) and floating-point values (`3.14`).  
- **strings:** always wrapped in double periods (e.g., `..hello world..`), and may safely include spaces.  
- **booleans:** `tr` (true) and `nttr` (false).  
- **end-of-file:** implicit; no line terminators are required.  

---

## reserved words: the language dictionary

these words carry specific meaning and cannot be used as identifiers for variables or functions.

### 1) control flow and blocks

these keywords define scope and structure, strictly adhering to the nt-closure law.

| start/head     | end/closure | purpose                                      |
|----------------|-------------|----------------------------------------------|
| `fn`           | `ntfn`      | function definition                          |
| `if`, `iffy`   | `ntif`      | conditional chains                           |
| `whlp`         | `ntwhlp`    | while loop                                   |
| `unlp`         | `ntunlp`    | until loop (while false)                     |
| `folp`         | `ntfolp`    | for loop (range or collection)               |
| `dolp`         | `ntdolp`    | do-while loop                                |
| `frlp`         | —           | forever loop (exits via `br`)                |
| `br`, `ct`, `bk` | —         | break, continue, return                      |
| `sh`           | —           | show/print output                            |

---

### 2) operators (word-ops)

two-letter operation words replace traditional symbols.

| word-op            | symbol equivalent | function                                      |
|--------------------|-------------------|-----------------------------------------------|
| `et`               | `==` or `=`       | assignment (statement) / equality (expression)|
| `ad`, `sb`, `xs`, `by`, `pc` | `+`, `-`, `*`, `/`, `%` | arithmetic: add, subtract, multiply, divide, modulus |
| `gt`, `lt`         | `>`, `<`          | greater than, less than                        |
| `gtet`, `ltet`     | `>=`, `<=`        | greater/less than or equal                     |
| `noet`             | `!=`              | not equal                                      |
| `an`, `or`, `nt`   | `and`, `or`, `not`| logical operations                              |

---

### 3) iteration helpers

used to structure the header of a `folp` (for loop).

- `in`, `to`, `of`

---

### 4) direction / flow directives

used to intentionally alter the parsing or execution flow.

- `revfile` — reverse token order parsing (file-wide)  
- `retro` — reverse ast execution (bottom-to-top)  
- `ltr` — reset to left-to-right locally  

---

## hybrid symbols (optional shortcuts)

for convenience, standard symbols can be used as shorthand for their respective word-ops.  
the interpreter resolves them to word-ops during parsing.

| symbol | word-op | symbol | word-op |
|--------|---------|--------|---------|
| `+`    | `ad`    | `>=`   | `gtet`  |
| `-`    | `sb`    | `<=`   | `ltet`  |
| `*`    | `xs`    | `!=`   | `noet`  |
| `/`    | `by`    | `==`   | `et`    |
| `%`    | `pc`    | `=`    | `et`    |
| `>`    | `gt`    | `<`    | `lt`    |
