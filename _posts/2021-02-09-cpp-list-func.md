---
title: 数组在函数中的传入传出
categories: [oi,cpp]
layout: mypost
---

今天最后一次唠叨一下这事儿。

````cpp
#include <bits/stdc++.h>

using namespace std;

int *arrDouble(int arr[], int l)
{
	int *p;
	p = new int[l];
	for(int i=0; i<l; i++)
		p[i] = 2*arr[i];
	return p;
}

int main()
{
	int a[] = {1,2,3,4,5};
	int *p =  arrDouble(a,5);
	for(int i=0; i<5; i++)
		cout << p[i] << ' ';
	return 0;
}

````



本质上就是指针的传入传出，我们其实不妨把```int*```理解为一种数据类型（虽然因为语法原因，码风上选择把```*```和变量名写在一起）进而再深入一下，```p[n]```就可以理解为```*p + n个内存地址```的语法糖，这样再来看上述程序，就会觉得“接口”十分顺滑。