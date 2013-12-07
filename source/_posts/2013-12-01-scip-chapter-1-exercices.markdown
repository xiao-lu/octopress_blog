---
layout: post
title: "SCIP Chapter 1 习题"
date: 2013-12-01 18:07:59 +0100
comments: true
categories: 
---

这个系列是我自己读SCIP后做的练习答案，答案仅供参考。

* Exercice 1.1 求出表达式的值

```scheme
10   							; 10
(+ 5 3 4)						; 12
(- 9 1)							; 8
(/ 6 2)							; 3
(+ (* 2 4) (- 4 6))				; 6
(define a 3)					; 定义 a = 3
(define b (+ a 1))				; 定义 b = a + 1
(+ a b (* a b))					; 3+4+3*4 = 19
(= a b)							; #f
(if (and (> b a) (< b (* a b))) ; 4
b a)							
(cond ((= a 4) 6)				; 16
      ((= b 4) (+ 6 7 a))
      (else 25))
(+ 2 (if (> b a) b a))			; 6
(* (cond ((> a b) a)			; 16
         ((< a b) b)
         (else -1))
   (+ a 1))
```
<!-- more -->
* Exercice 1.2 

```scheme
(/ (+ 5 4 (- 2 
			 (- 3
			 	(+ 6 
			 	   (/ 4 5))))) 
   (* 3 
   	  (- 6 2) 
   	  (- 2 7)))
```

* Exercice 1.3 定义一个过程，3个参数，返回较大两个数的和

```scheme
(define (sum_max a b c)
  (cond ((and (> a c) (> b c)) 
  			(+ a b))
        ((and (> a b) (> c b)) 
        	(+ a c))
    	(else (+ b c))))
```

* Exercice 1.5 

**正则序求值** 完全展开后规约
**应用序求值** 先求值参数后应用

题中关键是 `(define (p) (p))` 这是个无限循环

检验的思路是构造一个函数，传给他一个无限循环的参数，但这个参数不会被用到，这个函数就能顺利执行完毕。如果是正则序求值，那么就能执行完函数，而如果是应用序求值，那么就会在参数求值期间无限循环。

* Exercice 1.6

mit-scheme 是应用序求值解释器。但是if语句不完全是这样。if语句只会求值符合条件的分支。 `new-if` 是一个函数，所以它和if语句的差别在于它会将参数的值都求出来后再执行函数。


To be continued...
--

