---
date: 2023-09-09
reference: SICP
tags:
  - lists
  - mapping
---


The procedure square-list takes a list of numbers as argument and returns a list of the squares of those numbers.
```Scheme
(square-list (list 1 2 3 4))
(1 4 9 16)
```

Here are two different definitions of square-list. Complete both of them by filling in the missing expressions:
```Scheme
(define (square-list items)
  (if (null? items)
      nil
      (cons ⟨??⟩ ⟨??⟩)))

(define (square-list items)
  (map ⟨??⟩ ⟨??⟩))
```


### My Answer:

From scratch:

```Scheme
(define (square-list items)
  (if (null? items)
      nil
      (cons ((lambda (x) (* x x)) (car items)) 
            (square-list (cdr items)))))
    
```


Using map abstraction:

```Scheme
 (define (square-list items)
 (map (lambda (x) (* x x)) items)
 ```


