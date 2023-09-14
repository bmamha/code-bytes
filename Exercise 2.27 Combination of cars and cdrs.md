---
date: 2023-09-13
tags:
  - lists
  - mapping
  - SICP/Chapter2
reference: SICP
---


Exercise 2.25: Give combinations of cars and cdrs that will pick 7 from each of the following lists:

(1 3 (5 7) 9)
((7))
(1 (2 (3 (4 (5 (6 7))))))



### My Answer:

```Scheme
 (define list0 (list 1 3 (list 5 7) 9))
 (car (cdr (car (cdr (cdr list0)))))
 ```

```Scheme
(define list1 (list (list 7)))
(car (car list1))
```




```Scheme
(define list2 (list 1 (list 2 (list 3 (list 4 (list 5 (list 6 7)))))))
(car (cdr (car (cdr (car (cdr (car (cdr (car (cdr (car (cdr list2)))))))))))) 

```



As it is mentally exhausting to keep track in one-go I used the interpreter to breakdown the problem step by step.

```Scheme
(car(cdr list2))
(2 (3 (4 (5 (6 7)))))
> (cdr (car (cdr list2)))
((3 (4 (5 (6 7)))))
> (car (cdr (car (cdr list2))))
(3 (4 (5 (6 7))))
> (cdr (car (cdr (car (cdr list2)))))
((4 (5 (6 7))))
> (car (cdr (car (cdr (car (cdr list2))))))
(4 (5 (6 7)))
> (cdr (car (cdr (car (cdr (car (cdr list2)))))))
((5 (6 7)))
> (cdr (car (cdr (car (cdr (car (cdr (car (cdr list2)))))))))
((6 7))
> (car (cdr (car (cdr (car (cdr (car (cdr (car (cdr (car (cdr list2)))))))))))) 
7
```

The most confusing aspect is that we need to use car when only an element is left in our list. 