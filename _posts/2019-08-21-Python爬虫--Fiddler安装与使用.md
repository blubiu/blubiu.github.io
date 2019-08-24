---
layout: post
title: "Python爬虫--Fiddler安装与使用"
date: 2019-08-21
description: "Python 爬虫"
tag: Python 爬虫
---
---

### 前言：

为什么要安装 Fiddler ，<br>

是为 Ajax 异步爬虫编写做准备 <br>

---


### 目录：

* <a href="#a" target="_self">Fiddler简介</a>
* <a href="#b" target="_self">Fiddler安装</a>
* <a href="#c" target="_self">Fiddler使用</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">Fiddler简介：</span>

Fiddler 是位于客户端和服务器端之间的代理，也是目前最常用的抓包工具之一 <br>

他就相当于 **burp** ，能够抓包的 <br>

其他的就不多介绍了。 <br>

-----


### <span id = "b">Fiddler安装：</span>

打开官网：`https://www.telerik.com/download/fiddler` <br>

然后输入信息后就可以点击 Download 下载安装包了 <br>

可能要科学上网才能下载，实在不行就去别的下载站下载吧 <br>

不过官网的安全一点 ~ <br>

![images](/images/2019-08-21/01.png)

-----

接下来就是傻瓜安装了 <br>

打开第一步就是要你同意相关协议了 ，照做就是了 <br>

![images](/images/2019-08-21/02.png)

-----

下一步就是安装路径，默认是 **C 盘** ，这里我就安装到 **D 盘** <br>

然后点击 **Install** 就开始安装了 <br>

![images](/images/2019-08-21/03.png)

-----

到这个界面就表示安装成功了 ， 点击 **Close** 按钮 <br>

![images](/images/2019-08-21/04.png)

-----


### <span id = "c">Fiddler使用：</span>

第一次使用可能会弹出这样一个警告框 ，<br>

他说你的默认浏览器可能正在运行，如果要使 **Fiddler** 能够工作，<br>

你必须使用 **winconfig** 工具启用默认浏览器 <br>

这里我选择无视他，直接取消掉，点击 **Cancel** <br>

![images](/images/2019-08-21/05.png)

-----

这里的话就是一些简单的操作了 <br>

主要是查看一些信息 <br>

![images](/images/2019-08-21/06.png)

-----

接下来我们可以设置代理，**Fiddler** 默认监听 **8888** 端口，**burp** 默认是 **8080** <br>

火狐浏览器我们应该比较熟悉，可以在火狐浏览器中设置 <br>

后面就可以配合 火狐浏览器进行抓包了 <br>

![images](/images/2019-08-21/07.png)

-----

如果要修改 **Fiddler** 的默认端口，那也可以 <br>

点击第一栏的 **Tools** ，<br>

然后在弹出来的 **Options** 里面选择 **Connection** <br>

勾选 **Allow remote computers to connect** ，点击OK，就可以修改默认端口了 <br>

![images](/images/2019-08-21/08.png)

-----

接下来就配置抓取 HTTPS 请求的条件了 <br>

选择 **HTTPS** 那栏，然后把那些框框全部勾上，<br>

如果中间有弹出什么，全部同意就可以了 <br>

![images](/images/2019-08-21/09.png)

-----

然后点击 **Actions** ，选择第二个，把证书导出到桌面 <br>

然后在桌面上就会出现一个 **Fiddler** 证书 <br>

![images](/images/2019-08-21/10.png)

-----

接下来把它导入到火狐浏览器中 <br>

选择 隐私和安全 --> 查看证书 <br>

![images](/images/2019-08-21/11.png)

-----

然后把桌面上那个证书导入进去就 OK 了 <br>

鉴于最近网络钓鱼比较疯狂，我就不信任他的电子邮件了 <br>

这样就大功告成了 <br>

![images](/images/2019-08-21/12.png) <br>

![images](/images/2019-08-21/13.png)

-----


### <span id = "zg">总结：</span>

相比 burp 来说的话，有些时候还是比较方便吧 <br>

各有各的样 <br>

参考文献： <br>

`https://blog.csdn.net/ychgyyn/article/details/82154433` <br>

`https://www.cnblogs.com/yyhh/p/5140852.html`

--------
