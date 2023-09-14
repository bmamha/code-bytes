---
date: 2023-09-13
tags:
  - SICP/Chapter2
  - lists
reference: SICP
---

Suppose we define x and y to be two lists:

(define x (list 1 2 3))
(define y (list 4 5 6))

What result is printed by the interpreter in response to evaluating each of the following expressions:

(append x y)
(cons x y)
(list x y)


### My Answer:


```Scheme
(define x (list 1 2 3))
(define y (list 4 5 6))
(append x y)
(1 2 3 4 5 6)
(cons x y)
((1 2 3) 4 5 6)
(list x y)
((1 2 3) (4 5 6))
```


The only confusing aspect is how `cons (x y)` results in `(1 2 3) 4 5 6`. But that becomes clear when we realize how we use cons for the construction of lists. As it is, cons (list 1 2 3) (list 4 5 6).
Which is the same as cons (1 2 3) (cons 4 (cons 5 (cons 6 nil)))