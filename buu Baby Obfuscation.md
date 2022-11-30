---
comefrom: buu
tools: [IDA]
encryptdecrypt: []
whatfile: [exe]
language: [C]
score: 1
flag: "flag{0bfu5er}"
tags:
- re
- obfuscation
---

本以为是ollvm一类的混淆，事实上只是自己把一些运算函数复杂化了
![[res/Pastedimage20221021204930.png]]
随便看一下，然后动调跟一下，把逻辑理清楚：
```python
str -= v31[j - 1]
str ^= v31[j - 1]
str *= 10
str *= 10
```

下面是脚本：
```python
cipher = [
    0,
    7801,
    7801,
    8501,
    5901,
    8001,
    6401,
    11501,
    4601,
    9801,
    9601,
    11701,
    5301,
    9701,
    10801,
    12501,
]
key = [2, 3, 4, 5]
flag = ''
for i in range(1, len(cipher)):
    cipher[i] //= 100
    cipher[i] ^= key[(i - 1) % 4]
    cipher[i] += key[(i - 1) % 4]
    flag += chr(cipher[i])
print(flag)

```