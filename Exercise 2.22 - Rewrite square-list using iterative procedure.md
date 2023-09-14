---
date: 2023-09-09
reference: SICP
tags:
  - lists
  - mapping
---

 Louis Reasoner tries to rewrite the first square-list procedure of Exercise 2.21 so that it evolves an iterative process:

```Scheme
(define (square-list items)
  (define (iter things answer)
    (if (null? things)
        answer
        (iter (cdr things)
              (cons (square (car things))
                    answer))))
  (iter items nil))
  ```


Unfortunately, defining square-list this way produces the answer list in the reverse order of the one desired. Why?

Louis then tries to fix his bug by interchanging the arguments to cons: 

```Scheme
(define (square-list items)
  (define (iter things answer)
    (if (null? things)
        answer
        (iter (cdr things)
              (cons answer
                    (square 
                     (car things))))))
  (iter items nil))
  ```


This doesn’t work either. Explain. 


### My Answer:


If we go item by item for list 1 2 3 4 using the first procedure:
```Scheme
square-list list 1 2 3 4
(iter list 1 2 3 4 nil)
(iter list 2 3 4 (cons 1 nil))
(iter list 3 4 (cons 4 (cons 1 nil))
(iter list 4 (cons 9 (cons 4 (cons 1 nil)))
(iter list () (cons 16 (cons 9 (cons 4 (cons 1 nil))))
(cons 16 (cons 9 (cons 4 (cons 1))))))
list 16 9 4 1
```

As each item on the list gets processed using the square procedure, it is added as the first element of our `answer` list. 

Reversing the procedure with,
`cons answer (square (car things)` does not work to as well as the nil item should not be at the beginning of our list constructor.


```Scheme
  (iter list 1 2 3 4 nil)
  (iter list 2 3 4 (cons nil 1))
  (iter list 3 4 (cons (cons nil 1) 4))
  (iter list 4 (cons (cons (cons nil 1) 4) 9))
  (iter list () (cons (cons (cons (cons nil 1) 4) 9) 16)
  (((( , 1) 4) 9) 16) 
  //this is not a normal list
```


