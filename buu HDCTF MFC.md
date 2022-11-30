---
comefrom: buu
tools: [IDA, xspy, 彗星小助手]
encryptdecrypt: [DES]
whatfile: [exe]
language: [Cpp]
score: 1
flag: "flag{thIs_Is_real_kEy_hahaaa}"
tags:
- re
- question
---
比较困难，与MFC框架有关，wp都提到了xspy工具，然而从github上下载下来只有源码，编译非常困难，搜了半天才发现一个编译好的版本，在CSDN上收费，然后就发现了免费下载CSDN文件的“WATERLIKE文档共享助手“，就算是买也只要六毛钱，总是明天再干吧

然后是发送消息的问题，用C程序发不了，不知道为什么找不到句柄，用了“彗星小助手”，非常舒服，然后解DES，key用前8位就行
![](res/Pastedimage20221026003523.png)