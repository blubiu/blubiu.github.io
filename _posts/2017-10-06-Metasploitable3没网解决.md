---
layout: post
title: "从VBox虚拟机移植Metasploitable3到VM虚拟机没网问题"
date: 2017-10-06
description: "Metasploitable3没网解决"
tag: metasploitable3
---


### 前言
为了更好打线下比赛，安装一个Metasploitable3来练习下渗透技术，<br/>

Metasploitable3目前普遍安装在VirtualBox虚拟机，<br/>

因为我的虚拟机都是安装的VM上的，如果要换的话，全部都要换成VirtualBox，<br/>

这样未免有些麻烦，但是从VirtualBox移植到VM上又有点小问题，<br/>

此次记录从VirtualBox虚拟机移植到VM虚拟机没网问题解决方法。


---

### 第一步
**导入后不要开机，先在虚拟机设置里面将原有的两个网络适配器移除。**

![images](/images/2017-10-06/met1.png)

---

### 第二步
**接着在选项里面，在客户机操作系统里面，选择Microsoft Windwos(W)，**<br/>

<center>**版本选择Windows Server 2008 R2 x64**</center >

![images](/images/2017-10-06/met2.png)

---

### 第三步
**先打开虚拟机，然后再添加一个网络适配器(没有打开添加不知道行不行，你们可以试试)**

![images](/images/2017-10-06/met3.png)

---

### 第四步
**在终端里面输入ipconfig测试一下有没有网卡，之前是识别不到网卡的，**<br/>
**这里可以看到我是设置成功了，也可以上百度**

![images](/images/2017-10-06/met4.png)

---

### 第五步，开启渗透之旅
**在kali系统里面测试能不能相互连接，**<br/>
**我之前虚拟机网段都设置好了，如果没有大问题选择NET模式都是处于一个网段上的，**<br/>
**这里可以看到，nmap可以扫描出端口，浏览器也可以访问到，**<br/>
**说明已经成功了。**

![images](/images/2017-10-06/met5.png)

---

### 后续
**为学习打卡吧，虽然是小问题，**<br/>
**好记性不如烂笔头，**<br/>
**继续努力吧骚年！**<br/>
**Metasploitable3下载链接(其他表哥在FreeBuf上的分享)**<br/>
**链接: http://pan.baidu.com/s/1c1RTEN2 密码: 4ctm**<br/>
**(PS:合并命令去掉后面f即可)**
```
cat metasploitablea* | tar xjv
```
