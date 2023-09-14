---
date: 2023-09-07
reference: SICP
tags:
  - SICP
  - lists
  - Scheme
  - SICP/Chapter2
---

The procedures +, *, and list take arbitrary numbers of arguments. One way to define such procedures is to use define with dotted-tail notation. In a procedure definition, a parameter list that has a dot before the last parameter name indicates that, when the procedure is called, the initial parameters (if any) will have as values the initial arguments, as usual, but the final parameter’s value will be a list of any remaining arguments. For instance, given the definition

`(define (f x y . z) ⟨body⟩)`

the procedure f can be called with two or more arguments. If we evaluate

`(f 1 2 3 4 5 6)`

then in the body of f, x will be 1, y will be 2, and z will be the list (3 4 5 6). Given the definition

`(define (g . w) ⟨body⟩)`

the procedure g can be called with zero or more arguments. If we evaluate

`(g 1 2 3 4 5 6)`

then in the body of g, w will be the list (1 2 3 4 5 6).77

Use this notation to write a procedure same-parity that takes one or more integers and returns a list of all the arguments that have the same even-odd parity as the first argument. For example,

(same-parity 1 2 3 4 5 6 7)
(1 3 5 7)

(same-parity 2 3 4 5 6 7)
(2 4 6)



### My Answer:

My answer has issues. 

```Scheme
(define (same-parity x . y)
    (append list x
    (if (even? x)
        ((if (even? (car (y))) (cons (car y))) (same-parity x . (cdr y)))
        ((if (odd? (car (y))) (cons (car y))) (same-parity x . (cdr y))))))
> ```

I tried to use append where the first element x is appended with the rest of the elements with y if the elements are the same as x's 'evenness/oddness'.

`application: not a procedure;
 `expected a procedure that can be applied to arguments
  given: (4 1 2)`
  
I had difficulty applying procedures which work on lists on the arguments. How do I return them as a list. 



I will analyze the Community solution to get a better understanding. 

```Scheme
(let (yes? (if (even? first)
			   even?
			   odd?)))
 (define (iter items result)
 (if (null? items)
     (reverse result)
     (iter (cdr items) (if (yes? (car items))
                            (cons (car items) result)
                            result))))
    (iter rest (list first)))))
    ```

We first defined a procedure `yes` which returns an even? or odd? procedure depending on whether its argument is even or odd respectively.

We then create an iterative procedure `iter`
It checks if a list is null to then return a reversed list of our result.

If not, the iterative procedure is as follows:
`cdr items` the first item of the list is popped off,
For our `result` argument, 
`yes? (car items)` checks whether the first element of our items list, `car items` has the same even or odd property as our `first` argument. 

If it does, then `car items` is attached to our result by using `cons (car items) result` . If not `result` stays the same. 

We run our `iter` procedure with our `rest` list and a list with a single item `first` as our starting point.

The reason we reverse our list when `cdr items` becomes empty is because we are adding items at the beginning of our `result` list. 

