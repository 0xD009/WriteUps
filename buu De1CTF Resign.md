---
comefrom: buu
tools: [IDA]
encryptdecrypt: [base64]
whatfile: [exe]
language: [C]
score: 1
flag: "flag{E_L4nguag3_1s_K3KeK3_N4Ji4}"
tags:
- re
- question
---

纯动调题，跟下面这些函数
![[res/Pastedimage20221102003006.png]]![[res/Pastedimage20221102003045.png]]
![[res/Pastedimage20221102003105.png]]
![[res/Pastedimage20221102003139.png]]
然后里面还有两层

逻辑是换表（这个简单，前面没有指出函数在哪），然后对加密出来的字符做映射，射到normaltable-1的位置上

提取cipher，写脚本
```python
cipher_bytes = [
    0x08, 0x3B, 0x01, 0x20, 0x07, 0x34, 0x09, 0x1F, 0x18, 
    0x24, 0x13, 0x03, 0x10, 0x38, 0x09, 0x1B, 0x08, 0x34, 
    0x13, 0x02, 0x08, 0x22, 0x12, 0x03, 0x05, 0x06, 0x12, 
    0x03, 0x0F, 0x22, 0x12, 0x17, 0x08, 0x01, 0x29, 0x22, 
    0x06, 0x24, 0x32, 0x24, 0x0F, 0x1F, 0x2B, 0x24, 0x03, 
    0x15, 0x41, 0x41
]

import base64

key1 = '0123456789QWERTYUIOPASDFGHJKLZXCVBNMqwertyuiopasdfghjklzxcvbnm+/'
key2 = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/'

cipher = ''
for i in range(46): 
    print(cipher_bytes[i])
    cipher += key2[cipher_bytes[i]-1]
cipher += '=='

transtable = str.maketrans(key1, key2)

cipher = cipher.translate(transtable)

flag = base64.b64decode(cipher.encode('utf-8'))

print(flag)

#de1ctf{E_L4nguag3_1s_K3KeK3_N4Ji4}
```

其实值得研究的地方还有很多，以后二刷的时候再看看