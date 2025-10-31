# 03_functions: defining and calling procedures

functions are the primary means of creating reusable, grouped logic in tiny lento, and they are the only way to enforce operational grouping due to the strict left-to-right evaluation policy.

---

## 1. function definition (fn ... ntfn)

functions are defined using the `fn` head and strictly closed using `ntfn`, adhering to the nt-closure law.  
the basic structure includes the function name followed by a bracketed list of parameters.

```tl
;; simple function taking two arguments
fn add_nums [a b]
  a ad b bk
ntfn
```

---

## 2. parameter handling

parameters are positional by default. tiny lento provides explicit syntax for both default values and variadic arguments.

### default arguments
use the `et` operator within the parameter list to assign a default value.

```tl
;; takes two arguments, second defaults to 10
fn calc_rate [input_val rate et 10]
  input_val xs rate bk
ntfn

sh calc_rate 5        ;; result: 50 (5 xs 10)
sh calc_rate 5 2      ;; result: 10 (5 xs 2)
```

### variadic arguments
a single identifier preceded by `et` at the end of the parameter list will capture all remaining arguments into a list.  
this identifier becomes the list variable name.

```tl
;; accepts a starting value and any number of subsequent numbers
fn sum_list [start_val items_to_sum et rest]
  ;; logic to iterate through rest will be needed in v0.2+
  sh start_val
  sh items_to_sum
  bk
ntfn

;; calls the function with one fixed arg and three variadic args
sum_list 100 1 2 3
```

---

## 3. function calls

calling a function is done simply by listing the function name followed by its arguments.  
there are no parentheses required. arguments are resolved and passed as expressions.

```tl
val_a et 5
val_b et 7

;; function call syntax
result et add_nums val_a val_b

;; example using chained evaluation (left-to-right)
sh add_nums (add_nums 1 2) 3
;; this calls (add_nums 1 2) first, then calls add_nums (3) 3
;; in tiny lento, this would require explicit grouping or internal logic
```

---

## 4. return values

the return value of a function is determined by the `bk` keyword.

### explicit return
use `bk` followed by the value or expression to be returned.

```tl
fn get_ten []
  10 bk
ntfn
```

### default return
if execution reaches `ntfn` without encountering a `bk`, the function implicitly returns the boolean value `nttr` (false).

the design is optimized for flat, declarative execution, and complex operations must be intentionally structured via function decomposition.
