# 06_examples: runnable code snippets

these examples demonstrate fundamental syntax, strict left-to-right evaluation, and control flow using the v0.1 core specification.

---

## example 1: left-to-right arithmetic (zero precedence)

this illustrates how tiny lento ignores traditional operator rules, evaluating strictly from left to right.

```tl
;; what is traditionally 2 + (3 * 4) = 14

result_a et 2 ad 3 xs 4
;; evaluation steps (strictly left to right):
;; 1. (2 ad 3) -> 5
;; 2. (5 xs 4) -> 20
sh ..result a:.. result_a
;; output: result a: 20

;; using a function for grouping (preferred method):
fn calculate_product [a b]
  a xs b bk
ntfn

result_b et 2 ad (calculate_product 3 4)
;; evaluation steps:
;; 1. (calculate_product 3 4) -> 12
;; 2. (2 ad 12) -> 14
sh ..result b:.. result_b
;; output: result b: 14
```

---

## example 2: conditional chains (if, iffy, ntif)

demonstrates the two types of conditional blocks and the nt-closure law.

```tl
x et 5

;; 'if' block: first condition that is true executes, then skips the rest.
if x gt 10
  sh ..x is large..
if x et 5
  sh ..x is exactly 5..
if x lt 6
  sh ..x is less than 6..
ntif
;; output: x is exactly 5 (the chain stops here)

;; 'iffy' block: all conditions that are true execute.
iffy x gt 10
  sh ..x is large (iffy check)..
iffy x et 5
  sh ..x is exactly 5 (iffy check)..
iffy x lt 6
  sh ..x is less than 6 (iffy check)..
ntif
;; output:
;; x is exactly 5 (iffy check)
;; x is less than 6 (iffy check)
```

---

## example 3: inclusive for loop (folp)

demonstrates iterating over an inclusive range using `to`, which includes the end value.

```tl
;; standard, inclusive range (0 to 5)
sh ..counting from 0 to 5:..
folp i in range 0 to 5
  sh i
ntfolp
;; output: 0 1 2 3 4 5

;; inclusive range with a step (start at 1, go up to 10, skipping every other)
sh ..counting by 2 up to 10:..
folp j in range 1 to 10 by 2
  sh j
ntfolp
;; output: 1 3 5 7 9 (11 is skipped as it exceeds 10)
```

---

## example 4: function definition with defaults and return

demonstrates parameter defaults using `et` and the `bk` return keyword.

```tl
;; this function calculates a bonus. factor defaults to 1.
fn get_bonus [salary factor et 1]
  sh ..calculating bonus for.. salary ..with factor.. factor
  salary xs factor bk
ntfn

bonus_a et get_bonus 1000
sh ..bonus a:.. bonus_a
;; output: bonus a: 1000

bonus_b et get_bonus 1000 1.5
sh ..bonus b:.. bonus_b
;; output: bonus b: 1500
```

---

these snippets cover the core operational requirements of the v0.1 specification.

---

© 2025 Travis Halsey (aka "travtherobber")  
This document is part of the **TinyLento Documentation** project.  
Licensed under the **Creative Commons Attribution 4.0 International (CC-BY-4.0)** license.  
https://creativecommons.org/licenses/by/4.0/
