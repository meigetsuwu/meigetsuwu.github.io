---
title: 基础算法——递归与尾递归
layout: mypost
categories: [oi,scheme,code]
---

由于scheme标准对尾递归有所优化，因此我们大多数情况下在scheme中以（尾）递归代替```while```，```for```之类。

来看几个例子。

# 0 数列求和

## 递归解法

````scheme
(define (recsum li)
    (if (null? (cdr li))
        (car li)
        (+ (car li) (recsum (cdr li)))))
````

;为了叙述方便，我们这里把数列记为```'(1 2 3 4)```

所以这个算法的过程大约可以表示如下：

```scheme
(+ (recsum (1 2 3 4)))
(+ (+ 1 (recsum (2 3 4))))
(+ (+ 1 (+ 2 (recsum (3 4)))))
(+ (+ 1 (+ 2 (+ 3 (recsum (4))))))
(+ (+ 1 (+ 2 (+ 3 (+ 4)))))
(+ (+ 1 (+ 2 (+ 3 4))))
(+ (+ 1 (+ 2 7)))
(+ (+ 1 9))
(+ 10)
```

看着每行最右侧描成的的折线，我们很容易明白“递归”是什么意思——逐渐“递”到最深的栈，再“归”回最初的一层。而普通递归的弊端也显而易见，有极大的空间复杂度而会爆栈~~（MLE，噔 噔 咚）醒醒scheme不能oi~~。

因此我们提出了尾递归的概念。

## 尾递归解法

```scheme
(define (recsum-tail li)
  (recsum-tail-qwq li 0))
(define (recsum-tail-qwq li i)		;不要注意后缀（
  (if (null? li)
      i
      (recsum-tail-qwq (cdr li) (+ (car li) i))))
```

同上，表示算法过程为：

```scheme
(recsum-tail-qwq (1 2 3 4) (+ 0))
(recsum-tail-qwq (2 3 4) (+ 1 0))
(recsum-tail-qwq (3 4) (+ 1 2 0))
(recsum-tail-qwq (4) (+ 1 2 3 0))
(recsum-tail-qwq ('()) (+ 1 2 3 4 0))
```

**也就是说我们实际上是在相当于一遍又一遍地改变着传入```recsum-tail-qwq```的参数，而这些都是在“第一层”栈里完成的，空间复杂度O(1)**~~上一节没写具体空间复杂度是因为我不会算求dalao~~

而从写法来看，即是**返回值中递归的函数“在最高层”。**

那我们再随便看几个尾递归算法。



# 1 统计表中元素个数

```scheme
(define (my-length li)			;length为内置函数
  (my-length-qwq li 0))
(define (my-length-qwq li n)
  (if (null? li)
      n
      (my-length-qwq (cdr li) (+ n 1))))
;在typora上写的，不确定括号数量对（
```

大同小异。



# 2 返回删除某元素后的新表

```scheme
(define (my-remove li n)		;remove为内置函数
  (my-remove-qwq '() li n))
(define (my-remove-qwq l1 l2 n)
    (if (null? l2)
        l1
        (if (equal? (car l2) n)
            (my-remove-qwq l1 (cdr l2) n)
            (my-remove-qwq (cons (car l2) l1) (cdr l2) n))))
```

注意这个```my-remove-qwq```返回的是倒序，需要用下一节中的函数倒序处理（需要的话）。



# 3 表倒序

```scheme
(define (my-reverse li)
  (my-reverse-qwq '() li))
(define (my-reverse-qwq l1 l2)
  (if (null? l2)
    l1
    (my-reverse-qwq (cons (car l2) l1) (cdr l2))))
```





(完)