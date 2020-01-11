---
layout: post
title: "汇编语言笔记(十三)--adc、sbb以及cmp指令"
date: 2020-01-10
description: "汇编语言"
tag: 汇编语言
---
---

### 前言：

adc、sbb以及cmp指令 。

---


### 目录：

* <a href="#a" target="_self">adc指令</a>
* <a href="#b" target="_self">sbb指令</a>
* <a href="#c" target="_self">cmp指令</a>
* <a href="#zg" target="_self">总结</a>

-------


### <span id = "a">adc指令：</span>

adc 是带进位加法指令，它利用了CF位上记录的进位值 <br>

指令格式： **adc 操作对象1,操作对象2** <br>

功能： **操作对象1 = 操作对象1 + 操作对象2 + CF** <br>

例如指令 `adc ax,bx` 实现的功能是: **(ax)=(ax)+(bx)+CF** <br>

例如： <br>

```c
mov ax,2
mov bx,1
sub bx,ax
adc ax,1
```
执行后，`(ax)=4` 。 adc执行时，相当于计算: `(ax)+1+CF = 2+1+1 = 4`  <br>

**add ax, dx**;    ---> **ax = ax+dx** <br>

**adc ax, dx**;    ----> **ax = ax+dx+carry(进位)** <br>

**sub ax, dx**;  ----> **ax = ax - dx** <br>

**sbb ax, dx**; ------> **ax = ax - dx - carry**

-----


### <span id = "b">sbb指令：</span>

sbb是带借位减法指令，它利用了CF位上记录的借位值。 <br>

指令格式：**sbb 操作对象1,操作对象2**  <br>

功能：**操作对象1 = 操作对象1 - 操作对象2 - CF** <br>

SBB与SUB的区别  <br>

**SUB AX,BX** 的结果是 **AX-BX** <br>

**SBB AX,BX** 的结果是 **AX-BX-CF**（进/借位标志）

举个粟子： <br>

将 **dx:ax** 中存放的32位无符号数减去BX内的16位无符号数 <br>

**sub ax,bx** ; 结果的低16位，如果ax小于bx将产生借位，导致CF=1 <br>

**sbb dx,0** ; 高16位-CF，若前一步出现借位，则据此调整高16位的内容

-----


### <span id = "c">cmp指令：</span>

cmp 是比较指令，cmp 的功能相当于减法指令，只是不保存结果。 <br>

cmp 指令执行后，将对标志寄存器产生影响。 <br>

其他相关指令通过识别这些被影响的标志寄存器位来得知比较结果。 <br>

cmp指令格式: **cmp 操作对象1,操作对象2**

功能：计算 **操作对象1 - 操作对象2** ，但并不保存结果，仅仅根据计算结果对标志寄存器进行设置。

例如指令 `cmp ax,ax` , 做 `(ax)-(ax)` 的运算，结果为0，但并不在ax中保存，

仅影响flag的相关各位 。 指令执行后： **zf=1 ，pf=1 ，sf=0 ，cf=0 ，of=0** 。

比如： <br>

```c
mov ax,8
mov bx,3
cmp ax,bx
```

执行后: **(ax)=8, zf=0 ，pf=1 ，sf=0 ，cf=0 ，of=0** 。

通过cmp指令执行后，相关标志位的值就可以看出比较的结果。

`cmp ax,bx`

如果 **(ax)=(bx)** ，则 **(ax)-(bx)=0** ,所以：**zf=1** ;

如果 **(ax)≠(bx)** ，则 **(ax)-(bx)≠0** ,所以：**zf=0** ;

如果 **(ax)<(bx)** ，则 **(ax)-(bx)** 将产生借位，所以：**cf=1** ;

如果 **(ax)≥(bx)** ，则 **(ax)-(bx)** 不必借位，所以：**cf=0** ;

如果 **(ax)>(bx)** ，则 **(ax)-(bx)** 既不必借位，结果又不为0 ，所以：**cf=0** 并且 **zf=0** ;

如果 **(ax)≤(bx)** ，则 **(ax)-(bx)** 既可能借位，结果可能为0 ，所以：**cf=1** 或 **zf=1** ;

 

指令 `cmp ax,bx` 的逻辑含义是比较 ax 和 bx 中的值，如果执行后：

**zf=1** ，说明 **(ax)=(bx)**

**zf=0** ，说明 **(ax)≠(bx)**

**cf=1** ，说明 **(ax)<(bx)**

**cf=0** ，说明 **(ax)≥(bx)**

**cf=0** 并且 **zf=0** ， 说明 **(ax)>(bx)**

**cf=1** 或 **zf=0** ，说明 **(ax)≤(bx)**

-----


### <span id = "zg">总结：</span>

adc、sbb以及cmp指令 <br>
