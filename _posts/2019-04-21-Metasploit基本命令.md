---
layout: post
title: "Metasploit基本命令"
date: 2019-04-21
description: "Metasploit"
tag: Metasploit
---
---

### 前言

Metasploit入坑到放弃笔记 <br>

**特别说明：本笔记仅供安全研究使用，如有其他行为后果自负** 

------


### 环境

Kali 2017

-----


### 目录：

* <a href="#one" target="_self">1. 开启控制台</a>
* <a href="#a1" target="_self">2. 搜索模块</a>
* <a href="#a2" target="_self">3. 调用模块</a>
* <a href="#a3" target="_self">4. 查看模块使用方法</a>
* <a href="#a4" target="_self">5. 设置目标IP地址</a>
* <a href="#a5" target="_self">6. 设置目标端口</a>
* <a href="#a6" target="_self">7. exploit</a>
* <a href="#zj" target="_self">总结</a>


-------


### <span id = "one">1. 开启控制台</span>

命令：
```bash
msfconsole
```

![images](/images/2019-04-21/msf01.png) 

-----


### <span id = "a1">2. 搜索模块</span>

命令：
```bash
search ms17-010  # 模块名
```

这里以搜索 **ms17-010** 为例，<br>

**auxiliary** 开头的为测试模块，也就是 **POC**，看看存不存在漏洞，<br>

**exploit** 开头的为攻击模块

![images](/images/2019-04-21/msf02.png) 

-------


### <span id = "a2">3. 调用模块</span>

命令：
```bash
use auxiliary/scanner/smb/smb_ms17_010
```

![images](/images/2019-04-21/msf03.png) 


-----


### <span id = "a3">4. 查看模块使用方法</span>

命令：
```bash
show options
```

**Current Setting**(当前设置) ，也就是默认设置 <br>

**Required**(需要) ，必须要设置的 <br>

**RHOSTS** 目标**ip**地址 <br>

**RPORT** 端口，不设置的话默认为 **445** <br>

![images](/images/2019-04-21/msf04.png) 

--------


### <span id = "a4">5. 设置目标IP地址</span>

命令：
```bash
set RHOSTS 192.168.1.2  # 目标IP地址
```

![images](/images/2019-04-21/msf05.png)

---------


### <span id = "a5">6. 设置目标端口</span>

命令：
```bash
set RPORT 445  # 目标I端口
```

如果不设置端口，默认为 **445** <br>

![images](/images/2019-04-21/msf06.png)

---------


### <span id = "a6">7. exploit</span>

命令：
```bash
exploit
```

设置完成后就可以 **exploit** 了

---------


### <span id = "zj">总结</span>

一点基础的模块调用命令吧 ，<br>

菜就得多学<br>

--------
