---
layout: mypost
title: vscode配置#include<stdc++.h>
categories: [code,cpp,vsc]
---

在一般情况下，你安装的vscode（算上c++插件）是并不支持```#include<bits/stdc++.h>```这一句的。如果要使用的话，要先去你gcc的安装目录lib里面去找```bits/```文件夹下面的```stdc++.h```的。（我的话直接用everything搜了）。

然后找到vsc的lib目录（默认的话应该是```C:\Program Files (x86)\Windows Kits\10\Include\10.0.17763.0\ucrt\```的，当然10.xxx那一串不确定一样），新建文件夹```bits```，然后把你刚才那个```stdc++.h```ctrlc+v过来就好了。

