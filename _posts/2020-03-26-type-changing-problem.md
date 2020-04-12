---
layout: post
title: "C++类型转换时的一个坑"
date: 2020-03-09 21:00:30 +0800
categories: code
tags: code c++
img: https://i.loli.net/2020/03/08/8IoqnF4EceCP9A2.jpg
describe: 还是py好啊（棒读
themecolor: "#fff"
themetextcolor: "#000"
---

记录下c++中类型转换时遇到的一个坑。

本来是刷洛谷的时候遇到的，这里就不放题目的源码了。

看下面的代码。

````cpp
#include <bits/stdc++.h>

int main()
{
    using namespace std;
    cout << double(3/2) 
         << endl
         << (double) 3/2;
    return 0;
}
````

按照本来的设想，应该都是输出1.5的。

~~就像````float(3/2) ````in Python一样自然而美丽~~

然而第一个输出为1 --> ~~WA（sad~~，第二个才输出1.5。

其实到这里很容易就可以分析出来了，````type(exp)````先计算exp再强制转换为type，而````(type) exp````则先将exp中的量转换为type再计算。

# 然而问题就在于C艹 Primer Plus只提到了这两种都是强制类型转换机制的格式

# 然后谷歌‘double() (double)’谷歌娘会无视括号

# **fuck.**

~~哦天哪我写了一篇关于代码的博客~~

