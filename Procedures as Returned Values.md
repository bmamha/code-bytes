---
date: 2023-07-26
time: 14:41
tags:
  - SICP
reference: SICP
---



>[!summary]  Summary: 
> We can create procedures whose returned values are themselves procedures.
> 
>


### Cues

>[!question] Cues
> - procedures as returned values. 

### Notes

>[!note]  #### Functions as returned values
   > A good example to illustrate how we can return procedures within a procedure is the square root function
   > 
   


>[!note]  Average Damping
> this function allows us to calculate the average of an input and the function of the input.
> 
>
   ```Scheme
(define (average-damp f)
  (lambda (x)
      (average x (f x))))
```

>[!note]  Square root procedure as returned value
Using fixed-point procedure we can reformulate the square root procedure as follows.
```Scheme
(define (sqrt x)
  (fixed-point
  (average-damp 
  (lambda (y) (/ x y)))
  1.0))
```





