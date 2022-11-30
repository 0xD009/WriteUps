---
comefrom: buu
tools: [IDA]
encryptdecrypt: []
whatfile: [exe]
language: [Cpp]
score: 1
flag: "flag{a_3a2y_re_for_test}"
tags:
- re
- 花指令
---

本题主要考察[[花指令]]

整个程序只有只有一种花指令：
![[res/Pasted image 20221029003243.png]]
逻辑大概是通过call和ret两个指令和esp的移动（？栈清空），让IDA误认为函数已经结束了
恢复方法就是看汇编进行理解，发现让程序往后执行就行，所以图中红色方框内全部nop掉即可

花指令恢复后的两个重要函数：
![[res/Pasted image 20221029002819.png]]

![[res/Pasted image 20221029002843.png]]

虽然不算非常非常简单，但是至少一目了然了
下面是脚本

```python
from Crypto.Util.number import long_to_bytes

cipher = [2351698746, 4148999158, 4276070130, 2871606843, 651135530, 2292314745]

key = [0x3, 0x10, 0xd, 0x4, 0x13, 0xb]

def dec(a, k):
    a ^= 1 << k
    a = ((~a << 16) & 0xffffffff) | ((a) >> 16)
    a = ((a << k) & 0xffffffff) | (a >> (32 - k))
    return a

for i in range(5, 0, -1):
    cipher[i] ^= cipher[i - 1]

for i in range(6):
    cipher[i] = dec(cipher[i], key[i])

flag = b''

for _ in cipher: flag += long_to_bytes(_)

print(flag)

#flag{a_3a2y_re_for_test}

```