---
title: 基础算法——阶乘和
layout: mypost
categories: [oi,cpp,code]
---

如题，今天记录一下计算阶乘和的程序（O(n^2)）和改进版（O(n)）。

# O(n<sup>2</sup>) 的暴力程序

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int n = 20,sum,fact;
    for (int i = n; i >= 1; i--)
    {
        fact = 1;
        for (int j = i; j >= 1; j--)
            fact *= j;
        sum += fact;
    }
    cout << sum;
    return 0;
}
```

这个其实没什么好说的，两层for所以是O(n<sup>2</sup>)。



# O(n)的优化解

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int n = 20, prod = 1, sum = 0;
    for (int i = 1; i <= n; i++)
    {
        prod *= i;
        sum += prod;
    }
    cout << sum;
    return 0;
}
```

我们不难可以发现阶乘之和实际上是前面一个阶乘乘上这个数加一~~（怎么感觉说的比代码还麻烦啊（~~所以可以用一个变量prod（product）来储存这个乘积，这样就可以达到O(n)了。



**当然，数据过大（毕竟阶乘），会出现不可预料的bug，即使long long也存在，不做记载了，题目也不会这么变态的（**