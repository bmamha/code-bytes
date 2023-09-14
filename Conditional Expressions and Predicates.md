#SICP

```Scheme
define (name)
(cond (p1) e1)
 (cond (p2) e2)

```


```Scheme 
(if ⟨predicate⟩ ⟨consequent⟩ ⟨alternative⟩)
```

e.g. 
```Scheme
(define (abs x)
  (if (< x 0)
      (- x)
      x))
```