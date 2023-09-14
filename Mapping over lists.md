---
date: 2023-09-09
tags:
  - SICP
  - lists
  - mapping
reference: SICP
---



---

>[!summary]  Summary: Mapping
>Mapping is an operation to apply some transformation to each element in a list and generate a list of results. 



>[!question] Cues
> mapping
> map
> for-each




>[!note]  Notes
>Abstraction of `map` procedure
>```Scheme
>(define (map proc items)
> (if (null? items)
> nil
> (cons (proc (car items))
>        (map proc (cdr items)))))
> ```
> We create our list using our usual `cons a (cons b(...(nil)` constructor. `proc` procedure is applied to Each item in our items list (`car items`) and paired with the procedure itself applied to the rest of the items (`cdr items`)
> Instead of creating the map procedure from scratch each time e.g. 
> ```Scheme
>    (define (scale-list items factor)
 > (if (null? items)
   >   nil
     > (cons (* (car items) factor)
       > (scale-list (cdr items) 
         >               factor))))
        > (scale-list (list 1 2 3 4 5) 10)
>         (10 20 30 40 50)
>   ```
>   We can use our `map` abstraction as follows:
>   ```Scheme
>    (define (scale-list items factor)
>       (map (lambda (x) (* x factor))
>              items)
>   ```



![[Exercise 2.21 Procedure square-list]]

>![[Exercise 2.22 - Rewrite square-list using iterative procedure]] 

![[Exercise 2.23 - for-each procedure]]

![[Exercise 2.24 -interpreter, box-and-pointer structure and interpretation as tree of a lists]]


![[Exercise 2.27 Combination of cars and cdrs]]



![[Exercise 2.26 Use of append cons and list on a pair of lists]]