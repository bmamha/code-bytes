---
date: 2023-09-03
reference: SICP
tags:
  - lists
  
---


Define a procedure last-pair that returns the list that contains only the last element of a given (nonempty) list: 

`(last-pair (list 23 72 149 34))`
`(34)`


# My Answer:

```Scheme
(define (last-pair list)
    (list-ref list (- (length list) 1)))
```    

Using `list-ref`, it will simply be the value of the last item on the list (found by subtracting length of list by 1)

