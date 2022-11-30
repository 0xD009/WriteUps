---
comefrom: buu
tools: [IDA, deflat]
encryptdecrypt: []
whatfile: [elf]
language: [Cpp]
score: 1
flag: "flag{mY-CurR1ed_Fns}"
tags:
- re
- ollvm
---

其实并不很难，先去掉混淆，然后看
![[res/Pasted image 20221027205036.png]]

循环地干同一件事

找到enc和加密关系式之后就可以开始写脚本解了，这里其实对下位的写逆更简单
然后对于第一位，是没有办法得到的，所以采取爆破的办法，这里学到一点：异或的优先级是比减法低的，之前一直以为异或与乘法同级

```python
cipher = [
    0, 0xF3, 0x2E, 0x18, 0x36, 0xE1, 0x4C, 0x22, 0xD1, 0xF9, 0x8C,
    0x40, 0x76, 0xF4, 0x0E, 0x00, 0x05, 0xA3, 0x90, 0x0E, 0xA5
]

for c in range(32, 128):
    flag = ''
    flag += chr(c)
    for i in range(1, 21):
        flag += chr(((cipher[i] ^ ((ord(flag[i - 1]) ^ 18) * 3 + 2)) - ord(flag[i - 1]) % 7) % 256)
    if 'flag' in flag: print(flag)

#flag{mY-CurR1ed_Fns}
```