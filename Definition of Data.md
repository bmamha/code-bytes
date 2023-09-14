
---
date: 2023-08-26
time: 01:01
tags: 
- SICP
- data-abstraction 
---


>[!summary]  Summary: What is Data?
> Data is defined by some collection of selectors and collectors, together with specified conditions that these procedures must fulfill in order to be a valid representation



>[!question] Cues
>data
>cons
>pairs
> [[Data Abstraction]]
> 



>[!note]  Notes
>	We can define the primitive used for constructing pairs in our Scheme language - `cons` using the following
>```Scheme
>(define (cons x y)
  (define (dispatch m)
(cond ((= m 0) x)
  ((= m 1) y) 
  (else 
(error "Argument not 0 or 1:
CONS" m))))
dispatch)
(define (car z) (z 0))
(define (cdr z) (z 1))

### Exercise 2.4:
```Scheme
(define (cons x y) 
  (lambda (m) (m x y)))

(define (car z) 
  (z (lambda (p q) p)))
```

Verify that `(car (cons x y))` yields x by using substitution model.

Cons returns a procedure. But it also accepts an additional procedure into the argument which will be used to evaluate the returned procedure

```Scheme
(car (cons x y))
(car (lambda (m) (m x y)))
(lambda (m) (m x y)) (lambda (p q) p)
(lambda (p q) p) x y)
x
```

