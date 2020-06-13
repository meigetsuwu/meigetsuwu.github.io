---
layout: mypost
title: 为你的Jekyll博客部署Mikutap
categories: [code]
---

要说的如题目。话不多说进入正题。

## 0 克隆项目到本地

在bash中cd到自己的博客所在文件夹，然后克隆dalao整理好的内容到/mikutap文件夹。

```bash
git clone git@github.com:HFIProgramming/mikutap.git
```

克隆完了要记得点进去删掉.git目录。

```bash
rm -rf mikutap/.git
```

**另外请在继续下一步前阅读这个repo的[README.md](https://github.com/HFIProgramming/mikutap/blob/master/README.md)了解清楚版权相关内容。**



## 1 自定义

其实也没啥好自定义的，无非是一点提示语。有能力的话可以写写其它的，只要不把原作者内容抹去怎么魔改都是无所谓的。

下面只说说自定义提示语和ABOUT页面的过程。

/mikutap文件夹下的index.html和js/mikutap.min.js里的字符串找着改改就ok了。其中.js文件的格式**很 糟 糕**，建议百度个js格式化工具格式化了再ctrlc，v回去。

> 当然不是所有字符串都可以改==，另外也要注意HTML中一些特殊字符的转义问题。



## 2 ...Enjoy?

然后本地编译

```bash
bundle exec jekyll s
```

访问```127.0.0.1/mikutap/```即可。

**一定要注意不要落下url最后的斜杠，否则是无法访问的。**

然后你把url超链接到博客随便哪里都好啦awww。

> 这里有个偷懒小技巧，如果用相对链接(for exa, /mikutap)超链接引用的话因为_layout机制你还要配置一大堆来新建一个layout，不然直接点击它并不能刷新到Mikutap页面而是你的default layout，所以这里推荐引用绝对链接（逃

（最后别忘了push（（（

<br>

[来看看moi的吧w](https://rain.moimo.me/mikutap/)



## 3 尚未解决的问题

- BACK按钮点击后进入原repo的git页面……其实这个应该是翻翻源码就可以解决的，嘛嘛回头再看吧w

