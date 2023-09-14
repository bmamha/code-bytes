
---
date: 2023-08-30
time:  02:42
tags: SICP 
---


>[!summary]  Summary: 
>We can manipulate procedures to get by without numbers. Church numerals allow us to represent numbers and addition using only procedures (lambda functions). 



>[!question] Cues
> #Church-numerals
> #Alonso-Church


>[!note]  Notes
>The first thing we have to do to represent Church numerals is define zero.
>```Scheme
>(define zero (lambda (f) (lambda (x) x)))
>```
So zero is defined as a function (lambda(f)) with an inner function (lambda (x)) which is an identity function. 
>We will define the procedure of adding 1 (`add-1`) as follows.
>```Scheme
(define (add-1 n)
  (lambda (f) (lambda (x) (f ((n f) x)))))
  >```
So in this scenario, `f` will be an input for `n` and x will be an input for the output of `(n f)`. The procedure will be applied to the output. So in essence adding-1 implies we are subjecting our input to an additional procedure of `f`. 
Thus 1 becomes, 
>```Scheme
(lambda (f)(lambda(x)(f x)))

Two becomes,
```Scheme
>lambda (f) (lambda (x)(f(f x))))
>```
And it continues as such with `f` procedure applying to each additional number
### Exercise 2.6

```Scheme
(define (add-1 zero))
 (lambda (f) (lambda (x) (f ((n f)x)))))
 (lambda (f) (lambda (x) (f (zero f) x)))
 (lambda (f) (lambda (x) (f ((lambda(f) (lambda (x) x)f)x))
 (lambda (f) (lambda (x) (f (lambda(x) x)x)))
 (lambda (f)(lambda(x)(f x)))

lambda (f) (lambda(x) (f (one f)x))
lambda (f) (lambda (x) (f(lambda(f) (lambda(x)(f x)f)x)

lambda (f) (lambda (x) (f((lambda(x) (f x)) x)
lambda (f) (lambda (x)(f(f x))))
```

The easiest solution I found from the community
```Scheme
(define zero
  (lambda (f) (lambda (x) x)))

(define one
  (lambda (f) (lambda (x) (f x))))

(define two
  (lambda (f) (lambda (x) (f (f x)))))

define (add n m)
(lambda (f) (lambda(x) ((n f) ((m f x))))

```