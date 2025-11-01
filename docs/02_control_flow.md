# 02_control_flow: structured execution

tinylento uses a highly structured control flow, strictly adhering to the nt-closure law where every block keyword has a mirrored ending (e.g., `whlp` / `ntwhlp`). this ensures scope is always explicitly defined and clear.

---

## 1. conditional blocks

conditionals use the `if` and `iffy` keywords, always closing with `ntif`.

### if (first-match)
executes the first block whose expression evaluates to `tr`, then jumps to `ntif` — standard conditional chain.

```tl
if x gt 5
  sh ..x is large..
if x et 5
  sh ..x is perfect..
if x lt 5
  sh ..x is small..
ntif
```

### iffy (run-all)
executes all subsequent blocks whose expression evaluates to `tr`. execution continues through the chain regardless of previous matches.

```tl
iffy flag1
  sh ..flag one is set..
if flag2
  sh ..flag two is set..
ntif
```

note: you can start with `iffy` and transition to `if` within the same `ntif` closure, mixing run-all and first-match modes.

---

## 2. loop structures

loops are defined by four-letter head words, emphasizing readability over cryptic abbreviations.

### whlp ... ntwhlp (while loop)
executes the block repeatedly as long as the conditional expression evaluates to `tr`.

```tl
cnt et 0
whlp cnt lt 5
  sh cnt
  cnt et cnt ad 1
ntwhlp
```

### unlp ... ntunlp (until loop)
executes the block repeatedly as long as the conditional expression evaluates to `nttr` (false).

```tl
done et nttr
unlp done
  ;; loop runs until done becomes tr
  sh ..working..
  done et tr
ntunlp
```

### folp ... ntfolp (for loop)
iterates over collections or defined ranges.

#### inclusive range
ranges are always inclusive of the end value.

```tl
folp i in 1 to 10 by 2
  sh i ;; outputs 1, 3, 5, 7, 9
ntfolp
```

#### collection iteration
uses `in` or `of` (future container types).

```tl
;; assuming list_of_names is a collection in v0.2+
folp name in list_of_names
  sh name
ntfolp
```

### dolp ... ntdolp (do-while loop)
executes the block once before checking the condition at the end.

```tl
dolp
  sh ..run once..
ntdolp tr ;; loop condition is true (runs forever or until br)
```

### frlp (forever loop)
an infinite loop that must be exited via `br`.

```tl
frlp
  sh ..looping..
  br ;; exits the loop immediately
ntfrlp ;; closure not strictly needed but implied by scope end
```

---

## 3. flow keywords

- **br (break):** immediately exits the nearest enclosing loop (`whlp`, `folp`, `frlp`, etc.).  
- **ct (continue):** immediately skips the remainder of the current loop iteration and proceeds to the next iteration’s condition check.  
- **bk (return):** exits the current function (`fn`) and returns a value. if no value is provided, the function returns `nttr` by default.  

---

## 4. directional flow directives

these keywords modify how the language engine parses or executes the code. they are designed for intentional use cases and must be explicitly called.

- **revfile:** placed at the top of a file, this directive causes the parser to read tokens right-to-left. execution proceeds normally on the resulting reversed ast.  
- **retro:** this directive causes the compiled abstract syntax tree (ast) to be executed in reverse order (bottom-to-top). the scope stack is still respected.  
- **ltr:** used within a block governed by `revfile` or `retro`, this resets the flow back to the default left-to-right execution mode for the current block.  

---

© 2025 Travis Halsey (aka "travtherobber")  
This document is part of the **TinyLento Documentation** project.  
Licensed under the **Creative Commons Attribution 4.0 International (CC-BY-4.0)** license.  
https://creativecommons.org/licenses/by/4.0/
