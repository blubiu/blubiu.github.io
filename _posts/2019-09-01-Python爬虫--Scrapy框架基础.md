---
layout: post
title: "Python爬虫--Scrapy框架基础"
date: 2019-09-01
description: "Python 爬虫"
tag: Python 爬虫
---
---

### 前言：

前面一章讲了 Scrapy 安装 ，<br>

现在总结一下 Scrapy框架基本使用 <br>

---


### 目录：

* <a href="#a" target="_self">指令介绍</a>
* <a href="#b" target="_self">目录结构</a>
* <a href="#c" target="_self">爬虫工作流程</a>
* <a href="#d" target="_self">项目指令</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">指令介绍：</span>

打开 cmd 窗口 输入 `scrapy -h` 即可查看指令 <br>

![images](/images/2019-09-01/01.png)

-----

| 指令 | 功能 |
| --- | --- |
| bench | 项目指令，一般在项目里面运行的指令 |
| fetch | 获取某个网页的信息，使用此指令可以网页到本地 |
| genspider | 创建爬虫文件，而不是爬虫项目 |
| runspider | 运行爬虫 |
| settings | 查看爬虫对应的配置信息 |
| shell | 可以启动爬虫的交互终端，进入一个交互式窗口 |
| startproject |  创建一个爬虫项目 |
| version | 查看爬虫的版本信息 |
| view | 可以实现下载某个网页并用浏览器查看功能 |

其他的就不多介绍了。 <br>

-----


### <span id = "b">目录结构：</span>

下面来了解一下爬虫的目录结构 <br>

假设我们在 **D 盘** 下的 **scrapy** 目录下创建一个爬虫项目 ，名字叫 **demo** 吧 <br>

这里我们需要使用命令 **startproject** 来创建 <br>

命令： <br>

```python
scrapy startproject demo
```

这样就创建好了。 <br>

![images](/images/2019-09-01/02.png)

-----

打开 **demo** 后，里面有两个文件， <br>

一个是爬虫核心目录文件， <br>

另外一个是爬虫配置文件。 <br>

![images](/images/2019-09-03/03.png)

-----

接下来看看 核心目录 <br>

`__pycache__` 是缓存目录 <br>

spiders 文件夹放的是爬虫文件，一个爬虫项目里面可以有多个文件 <br>

`__init__.py` 是初始化文件 <br>

**items.py** 是定义爬取目标，如何去爬取的文件 <br>

**middlewares.py** 是中间件文件，比如爬取一个目标，中间要经过什么，使用代理或者其他的，都在这个文件里设置 <br>

**pipelines.py** 是爬后数据处理文件，爬取数据后怎样的一个处理方式就是这个文件来工作 <br>

**settings.py** 是爬虫设置文件，假如不想遵守 **robots** 文件协议，可以在这里面设置 <br>

![images](/images/2019-09-03/04.png)

-----


### <span id = "c">爬虫工作流程：</span>

首先定义一个爬取目录 **item** ，<br>

然后由爬虫文件 **spiders** 向这些目标发起请求 ，<br>

**Scrapy Engine** 意思是爬虫工作引擎 <br>

**Scheduler** 是任务队列 <br>

接到任务后，就去 **intemet** 上爬取目标 <br>

然后再返回 **spiders** 处理这些信息 <br>

大概就是这么一个流程 <br>

如果中间需要走什么代理，那么 **middlewares** 就可以了 <br>

![images](/images/2019-09-01/05.png)

-----

这里的话就是一些简单的操作了 <br>

主要是查看一些信息 <br>

![images](/images/2019-09-01/06.png)

-----


### <span id = "d">项目指令：</span>

项目指令就是在爬虫项目里面才能使用的指令 <br>

首先我们进到爬虫项目里面 <br>

然后输入命令 <br>

```python
scrapy -h
```

然后你就会发现多出来几个指令 <br>

**check** ， **crawl** ，**edit** ， **list** <br>

![images](/images/2019-09-01/07.png)

-----

**check** 检查爬虫文件是否合规 <br>

**crawl** 运行某个爬虫文件 <br>

**edit** 编辑某个爬虫文件 <br>

**list** 展示当前爬虫项目下，那些可以使用的爬虫文件 <br>

**fetch** 获取某个网页的信息 <br>

不过这个指令不是项目指令 <br>

-----

**fetch** 使用方法： <br>

```python
scrapy fetch https://www.baidu.com/  # 比如要获取百度网页信息
```

![images](/images/2019-09-01/07.png)

-----

**shell** 使用方法： <br>

```python
scrapy shell https://www.baidu.com/  # 使用交互方式爬取百度网页信息
```

爬取完后就进入了交互式页面 。 <br>

![images](/images/2019-09-01/08.png)

-----


### <span id = "zg">总结：</span>

基础就先这样吧！！ 

--------
