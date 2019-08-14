---
layout: post
title: "Python爬虫--Urllib基础"
date: 2019-08-03
description: "Python 爬虫"
tag: Python 爬虫
---
---

### 前言：

Python Urllib基础 <br>

---


### 目录：

* <a href="#a" target="_self">1. urlretrieve</a>
* <a href="#b" target="_self">2. urlcleanup</a>
* <a href="#c" target="_self">3. info()</a>
* <a href="#d" target="_self">4. getcode()</a>
* <a href="#e" target="_self">5. geturl()</a>
* <a href="#f" target="_self">6. 超时设置</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">1. urlretrieve</span>

**Urllib** 库也是类似 **request** 库，用来解析html的 <br>

首先讲 **urlretrieve** 子模块 <br>

这个模块的作用是将网页下载到本地 <br>

语法： urlretrieve(网址,本地地址) <br>

例如： <br>

这样就可以了，他会将百度网页下载到本地D盘下，<br>

不过图片那些可能下载不到，因为他做了防盗取 <br>

```python
import urllib.request

url = 'https://www.baidu.com/'

urllib.request.urlretrieve(url,'D:/')
```

-----


### <span id = "b">2. urlcleanup</span>

urlcleanup 用来清除爬虫产生的一些缓存及其他一些杂七杂八的东西 <br>

他通常在请求网页的时候使用，<br>

运行时不会有任何提示 <br>

例： <br>

```python
import urllib.request

url = 'https://www.baidu.com/'

urllib.request.urlretrieve(url,'D:/')

urllib.request.urlcleanup()
```

-----


### <span id = "c">3. info()</span>

**info()** 用来获取网页的简介信息 <br>

例： <br>

```python
import urllib.request

url = 'https://www.baidu.com/'

data = urllib.request.urlopen(url)

urllib.request.urlcleanup()

print(data.info())
```

效果图： <br>

![images](/images/2019-07-28/01.png)

-----


### <span id = "d">4. getcode()</span>

**getcode()** 获取状态码 <br>

```python
import urllib.request

url = 'https://www.baidu.com/'

data = urllib.request.urlopen(url)

urllib.request.urlcleanup()

print(data.getcode())

>>> 输出 200
```

-----


### <span id = "e">5. geturl()</span>

**geturl()** 获取当前访问网页的url地址 <br>

例：

```python
import urllib.request

url = 'https://www.baidu.com/'

data = urllib.request.urlopen(url)

urllib.request.urlcleanup()

print(data.geturl())

>>> 输出 https://www.baidu.com/
```

-----


### <span id = "f">6. 超时设置</span>

在我们访问网页的时候，可能会因为各种原因导致访问不成功， <br>

这个原因可能是对方服务器反应慢，或者网速慢之类的问题， <br>

那么我们就需要给代码更多的判断时间，<br>

如果超过这个时间，那么我们就可以认为网页无法访问。 <br>

这里我们使用到 **timeout()** 函数来设置请求时间 <br>

它通常会配合 **try except** 函数一起使用 <br>

**例：** <br>

设置超时时间为 **5秒**， <br>

**len()** 函数为获取返回长度，<br>

**decode()** 是解码的意思，有些时候因为编码不同，不解码的话会出错，<br>

第二个参数 `ignore` ，表示解码失败也强行解码 <br>

```python
import urllib.request

try:

	url = 'https://www.baidu.com/'

	data = urllib.request.urlopen(url,timeout=5)

	urllib.request.urlcleanup() # 清除缓存

	print(len(data.read().decode("utf-8","ignore")))

except Exception as error:
	print("无法访问 " + str(error))

>>> 输出 227
```

-----


### <span id = "zg">总结：</span>

Urllib基础，有些时候没有 request模块方便 <br>

--------
