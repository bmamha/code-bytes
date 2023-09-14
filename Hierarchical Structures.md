---
date: 2023-09-10
tags:
  - lists
  - data-structures
  - SICP/Chapter2
reference: SICP
---



>[!summary]  Summary: 
>Representation of sequences in a list may themselves be sequences.
>e.g. ((1 2) 3 4) 



>[!question] Cues
> - count-leaves
> - tree structure
> - pair?



>[!note]  Notes
>We can think of sequences whose elements are sequences as trees. 
>The elements of the sequence are a branch of a tree
>Elements are themselves sequences as subtrees.
>We can use recursion to find the total number of branches.
>We can use the procedure `pair?` to evaluate if an object is a pair.
>Our `count-leaves` procedure can be configured as follows
>```Scheme
> (define (count-leaves x)
>  (cond ((null? x) 0)
>  ((not (pair? x)) 1)
>  (else (+ (count-leaves (car x))
>           (count-leaves (cdr x))))))
>  ```
>  So for `list 1 2 3 4`, count-leaves will simply be the sum of `count-leaves (car x)` as each element is not a pair `+ 1 1 1 1 0` = 4
>  For list (1 2) 3 (4 5)
>  ```Scheme
>      (+ (count-leaves (1 2)
>      (+ (count-leaves ( 3 (4 5))
>  (+ (count-leaves 1 + count-leaves (2))
>  (+ count-leaves 3 
>  (+ count-leaves (4 5))
>(+ 1(+ 1)
>(+1 (+ count-leaves 4 (+ count-leaves 5)
>(+ 2 (+ 1 1 1)
>5
>```
>Thus length of the list is 3 where as total branches is 5



> ![[Exercise 2.24 -interpreter, box-and-pointer structure and interpretation as tree of a lists]]





