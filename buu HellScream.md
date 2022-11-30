---
comefrom: buu
tools: [IDA]
encryptdecrypt: [RSA]
whatfile: [exe]
language: [Cpp]
score: 24
flag: "flag{274964845CCC8AAA8A0CD62B0971A23954F741240EEDD43A02F79DA2B7372D68C80C}
"
tags:
- re
---

这是很难的一道题，实际上系看雪CTF2016

参考一下wp：
https://blog.csdn.net/m0_46296905/article/details/116382650
https://bbs.pediy.com/thread-258108.htm
https://bbs.pediy.com/thread-214562-1.htm

解题过程在IDA的注释里写好了
![[res/Pasted image 20221117214713.png]]
进来是把一串字符变成了数，用了一个特殊的table，后面对输入也是这样变换的
后来知道这是RSA公钥，这种大数应该算RSA的一个特征

![[res/Pasted image 20221117214846.png]]
一些注意点

![[res/Pasted image 20221117214946.png]]
主加密，根据username生成了一个公钥e然后实际上是不准的，加遍历100遍，其中有一次是正确的即可，其实考验了对RSA算法的熟悉程度，不然找不到e的，这里我们读出e的初始值，然后找到e+2与$\varphi(n)$互素，细节在图里，不多赘述

最后是解密部分
```python
from Crypto.Util.number import bytes_to_long
import gmpy2

c = bytes_to_long(b'Happy Birthday Buddy\x00ok'[::-1])
n = 0xA324F100182D501F6F6F78F397A3AA59641023D6A3DED8A4BF344F1E0FC71C188F4D

p = 62822928286347608648869628628072621308819
q = 76979057716441943100156208562083628995999

e = 0x9CA87DE3775787F7695F3F316E503600348AB6F58BEF375D0ED8F8BE84425FA7A6C3 + 2
phi = (p - 1) * (q - 1)
d = gmpy2.invert(e, phi)

print(hex(pow(c, d, n)))

# 0x274964845ccc8aaa8a0cd62b0971a23954f741240eedd43a02f79da2b7372d68c80c
```
这种题是很明显的cpp，传参传些莫名其妙的东西点进去看才知道是坨什么东西，估计是结构体，很多时候还是马后炮出来的
