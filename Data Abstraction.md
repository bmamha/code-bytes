
---
date: 2023-08-18
time:  19:49
tags: 
reference: SICP
---


>[!summary]  Summary:  
>Data Abstraction is the general technique of isolating the parts of a program that deal with how data objects are presented from the parts of the program that deal with how objects are used.



>[!question] Cues
> pairs
> cons
> cdr 
> car



>[!note]  Notes
>




### Code Snippets:

- code to define adding, subtraction, multiplication and divison of rational numbers.
```Scheme
(define (add-rat x y)
  (make-rat (+ (* (numer x) (denom y))
               (* (numer y) (denom x)))
            (* (denom x) (denom y))))

(define (sub-rat x y)
  (make-rat (- (* (numer x) (denom y))
               (* (numer y) (denom x)))
            (* (denom x) (denom y))))

(define (mul-rat x y)
  (make-rat (* (numer x) (numer y))
            (* (denom x) (denom y))))

(define (div-rat x y)
  (make-rat (* (numer x) (denom y))
            (* (denom x) (numer y))))

(define (equal-rat? x y)
  (= (* (numer x) (denom y))
     (* (numer y) (denom x))))
```


Define rational numbers as a pairing of a numerator and denominator - n/d.
```Scheme
(define (make-rat n d) (cons n d))
(define (numer x) (car x))
(define (denom x) (cdr x))
```


code to have print format for our rational number. 
```Scheme
(define (print-rat x)
  (newline)
  (display (numer x))
  (display "/")
  (display (denom x)))
```


A better definition of rational numbers which reduces the numerator and denominator values to the lowest term. 
```Scheme
(define (make-rat n d)
  (let ((g (gcd n d)))
    (cons (/ n g) 
          (/ d g))))
```


### Exercise 2.1:
An even better construction of rational numbers which takes into account the negative or positive values of the terms.

```Scheme
(define (make-rat n d)
    (let ((g (gcd n d)))
      (if (or (and (> n 0) (> d 0)) (and (< n 0) (< d 0)))
          (cons (abs (/ n g))
                (abs(/ d g)))
          (if (> n  0)
              (cons (- 0 (/ n g))
                    (abs (/ d g)))
              (cons (/ n g)
                    (abs (/ d g)))))))
```
