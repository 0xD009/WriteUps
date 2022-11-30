---
comefrom: buu
tools: [IDA, x64dbg]
encryptdecrypt: [AES]
whatfile: [exe]
language: [C++]
score: 1
flag: "flag{Ae3_C8c_I28_pKcs79ad4}"
tags:
- re
- antidebug
---

用IDA的findcrypt插件找到AES和base64特征，找到key是这样：
![[res/Pasted image 20221020212430.png]]
这里是做了拓展key操作

这里有一详细的介绍：[(18条消息) AES-CBC加密_Ni9htMar3的博客-CSDN博客_aes-cbc算法](https://blog.csdn.net/Ni9htMar3/article/details/53416049)

用附加进程的方式调试，找到最后比较的时候用的密文：
![[res/Pasted image 20221020212650.png]]
以及加密过程中有一段循环在异或，这是跟iv有关的操作，所以得到iv：
![[res/Pasted image 20221020214025.png]]

学着用python解一下AES-CBC
```python
from base64 import b64decode
from Crypto.Cipher import AES

cipher = b'nKnbHsgqD3aNEB91jB3gEzAr+IklQwT1bSs3+bXpeuo='
key = b'sycloversyclover'
iv = b'sctfsctfsctfsctf'

aes = AES.new(key,AES.MODE_CBC,iv)

den_text = aes.decrypt(b64decode(cipher))

print(den_text)
```