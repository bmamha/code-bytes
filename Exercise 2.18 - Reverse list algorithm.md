---
date: 2023-09-03
reference: SICP
tags:
  - lists
---

 Define a procedure reverse that takes a list as argument and returns a list of the same elements in reverse order: 
 
`(reverse (list 1 4 9 16 25))`
`(25 16 9 4 1)`


# My Answer:

```Scheme
(define (reverse list1)
    (define (reverse-iter n)
      (if (= n 0)
          (cons (car list1) nil)
          (cons (list-ref list1 n)
                (reverse-iter (- n 1)))))
    (reverse-iter (- (length list1) 1))) 
```

- Create an iterative function with argument n (index of the list).
- When n equals 0, return a pair of the first element of our list and nil (this will be the last element of our reverse procedure which is the first element of the original list)
- If not, return a pair of the list item of n (nth index) and the iterative function with an argument of `n - 1`
- At each step (`cons (list-ref list1 n) (cons list-ref list1 (- n 1)))` and so on is created with the last element being a pair of the first element of list `car list1` paired with nil when (- n 1) becomes 0.
- `reverse-iter` starts from the last element of the list whose index will be length of the list subtracted by 1.



```Scheme
cons(list-ref list1 n) (reverse-iter (- n 1))
cons(list-ref list1 n)(cons list-ref list1 (- n1)(reverse-iter (- n 2)))
cons(list-ref list1 n)(cons list-ref list1 (-n 1)(cons(list1-ref list1 (-n 2)reverse-iter(-n 3))))
```

let's say (-n 3) is 0 as the list has only 4 elements, then

```Scheme
cons(list-ref list1 n) (reverse-iter (- n 1) cons(list-ref list1 - n 2)(cons(car list1) nil))
```

will give us the reverse list.