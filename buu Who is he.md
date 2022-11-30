---
comefrom: buu
tools: [dnspy, CheatEngine]
encryptdecrypt: [DES]
whatfile: [dll]
language: [CSharp]
score: 1
flag: "flag{She_P1ay_Black_Hole_Very_Wel1!LOL!XD!}"
tags:
- re
- unity
---

姬霓太美鬼畜游戏，DES加密，unity中的字符常量一般不存在于.dll文件中，而且是以utf-16（Unicode）的格式，即每个字符后面接一个\x00，一开始以为key是4位的，实际上是还在他们之间插了\x00形成了8位key

动调的时候提示模块未被加载，好奇怪

最后虽然解出了假flag，然后去看别人wp发现了Cheat Engine这个工具，用于修改进程中的内存，还可以查看反汇编