# 05_grammar: language structure (ebnf)

this document defines the complete syntax of the tiny lento v0.1 frozen core using a readable extended backus–naur form (ebnf).

---

## 1. grammar conventions

```
::=   means "is defined as"
|     means "logical or" (alternative)
( ... )  grouping
[ ... ]  optional element (zero or one)
{ ... }  zero or more repetitions
```

---

## 2. lexical tokens

tokens are the building blocks defined in `01_syntax.md`.

```
IDENTIFIER       ::= [A-Za-z_] { [A-Za-z0-9_] } ; cannot be a reserved word
NUMBER           ::= [ '-' ] DIGIT+ [ '.' DIGIT+ ]
STRING           ::= '..' { ANY CHARACTER } '..'
BOOLEAN          ::= 'tr' | 'nttr'
COMMENT          ::= ';;' { ANY CHARACTER EXCEPT NEWLINE }
```

---

## 3. program structure

the root of a tiny lento program is a sequence of statements.

```
program      ::= statement*

statement    ::= declaration
               | assignment
               | if_chain
               | loop_block
               | flow_control
               | print_statement
               | expression

block_body   ::= statement*

flow_control ::= 'br' | 'ct' | 'bk' [ expression ]
```

---

## 4. functions and calls

function definitions and the structure of a function call are defined here.

```
declaration  ::= 'fn' IDENTIFIER '[' parameters ']' block_body 'ntfn'

parameters   ::= ( IDENTIFIER [ 'et' expression ] [ 'et' IDENTIFIER ] )*

call_args    ::= expression+
```

---

## 5. control blocks

all control blocks use the nt-closure law and are defined with their structural keywords.

```
if_chain     ::= ( ( 'if' | 'iffy' ) expression block_body )+ 'ntif'

loop_block   ::= while_loop
               | until_loop
               | for_loop
               | do_while_loop
               | forever_loop

while_loop   ::= 'whlp' expression block_body 'ntwhlp'

until_loop   ::= 'unlp' expression block_body 'ntunlp'

for_loop     ::= 'folp' IDENTIFIER ( 'in' | 'of' ) ( range | expression ) block_body 'ntfolp'

range        ::= expression 'to' expression [ 'by' expression ]

do_while_loop::= 'dolp' block_body 'ntdolp' expression

forever_loop ::= 'frlp' block_body
```

---

## 6. expression and operations

due to strict left-to-right evaluation, there is only one expression rule, defined by unary and binary word-ops.  
function calls are treated as primary expressions.

```
assignment   ::= IDENTIFIER 'et' expression

print_statement::= 'sh' expression+

expression   ::= unary_expression { operator unary_expression }

unary_expression ::= 'nt' unary_expression
                   | primary_expression

primary_expression ::= NUMBER
                     | STRING
                     | BOOLEAN
                     | IDENTIFIER [ call_args ]

operator     ::= 'ad' | 'sb' | 'xs' | 'by' | 'pc'
               | 'gt' | 'lt' | 'gtet' | 'ltet' | 'noet'
               | 'et' | 'an' | 'or'
```

---

this formal definition completes the grammar specification for tiny lento v0.1.
