---
layout: post
title: "简要的记录一下搭博客的过程（使用githubPage+Jekyll）"
date: 2020-03-30 17:30:30 +0800
categories: code
tags: 记录
img: https://i.loli.net/2020/03/08/8IoqnF4EceCP9A2.jpg
describe: 只是记录而已。
themecolor: "#fff"
themetextcolor: "#000"
---

简要记录一下吧，也只是记录一下而已，因为我很难说哪些东西是我选择的方式（主题、github pages，etc.）所特有的。如果翻到了这篇博客，也就看看权当参考吧。凭记忆写，可能有错em。

## 1 fork一个Jekyll仓库并clone

这个网上很多了……gayhub随便找一个点下fork就好。

fork到自己id下之后把repo名改为[userid].github.io，repo页面点settings按钮，就可以看到rename repo name的地方了。

~~自己会写的话当我没说当然你要是会写也没必要来看我这种文章~~

我的话使用的是[jekyll-theme-mdui](https://github.com/KeJunMao/jekyll-theme-mdui)作为主题，然后repo名改成````moi-mo.github.io````。

然后打开git bash，clone下来

> 如果是初次使用git的话还要配置ssh（好像），但是我忘了（，请[google](https://google.com)（

````bash
git clone https://github.com/{userid}/{userid}.github.io.git
````

（其实上面那个链接可以在repo页面点击````clone or download````按钮复制那个链接就ok。）

有需要的话可以先````cd````到需要的目录下。

<br>

## 2 自定义

**！这段包含可能并不通用的内容**

我的话对照着[jekyll-theme-mdui](https://github.com/KeJunMao/jekyll-theme-mdui)的文档改一改各个.yml配置文件就好了，最后要记得改完配置在目录下git bash运行````bundle install````命令安装一下。

想看一下效果的话运行````bundle exec jekyll s````，访问http://127.0.0.1:4000/就可以预览了。

<br>

## 3 上传文章

不论你clone的是什么主题，只要是jekyll，目录下应该会有一个`````_posts`````目录，在里面新建文件名格式为````yyyy-mm-dd-the-words-of-title.md````的文件，在里面写推文就好了。

记得要在推文最前加入如下内容：（部分项目可能仅适用于我）

````yaml
---
layout: post
title: 题目
date: yyyy-mm-dd hh:mm:ss +0800
categories: category
tags: xxx xxx xxx
img: 头图
describe: 描述
---
````

//记得替换为自己的内容o_o

tags之间用空格分开，可以添加多个。

然后打开git bash，切换到博客目录，我们把这边的本地更改提交到github上

````bash
git add .
git commit -m "[COMMIT_MESSAGE]"
git push origin master
````

[COMMIT_MESSAGE]是可以自定义的，然后可能会让你输入github用户名和密码，输入就好了。

另外提一下push上去之后可能要等一会或者要刷新几次页面，毕竟是静态的网站。

<br>

## 4 一个坑

前面提到的category，你每新建一个category，都要在````/category````目录下新建一个````[新的category名].md````文件（名字是上述的新category）。接下来再在新建的.md文件中粘贴以下内容

````yaml
---
layout: category_content
---
````

不然的话直接访问主题中包含的post下面category的超链接是会404的。

比如说我的post中有一个先前尚未出现的category````test````，那我们就要在````/category````目录下新建一个````test.md````文档，并把上述内容粘贴进去。



## 5

***不保证全部适用于一般的Jekyll站点***

