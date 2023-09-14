---
date: 2023-09-02
tags:
  - SICP
  - lists
  - LISP
reference: SICP
---



>[!summary]  Summary:
> Lists and operations on lists can be derived from the primitive data structure of `cons` (pairs). The useful property of closure allows us to create hierarchical data structures.



>[!question] Cues
>- lists
>- closure property
>- length
>- list-ref
>- append
> 



>[!note]  Notes
> `List`: A sequence of pairs formed by nested conses
> e,g. `(cons 1(cons 2(cons 4(cons 4 nil))))`
> 
> `Closure`: A property of an operation for combining data objects where combined outputs of the operation can themselves be combined using the same operation. It allows us to create hierarchical data structures.
> 
> Scheme (Lisp) has the primitive data structure `list` to create lists.
> 
> e.g. `(define one-through-four (list 1 2 3 4))`
>
We can use car and cdr operations on a list.
>
`(car one-through-four)`
>  `1`
>  `(cdr one-through-four)`
>  `(2 3 4)`
>  
We can add to the list by using `cons`
>
> `(cons 5 one-through-four)`
>  ``(5 1 2 3 4)`
>  # List Operations
>  `List Ref`: Takes as arguments a list and a number n and returns the nth item of the list. 
>  ```Scheme
>  (define (list-ref items n)
>  (if (= n 0)
>       (car items)
>       (list-ref (cdr items (-n 1))))
>   ```
If `n=0` , `car items` returns the first item on the list. If `n > 1` the rest of the elements in items are extracted using cdr. That operation will keep going till `n-1` becomes `0`. 
>
>`length`: We can define the length of a list using the algorithm below.
>```Scheme
  >  (define (length items)
    > if (null? items)
   >   0
    > (+ 1 (length(cdr items)))))
   > ```
> An alternative iterative method for length
> ```Scheme
> (define (length items)
  (define (length-iter a count)
    >(if (null? a)
          >     count
          >    (length-iter (cdr a) 
          >    (+ 1 count))))
  >(length-iter items 0))
  >```
`Append`: takes two lists as arguments and combines their elements to make a new list. Can be considered as 'cons up'
e.g.`(append (list 1 4 9 16) list (1 3 5 7)`
`(1 4 9  16 1 3 5 7`

![[Exercise 2.17 - Find last element of a list]]
![[Exercise 2.18 - Reverse list algorithm]]


![[Exercise 2.19 - Using Lists for our Count Change Procedure]]


![[Exercise 2.20 Applying procedure to multiple arguments]]