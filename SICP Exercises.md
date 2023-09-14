
```Scheme
(define (sum-integers a b)
  (if (> a b) 
      0 
      (+ a (sum-integers (+ a 1) b))))
      ```
      
```Scheme
> (sum-integers 3 5)
12
```

```Scheme
> (define (sum-cubes a b)
  (if (> a b) 
      0 
      (+ (cube a) 
         (sum-cubes (+ a 1) b))))
> (define (cube x) (* x x x))
> (define (simpsons f a b n)
    (define h (/ (- b a) n))
    (define (yk k)(f (+ a (* k h))))
    (define simpson-term k)
    (* (cond((or (= k 0) (= k n)) 1)
                ((odd? k) 4)
                (else 2))
       (yk k)))
>  (define (simpsons f a b n)
    (define h (/ (- b a) n))
    (define (yk k)(f (+ a (* k h))))
    (define (simpson-term k)
    (* (cond((or (= k 0) (= k n)) 1)
                ((odd? k) 4)
                (else 2))
       (yk k)))
     (* (/ h 3) (sum simpson-term 0 inc n)))
>  (define (sum term a next b) 
   (if (> a b) 
       0 
       (+ (term a) 
          (sum term (next a) next b)))) 
  
> (define (inc n) (+ n 1)) 
>  (define (cube x) (* x x x)) 
> (define (odd? x) (= (remainder x 2) 1))
>  (simpson-integral cube 0 1 100) 
. . simpson-integral: undefined;
 cannot reference an identifier before its definition
> (simpsons cube 0 1 100)
1/4
>  (simpsons cube 0 1 1000) 
1/4
> (define (product term a next b)
    (if (> a b)
        1
        (* (term a)
           (product term (next a) next b))))
> (define (identity x) x)
> (define (factorial n)
    (product identity 1 inc n))
> (factorial 7)
5040
> (factorial 6)
720
> (define (pi-product n)
    (define (multiply-2 k) (* k (+ k 2)))
    (define (square-inverted x) (/ 1 (* x x)))
    (define (add-2 x) (+ x 2))
    (* (product multiply-2 2 add-2 n)
       (product square-inverted 3 add-2 n) 4))
> (pi-product 1000)
3149450 6055796165280906305504915102776769106691030293366206569979103045505529953500461374792668268973037575153365170426141796716376123013061755944288584590187780744710946916245966158585903422119196486353387260792213385396393489020910889819791494279633301918535278276352711148908858724120689201632317473038017590771727264164839884521522617425339445097164936636691851880724033763231209154487814157250070395262498062648751782520169100307787527025175378828166554981000430263322197300040066509866581120837855313919125024207611736064979501664686432133601601176564880555930615250958137018448500354118838974/35600543636057169696679201701120164941628016448449363319131349454361298308774138329582316965796582402859440086653526484093301527138281202796617715700222303877848000544149647459780748162710869104306569451919100952136455874779306582341809510692707820148410037360825601687325990550852622255333775338773573154394441625824468111745682323615269697187127600219487072750379251476792895691447026928883283086644196385665236522511990089293010649362334566065092022947257467380252643362599656784732495410234563166780465566284298283645610200751948737412859527983011859081111210739633366599006144228338052525
> (define (product-2 term a next b)
    (define (iter a result)
      (if (> a b)
          result
          (iter (next a) (* result (term a)))))
    (iter a 1))
> ```
> 