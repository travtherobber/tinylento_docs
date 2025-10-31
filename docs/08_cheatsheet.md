# 08_cheatsheet: quick reference

this is the comprehensive technical reference for the tiny lento v0.1 core.

---

## 1. lexical tokens

| item | syntax | notes |
|------|---------|-------|
| comment | `;; your thought` | ignored to end of line. |
| string | `..text here..` | wrapped in double periods. |
| boolean | `tr`, `nttr` | true and not-true (false). |

---

## 2. variable and assignment

| operation | syntax | notes |
|------------|---------|-------|
| assignment | `name et value` | `et` is dual-purpose: assignment (statement) or comparison (expression). |
| print/show | `sh expr1 expr2` | shows/prints one or more values. `say` is an alias. |

---

## 3. core word-ops (operators)

evaluation is strictly left-to-right with no operator precedence.

| type | word-op | symbol | function |
|------|----------|---------|-----------|
| arithmetic | `ad`, `sb`, `xs`, `by`, `pc` | `+`, `-`, `*`, `/`, `%` | add, subtract, multiply, divide, modulus |
| comparison | `et`, `noet`, `gt`, `lt` | `==`, `!=`, `>`, `<` | equal, not equal, greater than, less than |
| comparison | `gtet`, `ltet` | `>=`, `<=` | greater/less than or equal |
| logic | `an`, `or`, `nt` | — | and, or. `nt` is unary not (`nt expr`). |

---

## 4. functions (nt-closure law)

| operation | syntax | notes |
|------------|---------|-------|
| definition | `fn name [p1 p2 et def] ... ntfn` | parameters are space-delimited. `et` sets a default value. |
| variadic | `fn name [p1 rest et rest_name] ... ntfn` | `et` captures remaining arguments into `rest_name`. |
| return | `bk [expression]` | returns value from function. |
| call | `name expr1 expr2` | arguments are space-delimited expressions. |

---

## 5. control flow blocks (nt-closure law)

all blocks must be closed with their mirrored `nt` keyword.

| block type | start keyword | end keyword | notes |
|-------------|----------------|--------------|--------|
| function | `fn` | `ntfn` | function definition scope. |
| conditional | `if` | `ntif` | executes the first true condition, then stops. |
| run-all cond. | `iffy` | `ntif` | executes all true conditions. |
| while loop | `whlp condition` | `ntwhlp` | loops while condition is true. |
| until loop | `unlp condition` | `ntunlp` | loops while condition is false. |
| do-while loop | `dolp` | `ntdolp condition` | runs once, then loops while condition is true. |
| forever loop | `frlp` | — | loops indefinitely; requires `br` to exit. |

---

## 6. iteration (folp)

| for loop | syntax | notes |
|-----------|---------|-------|
| range loop | `folp i in range start to end [by step]` | inclusive range: includes end value. `by step` is optional. |
| collection loop | `folp element in collection` | iterates over items in a collection (v0.2 feature). |

---

## 7. flow manipulation

| directive | keyword | function |
|------------|----------|-----------|
| break | `br` | exits the current loop block immediately. |
| continue | `ct` | skips the rest of the current loop iteration. |
| reverse parsing | `revfile` | sets token reading to right-to-left for the entire file. |
| reverse execution | `retro` | sets ast execution order to bottom-to-top. |
