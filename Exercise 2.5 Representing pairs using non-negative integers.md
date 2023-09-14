
---
date: 2023-08-30
time:  02:32
tags: 
  -pairs 
  -SICP 
---


>[!summary]  Summary: 
>There are many interpretations of a pair. 



>[!question] Cues
> #pairs
> #



>[!note]  Notes


```Scheme
> (define (cons a b)
    (* (expt 2 a) (expt 3 b)))
```


represent the pair a and b as the integer that is the product 2^a*3^b

```Scheme
(define (car x)
    (define (division-2 n count)
      (if (= (remainder n 2) 1)
          count
          (division-2 (/ n 2) (+ count 1))))
    (division-2 x 0))
```

`car` will be defined as the number of times our output from `cons` function is divided by 2.

```Scheme
(define (cdr x)
    (define (division-3 n count)
      (if (= (remainder n 3) 0)
       (division-3 (/ n 3) (+ count 1))
       count))
    (division-3 3 0))
```
`cdr` likewise will be defined as the number of times our output from `cons `function is divided by 3.