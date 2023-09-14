---
date: 2023-09-04
tags:
  - recursion
reference: SICP
---
```Scheme
(define (count-change amount)
  (cc amount 5))

(define (cc amount kinds-of-coins)
  (cond ((= amount 0) 1)
        ((or (< amount 0) 
             (= kinds-of-coins 0)) 
         0)
        (else 
         (+ (cc amount (- kinds-of-coins 1))
            (cc (- amount (first-denomination 
                           kinds-of-coins))
                kinds-of-coins)))))

(define (first-denomination kinds-of-coins)
  (cond ((= kinds-of-coins 1) 1)
        ((= kinds-of-coins 2) 5)
        ((= kinds-of-coins 3) 10)
        ((= kinds-of-coins 4) 25)
        ((= kinds-of-coins 5) 50)))
```



The procedure only counts when the amount to be subtracted matches the denomination exactly i.e. amount = 0 or (amount - first-denomination kind of coins - 0). The rest of the time the procedure is recursively outputs the next procedures,

Either the denomination is subtracted by 1. 
(cc amount (- kinds-of-coins 1))

Or, 
the amount is reduced by the denomination of the coin.
cc (- amount (first-denomination kinds-of-coins)) kinds-of-coins).


It is quite ingenious as it covers all possibilities till the coin is covered by the lowest denomination - The permutations are the sum of the combinations of the first-denominations and all the denominations below it which add up to the amount. 