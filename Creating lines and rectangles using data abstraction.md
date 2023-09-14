
---
date: 2023-08-25
time:  14:24
tags: SICP
---


>[!summary]  Summary: 
>This note will show how layers of abstraction can be formed in our programs by showing a heirarchy of abstraction. We will be building points, to build lines which will help us to build rectangles. 

>[!question] Cues
> #data-abstraction 
> #SICP/Chapter2 
> Related to: [[Data Abstraction]]

>[!note]  Notes
>#### Abstraction Layer 1 - `Point`
>In the beginning there was the point (x,y)... as described by the data structure of a pair. Pairs are created using the label `cons` in our Scheme language
>```Scheme 
>(define (make-point a b)
>(cons a b))
>```
>#### Abstraction Layer 2 -`Line`
>Once we make a point, we can then make a line segment defined as a pair of two points (a point which is also a pair as defined in `make-point`)
>```Scheme
>(define (make-segment a b c d)
 (cons (make-point a b) (make-point c d))) 
 
 
 Once we have the procedure to construct line segments we can create other operations on such constructions like calculating the starting point, midpoint, and endpoint of a line segment. The midpoint procedure calculates the average of the x and y values of the starting and ending points of the line-segment. The start-segment and end-segment procedure can be easily be defined as the first and second element of the make-segment pair (similar to x-point and y-point for make-point procedures)
>  ```Scheme
> (define (start-segment l)
   (car l))
(define (end-segment l)
   (cdr l))
(define (midpoint-segment l)
  (cons (average (x-point (start-segment l)) (x-point (end-segment l)))
  (average (y-point (start-segment l)) (y-point (end-segment l))))
(define(average a b)
(/ (+ a b) 2)

>[!notes] ### Note 2
>### Abstraction Layer 3 - `Rectangle`
>A rectangle can be defined with two lines in a plane (the length and width). For our purposes, we are only constructing rectangles parallel to the x-y plane. Our rectangle will take in 4 arguments which will specify the starting position, length and width of the rectangle.
>```Scheme
>(define (make-rectangle a b c d)
>(cons (make-segment a c b c) (make-segment a d b d)))
>``` 
>Thus the rectangle will be a pair of two line segments (which are a pair of two-points (**see** Abstraction 2 - `makesegment`) which are also a pair of x and y values (*see* abstraction 1 - `makepoint`)).  The arguments will be the x and y values of the rectangle - (x1, x2, y1, y2). 
>The first element of the pair will signify the bottom horizontal line of the rectangle (from x1 to x2 on y1 axis). The second pair will signify the upper horizontal line of the rectangle (from x1 to x2 on y2 axis)
>e.g. 
>```Scheme
(make-rectangle 0 1 0 1)
(((0 . 0) 1 . 0) (0 . 1) 1 . 1)
>```
> We can create operations on this layer to calculate area and perimeter of a rectangle. The area will be a product of the length (difference between the x values of the starting and ending segment) and the y-values (difference between the y-values of the first second line and the first line)
> ```Scheme
>  (define (area-rectangle a)
 ( * (- (x-point (end-segment (cdr a)))
(x-point (start-segment (car a))))
(-  (y-point (end-segment (cdr a)))
  (y-point (start-segment (car a))))))

>For the perimeter we will use the formula P = 2(l + h).  For l (length), is the difference between the length of the  x values of the end and starting point. 
```Scheme

(define (perimeter-rectangle a)
    (* 2
       (+ (-  (x-point (end-segment (cdr a)))
              (x-point (start-segment (car a))))
            
          (-  (y-point (end-segment (cdr a)))
              (y-point (start-segment (car a)))))))
```
> We can also define a rectangle as parallel vertical lines separated by a distance 
> ```Scheme
> (define (make-rectangle x1 x2 y1  y2)
> (cons (make-segment x1 y1 x1, y2)
> (make-segment x2 y1 x2 y2))
> ```
