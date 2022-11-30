---
comefrom: buu
tools: [IDA]
encryptdecrypt: []
whatfile: [exe]
language: [Cpp]
score: 1
flag: "flag{8cda1bdba8b7b68b68a8b71bdb8cda}"
tags:
- re
- pwn
---

这又是一道pwn题，感觉没什么好说的
![[res/Pastedimage20221029001502.png]]

三个函数形成虚函数表(?)，然后对输入的数据进行操作就行，事实上，这个函数的栈安全性很差，文件有多长就读多长，所以可以栈溢出来操作这三个函数

![[res/Pastedimage20221029002529.png]]

运用一点数学知识就可以知道，func1的结果是可以为0的，但func2的结果恒为正，但是v9的值由func1给定，所以我们的基本思路就是利用func0把func1和func2换个位置，然后构造数据使v9=0

最后构造出来的data是这样
![[res/Pasted image 20221029002255.png]]

即v9位取-1，func0的参数位取func1和func2相对v8的偏移

这样输入就能获取flag了