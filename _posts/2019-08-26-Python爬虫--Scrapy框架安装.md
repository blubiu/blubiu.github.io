---
layout: post
title: "Python爬虫--Scrapy框架安装"
date: 2019-08-26
description: "Python 爬虫"
tag: Python 爬虫
---
---

### 前言：

Scrapy框架安装 ，<br>

**Scrapy** 是 **Python** 领域专业的爬虫开发框架，已经完成爬虫程序的大部分通用工具 <br>

它使用了 **Twisted** 异步网络库来处理网络通讯。整体架构大致如下 <br>

![images](/images/2019-08-26/01.png)

---


### 目录：

* <a href="#a" target="_self">第一步:挂小灰机或者将要安装的文件下载到本地</a>
* <a href="#b" target="_self">第二步:升级pip</a>
* <a href="#c" target="_self">第三步:安装wheel</a>
* <a href="#d" target="_self">第四步:安装lxml</a>
* <a href="#e" target="_self">第五步:安装Twisted</a>
* <a href="#f" target="_self">第六步:安装Scrapy</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">第一步：挂小灰机或者将要安装的文件下载到本地</span>

Scrapy 框架安装踩坑中 <br>

为什么要挂小灰机呢？？ <br>

因为有些扩展包需要科学上网才能下载，不挂的话会出错 <br>

如果确实挂不了的话，可以考虑才其他地方下载安装包到本地，<br>

然后在本地进行安装。 <br>

-----


### <span id = "b">第二步：升级pip</span>

**pip** 是一个现代的，通用的 **Python** 包管理工具。提供了对 **Python** 包的查找、下载、安装、卸载的功能。 <br>

在安装扩展包的时候，可会因为 **pip** 版本过低安装不了 <br>

例如出现如下错误 <br>

![images](/images/2019-08-26/02.png)

-----

这个时候我们可以考虑先升级 **pip** ，然后再安装扩展包 <br>

升级命令： <br>

```python
python -m pip install --upgrade pip
```

这样就成功升级了 <br>

![images](/images/2019-08-26/03.png)

-----


### <span id = "c">第三步：安装wheel</span>

Python的第一个主流打包格式是 **.egg** 文件，<br>

现在大家庭中又有了一个叫做 **Wheel(`*.whl`)** 的新成员。 <br>

wheel 被设计成包含PEP 376兼容安装（一种非常接近于磁盘上的格式）的所有文件。 <br>

你可以这么理解，**source**是源代码，如果包含**C++**的化需要编译，<br>

而 **wheel** 是编译后的，可以直接安装。 **pip** 默认的也是先下载 **wheel** 文件安装，没有的话再源码编译安装 <br>

-----

安装 **wheel** 的话，我们采用网络安装，不需要挂小灰机 <br>

出现这个就表示已经安装好了 <br>

![images](/images/2019-08-26/04.png)

-----


### <span id = "d">第四步：安装lxml</span>

**lxml** 是 **python** 的一个解析库，支持 **HTML** 和 **XML** 的解析，支持 **XPath** 解析方式，而且解析效率非常高 <br>

**XPath**，全称 **XML Path Language**，即 **XML** 路径语言，它是一门在 **XML** 文档中查找信息的语言，<br>

它最初是用来搜寻 **XML** 文档的，但是它同样适用于 **HTML** 文档的搜索 <br>

-----

现在来安装 **lxml** ，我们采用下载安装，就是将安装包下载到本地进行安装 <br>

打开这个网站：`https://www.lfd.uci.edu/~gohlke/pythonlibs/` <br>

然后找到 **lxml** 下载 <br>

这里 **cp37** 表示 **python** 版本 ，**win_amd64** 表示 **Windows** 位数是 **64** 位的 <br>

下载对应的版本就好了 <br>

![images](/images/2019-08-26/05.png)

-----

然后下载到了 **D 盘** ，**Python37 文件夹**下了 <br>

然后进入这个文件夹下安装即可 <br>

命令： <br>

```python
pip install lxml-4.4.1-cp37-cp37m-win_amd64.whl  #  pip install 文件全名
```

这样就安装成功了 <br>

![images](/images/2019-08-26/06.png)

-----


### <span id = "e">第五步：安装Twisted</span>

Twisted 介绍： <br>

```
Twisted 是用 Python 实现的基于事件驱动的网络引擎框架。 Twisted 诞生于2000年初，

在当时的网络游戏开发者看来，无论他们使用哪种语言，手中都鲜有可兼顾扩展性及跨平台的网络库。

Twisted 的作者试图在当时现有的环境下开发游戏，这一步走的非常艰难，

他们迫切地需要一个可扩展性高、基于事件驱动、跨平台的网络开发框架，

为此他们决定自己实现一个，并从那些之前的游戏和网络应用程序的开发者中学习，汲取他们的经验教训。

Twisted 支持许多常见的传输及应用层协议，

包括 TCP 、 UDP 、 SSL/TLS 、HTTP 、IMAP 、SSH 、IRC 以及 FTP 。

就像python一样，Twisted 也具有“内置电池”（batteries-included）的特点。

Twisted对于其支持的所有协议都带有客户端和服务器实现，

同时附带有基于命令行的工具，使得配置和部署产品级的 Twisted 应用变得非常方便。
```

-----

安装 **Twisted** ，我们也使用本地安装的方法 <br>

还是这个网站：`https://www.lfd.uci.edu/~gohlke/pythonlibs/` <br>

还是跟之前一样，找到对应的版本下载 <br>

然后安装 <br>

这样就安装成功了，如果这样都安装不了的话，建议挂个小灰机再安装 <br>

![images](/images/2019-08-26/07.png)

-----


### <span id = "f">第六步：安装Scrapy</span>

前面的准备工作完成了 <br>

最后一步就是安装 **Scrapy** 了 <br>

这一步无需挂小灰机，如果确实怕出错，挂上也无所谓 <br>

命令：<br>

```python
pip install scrapy
```

出现这个就表示成功安装了 <br>

![images](/images/2019-08-26/08.png)

-----

如果不确定是否安装成功，可以输入 scrapy <br>

如果能够显示出信息，就说明成功了 <br>

![images](/images/2019-08-26/09.png)

-----


### <span id = "zg">总结：</span>

到这里 Scrapy 就安装结束了 <br>

接下来开启新的爬虫之旅了！！

--------
