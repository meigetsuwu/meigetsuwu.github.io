---
title: 基础算法——选择、冒泡、桶排序
categories: [oi,scheme,code]
layout: mypost
---

# 选择排序

选择排序为复杂度O(n**2)的最基础的排序算法，思路为每次从已有列表中选择其中最值加入新列表并将该最值pop出该列表，如此循环列表长度次；而其中每次寻找最值又占用一轮循环，故此算法嵌套了两层循环。

```scheme
(define (my-sort li)
    (my-sort-qwq '() li))

(define (my-sort-qwq l1 l2)
    (if (null? l2)
        l1
        (my-sort-qwq (cons (greatest l2) l1) (pop l2 (greatest l2)))))

(define (greatest li)
    (greatest-qwq (cdr li) (car li)))
(define (greatest-qwq li n)
    (if (null? li) 
        n
        (if (< n (car li))
            (greatest-qwq (cdr li) (car li))
            (greatest-qwq (cdr li) n))))

(define (pop li n)
    (pop-qwq '() li n))
(define (pop-qwq l1 l2 n)
    (if (null? l2)
        l1
        (if (equal? (car l2) n)
            (pop-qwq l1 (cdr l2) n)
            (pop-qwq (cons (car l2) l1) (cdr l2) n))))
```

# 冒泡排序

冒泡排序（未优化）的时间复杂度同样为O(n**2)，思路为将列表遍历一遍，若l[n]>l[n+1]（从小到大排列）则调换两元素；由此列表中最大的元素“冒泡”到了最末——而在此之上进行再一次的冒泡，将列表倒数第二大的元素“冒泡”到列表第二末——如此循环。

优化的冒泡排序本篇先不做讨论。

```scheme
(define (my-sort li)
    (vector->list (my-sort-qaq (list->vector li) 0)))
(define (my-sort-qaq ve n)
    (if (equal? n (- (vector-length ve) 1))
        ve
        (my-sort-qaq (my-sort-qwq ve 0) (+ 1 n))))
(define (my-sort-qwq ve n)
    (if (equal? n (- (vector-length ve) 1))
        ve
        (if (greater? ve n)
            (my-sort-qwq (exchange ve n) (+ 1 n))
            (my-sort-qwq ve (+ 1 n)))))

(define (exchange ve n)
    ; set and return ve' which
    ; ve[n]=ve'[n+1]&&ve[n+1]=ve'[n]
    (let ((a (vector-ref ve n)) (b (vector-ref ve (+ 1 n))))
        (vector-set! ve n b)
        (vector-set! ve (+ 1 n) a)
        ve))

(define (greater? ve n)
    ; #t if ve[n]>ve[n+1] otherwise #f
    (let ((a (vector-ref ve n))(b (vector-ref ve (+ 1 n))))
        (> a b)))
```

# 桶排序

桶排序时间复杂度O(n)（O(2n)），适用于待排序元素均来自一已知集合的情况；思路为生成指定多个“桶”，记为li，扫描待排序的列表，将值为n的元素放入li[n]中（假设该集合第一个数为0，视具体情况调整）；再进行取出的操作，将li的第n项打印li[n]遍即可（假设同上）。

建议将每个桶的初始值设为0。

```scheme
; 数据范围 0 <= n <= 1000
(define (my-sort li)
    (output '() (vector->list (fill li)) 0))

(define (fill li)
    (fill-qwq li (make-vector 1001 0)))

(define (fill-qwq li ve)
    (if (null? li)
        ve
        (fill-qwq (cdr li) (++ ve (car li)))))

(define (output l1 l2 n)
    (if (null? l2)
        l1
        (output (append l1 (output-qwq '() n (car l2))) (cdr l2) (+ 1 n))))

(define (output-qwq li n m)
    (if (zero? m)
        li
        (output-qwq (append li (cons n '())) n (- m 1))))

(define (++ ve n)
    (vector-set! ve n (+ 1 (vector-ref ve n)))
    ve)
```