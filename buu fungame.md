---
comefrom: buu
tools: [IDA]
encryptdecrypt: [base64]
whatfile: [exe]
language: [C]
score: 1
flag: "flag{Re_1s_So0_funny!=#@a1s0_pWn}"
tags:
- re
- pwn
---

事实上本题是一道pwn题，利用栈溢出跳转到隐藏函数的地址即可，最后还解了一个base64

