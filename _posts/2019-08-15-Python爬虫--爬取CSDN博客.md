---
layout: post
title: "Python爬虫--爬取CSDN博客"
date: 2019-08-15
description: "Python 爬虫"
tag: Python 爬虫
---
---

### 前言：

爬取 csdn 博客

---


### 目录：

* <a href="#a" target="_self">爬取csdn博客</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">爬取csdn博客：</span>

直接来吧，简单粗暴， <br>

假设我们要爬取 python 专栏的文章， <br>

我们首先要查看他链接的规律，先抓取他的链接， <br>

查看源代码搜索第一条内容，看看他在哪里。 <br>

![images](/images/2019-08-15/01.png) <br>

![images](/images/2019-08-15/02.png)

-----

我们知道他的链接在这个位置 `{"mod":"popu_459","dest":"` <br>

我们查找一下其他的标题，发现链接依旧在这个位置 <br>

那么我们就可以根据这个规律来抓取链接了 <br>

跟之前的方法一样， <br>

首先使用 **urllib.request.urlopen()** 函数来打开链接，<br>

然后再通过正则表达式去抓取链接 <br>

代码：<br>

```python
import urllib.request
import re

url = "https://blog.csdn.net/nav/python"

data = urllib.request.urlopen().read().decode("utf-8","ignore")

path = '{"mod":"popu_459","dest":"(.*?)",'

All_link = re.compile(path).findall(data)

for i in range(0,len(All_link)):
	this_link = All_link[i]
	print(this_link)
```

运行后就是这个样子 <br>

![images](/images/2019-08-15/03.png)

-----

我们也可以将这些文章保存到本地，<br>

使用 **urllib.request.urlretrieve()** 方法 <br>

代码： <br>

```python
import urllib.request
import re

url = "https://blog.csdn.net/nav/python"

data = urllib.request.urlopen(url).read().decode("utf-8","ignore")

path = '{"mod":"popu_459","dest":"(.*?)",'

All_link = re.compile(path).findall(data)

for i in range(0,len(All_link)):
	this_link = All_link[i]
	urllib.request.urlretrieve("D:/link/"+str(i)+".html")
```

运行后就成功将文章抓取到本地 **D 盘** 下的 **link** 文件夹下面 <br>

记得先创建 **link** 文件夹 ，不然会报错 <br>

![images](/images/2019-08-15/04.png)

-----


### <span id = "zg">总结：</span>

先这样吧！！！

--------
