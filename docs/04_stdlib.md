# 04_stdlib: the core library

the tiny lento standard library (stdlib) is designed to be minimal and high-performance, providing essential utility functions that often wrap or mirror the core word-ops for better functional clarity.

---

## stdlib philosophy

- **minimal surface area:** only essential, frequently needed utilities are included.  
- **consistency:** function names often use the full, unabbreviated version of the word-op (e.g., `add` instead of `ad`).  
- **host assist:** functions that can be dramatically faster via host platform assistance (like `len` for length checking) are included, though they must have a theoretical tiny lento iterative fallback.

---

## core functions (v0.1)

these functions are included in the v0.1 specification and are available globally.

---

### i/o and debugging

| function | word-op basis | purpose |
|-----------|----------------|----------|
| `sh` | n/a | shows/prints one or more expressions to the output stream. |
| `say` | `sh` wrapper | alias for `sh`, often preferred for human readability. |

---

### arithmetic and math

these functions wrap their corresponding word-ops, providing an alternative functional style of computation which is critical for grouping operations (since there is no operator precedence).

| function | word-op basis | purpose |
|-----------|----------------|----------|
| `add` | `ad` | adds two numbers. equivalent to `x ad y`. |
| `sub` | `sb` | subtracts two numbers. equivalent to `x sb y`. |
| `mul` | `xs` | multiplies two numbers. equivalent to `x xs y`. |
| `div` | `by` | divides two numbers. equivalent to `x by y`. |
| `mod` | `pc` | calculates the remainder (modulus). equivalent to `x pc y`. |

---

### utility (future container support)

these are defined in v0.1 but will become fully functional only upon the introduction of native container types in v0.2.

| function | v0.1 status | purpose |
|-----------|-------------|----------|
| `len` | placeholder / host-assisted | returns the length of a string or list. |
| `to_num` | planned | safely converts a string representation to a number. |
| `to_str` | planned | safely converts any value to its string representation. |

---

## usage example

using the functional style is the recommended way to manage complex arithmetic due to the strict left-to-right evaluation:

```tl
;; naive (left-to-right) evaluation in tiny lento:
;; result et 5 ad 10 xs 2
;; (5 ad 10) -> 15
;; 15 xs 2 -> 30

;; functional style (preferred for grouping):
result et mul (add 5 10) 2
;; (add 5 10) evaluates first -> 15
;; mul 15 2 evaluates next -> 30

sh result
```

the stdlib ensures that even complex expressions can be written clearly and deterministically using function composition.

---

© 2025 Travis Halsey (aka "travtherobber")  
This document is part of the **TinyLento Documentation** project.  
Licensed under the **Creative Commons Attribution 4.0 International (CC-BY-4.0)** license.  
https://creativecommons.org/licenses/by/4.0/
