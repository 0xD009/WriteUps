---
comefrom: buu
tools: [IDA, binwalk]
encryptdecrypt: [爆破]
whatfile: [bin, exe]
language: [C]
score: 1
flag: "flag{Flag_8i7244980f}"
tags:
- re
- linux
---

用wsl的file指令查到是PE32＋文件，改后缀，拖进IDA之后发现大量赋值，只scan一个int，输出一些东西，没有后续逻辑，极有可能输出的就是flag，这种情况爆破就好了
