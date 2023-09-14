#SICP

Blocks of any powerful language


### 1. Primitive expressions

e.g.  35, "string"

### 2. Means of Combination

(+ 1 2 3)
(operator/function  arguments  )

when defining a procedure 
```Scheme
(define (<name> <formal parameters>)(<body>))
```


### 3. Means of Abstraction




Normal Order vs Applicative-order evaluation

Applicative Order evaluates the body first. Then the final operation or procedure is executed.
Normal-order evaluation "fully expands and then reduces" evaluation method where each procedure is expanded into its definition before elementary calculations take place. 

Applicative Order evaluation reduces executed tasks. The LISP interpreter uses it.