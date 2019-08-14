---
layout: post
title: "Python爬虫--模拟HTTP请求"
date: 2019-08-04
description: "Python 爬虫"
tag: Python 爬虫
---
---

### 前言：

GET 和 POST <br>

---


### 目录：

* <a href="#a" target="_self">GET请求</a>
* <a href="#b" target="_self">POST请求</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">GET请求：抓取百度搜索标题</span>

使用 **Urllib** 库来模拟浏览器发送GET请求， <br>

这跟 **request** 模块差不多， <br>

同时用一个例子来学习它。 <br>

-----

我们来抓取百度搜索的标题 <br>

假设我们搜索 **Python** <br>

那么在 **url** 上应该是这样的格式 `https://www.baidu.com/s?wd=python` <br>

`s?wd=` 后面跟要搜索的内容 <br>

首先模拟 **HTTP** 请求 <br>

```python
import urllib.request

keyword = "python"

url = "https://www.baidu.com/s?wd="+keyword

data = urllib.request.urlopen(url).read().decode("utf-8")

print(data)  #  打印内容
```

这样一个简单的 GET 请求就完成了

-----

接下来就是抓取搜索标题， <br>

也就是这个东西，<br>

![images](/images/2019-08-04/01.png) 

-----

我们查看源代码看看有什么规律，然后写正则 <br>

搜索 `Welcome to Python.org` 发现他在 **title** 里面 <br>

查看其他的标题，还是在这个标签里面 <br>

那么我们就可以根据这个规律写正则表达式了 <br>

```python
import urllib.request
import re

keyword = "python"

url = 'https://www.baidu.com/s?wd='+keyword

data = urllib.request.urlopen(url).read().decode("utf-8")

path = '"title":"(.*?)",'  # 正则表达式，括号里面就是要提取的内容

resut = re.compile(path).findall(data)

print(resut)
```

运行后发现， <br>

抓是抓到了，但是为啥有 Unicode 编码的字符 <br>

![images](/images/2019-08-04/02.png) 

-----

经过分析，这个编码其实是 广告 标题来的，<br>

![images](/images/2019-08-04/03.png) 

-----

接下来我们就要把广告去掉 <br>

只要判断是 **Unicode** 编码的字符串就 **pass** <br>

```python
import urllib.request
import re

keyword = "python"

url = "https://www.baidu.com/s?wd="+python

data = urllib.request.urlopen(url).read().decode("utf-8")

path = '"title":"(.*?)",'

resut = re.compile(path).findall(data)

for i in resut:
	if (i >= u'\u0041' and i <=u'\u005a') or (i >= u'\u0061' and i<=u'\u007a'):  #  判断是否Unicode编码
 		print(i)
 	else:
 		pass
```

运行后就成功提取到正确的内容 <br>

![images](/images/2019-08-04/04.png) 

-----

这只是提取了一页的内容，<br>

如果要提取多页呢，那还得找规律 <br>

发现，当 `pn=0` 时，就是第一页，<br>

当 `pn=10` 时，就是第二页 <br>

依次加10，那么这个就应该是 `(a-1)*10` <br>

如果我们要获取5页的内容，那么就应该是 `range(1,7)` ， 因为 `a-1` <br>

上代码 <br>

```python
import urllib.request
import re

keyword = "python"

for a in range(1,7):

	url = "https://www.baidu.com/s?wd="+keyword+"&pn={}".format((a-1)*10)

	data = urllib.request.urlopen(url).read().decode("utf-8")

	path = '"title":"(.*?)",'

	resut = re.compile(path).findall(data)

	for i in resut:
		if (i >= u'\u0041' and i <=u'\u005a') or (i >= u'\u0061' and i<=u'\u007a'):
			print(url+' ----> '+i)
		else:
			pass
```

这样我们就成功提取到多页的内容了 <br>

![images](/images/2019-08-04/05.png) 

-----


### <span id = "b">POST请求：模拟登录</span>

模拟登录将使用 VAuditDemo 漏洞平台进行演示 <br>

虚拟域名为：`http://www.vd.com/` <br>

-----

POST请求使用 urllib.parse 这个模块 <br>

这个也跟 request 差不多，只不过模块不同而已 <br>

首先抓个包，然后查看POST参数有那些，还有请求地址 <br>

然后就可以开始写脚本了 <br>

![images](/images/2019-08-04/06.png) 

-----

代码： <br>

```python
import urllib.request
import urllib.parse

url = 'http://www.vd.com/user/logCheck.php'

data = urllib.parse.urlencode({

	"user":"admin",
	"pass":"123456",
	"submit":"login"

	}).encode("utf-8")

headers = {
	
	"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:68.0) Gecko/20100101 Firefox/68.0",
	"Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
	"Accept-Language": "zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2"


}

# 进行POST请求，就需要使用 urllib.request 下面的 Request(地址,数据)
req = urllib.request.Request(url,headers=headers,data=data)

resut = urllib.request.urlopen(req).read().decode("utf-8")

print(resut)
```

这样就可以了，<br>

记住语法就行了。 

-----


### <span id = "zg">总结：</span>

模拟请求就先到这里吧， <br>

--------
