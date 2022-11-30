---
comefrom: buu
tools: [IDA]
encryptdecrypt: []
whatfile: [exe]
language: [C]
score: 28
flag: "flag{et_tu_brute_force@flare-on.com}"
tags:
- re
- smc
---

![[res/Pasted image 20221123232021.png]]

idapython
```python
import idc
addr = 0x40107c
for i in range(121):
    ida_bytes.patch_byte(addr + i, (idc.get_wide_byte(addr + i) ^ 162) + 34)
```

需要爆破，选择linux下用pwntools，用了都说好

smc，看脚本
```python
from pwn import *

data = open('greek_to_me.exe', 'rb').read()[0x27c:0x2f5]

v3 = 0
# for v3 in range(256):
b = bytes([((v2^162) + 34)&0xff for v2 in data])

tmp = disasm(b)
if '(bad)' not in tmp and '.byte' not in tmp:
    print(tmp)
    print(v3)

flag = [0x65, 0x74, 0x5f, 0x74, 0x75, 0x5f, 0x62, 0x72, 0x75, 0x74, 
    0x65, 0x5f, 0x66, 0x6f, 0x72, 0x63, 0x65, 0x40, 0x66, 0x6c, 0x61, 
    0x72, 0x65, 0x2d, 0x6f, 0x6e, 0x2e, 0x63, 0x6f, 0x6d
]

for i in flag: print(chr(i), end='')

# 0:   b3 65                   mov    bl, 0x65
# 2:   88 5d d5                mov    BYTE PTR [ebp-0x2b], bl
# 5:   c6 45 d6 74             mov    BYTE PTR [ebp-0x2a], 0x74
# 9:   b2 5f                   mov    dl, 0x5f
# b:   88 55 d7                mov    BYTE PTR [ebp-0x29], dl
# e:   c6 45 d8 74             mov    BYTE PTR [ebp-0x28], 0x74
# 12:   c6 45 d9 75             mov    BYTE PTR [ebp-0x27], 0x75
# 16:   88 55 da                mov    BYTE PTR [ebp-0x26], dl
# 19:   c6 45 db 62             mov    BYTE PTR [ebp-0x25], 0x62
# 1d:   c6 45 dc 72             mov    BYTE PTR [ebp-0x24], 0x72
# 21:   c6 45 dd 75             mov    BYTE PTR [ebp-0x23], 0x75
# 25:   c6 45 de 74             mov    BYTE PTR [ebp-0x22], 0x74
# 29:   88 5d df                mov    BYTE PTR [ebp-0x21], bl
# 2c:   88 55 e0                mov    BYTE PTR [ebp-0x20], dl
# 2f:   c6 45 e1 66             mov    BYTE PTR [ebp-0x1f], 0x66
# 33:   c6 45 e2 6f             mov    BYTE PTR [ebp-0x1e], 0x6f
# 37:   c6 45 e3 72             mov    BYTE PTR [ebp-0x1d], 0x72
# 3b:   c6 45 e4 63             mov    BYTE PTR [ebp-0x1c], 0x63
# 3f:   88 5d e5                mov    BYTE PTR [ebp-0x1b], bl
# 42:   c6 45 e6 40             mov    BYTE PTR [ebp-0x1a], 0x40
# 46:   c6 45 e7 66             mov    BYTE PTR [ebp-0x19], 0x66
# 4a:   c6 45 e8 6c             mov    BYTE PTR [ebp-0x18], 0x6c
# 4e:   c6 45 e9 61             mov    BYTE PTR [ebp-0x17], 0x61
# 52:   c6 45 ea 72             mov    BYTE PTR [ebp-0x16], 0x72
# 56:   88 5d eb                mov    BYTE PTR [ebp-0x15], bl
# 59:   c6 45 ec 2d             mov    BYTE PTR [ebp-0x14], 0x2d
# 5d:   c6 45 ed 6f             mov    BYTE PTR [ebp-0x13], 0x6f
# 61:   c6 45 ee 6e             mov    BYTE PTR [ebp-0x12], 0x6e
# 65:   c6 45 ef 2e             mov    BYTE PTR [ebp-0x11], 0x2e
# 69:   c6 45 f0 63             mov    BYTE PTR [ebp-0x10], 0x63
# 6d:   c6 45 f1 6f             mov    BYTE PTR [ebp-0xf], 0x6f
# 71:   c6 45 f2 6d             mov    BYTE PTR [ebp-0xe], 0x6d
# 75:   c6 45 f3 00             mov    BYTE PTR [ebp-0xd], 0x0
# 0
# et_tu_brute_force@flare-on.com%
```