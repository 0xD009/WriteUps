---
comefrom: buu
tools: [dnspy]
encryptdecrypt: []
whatfile: [exe]
language: [Csharp]
score: 1
flag: "flag{Kitteh_save_galixy@flare-on.com}"
tags:
- re
---

Main
![[res/Pasted image 20221106000446.png]]

Stage1Form
![[res/Pasted image 20221106000419.png]]

Stage2Form
![[res/Pasted image 20221106000320.png]]

VictoryForm
![[res/Pasted image 20221106000927.png]]

exp：
```python
cipher = [
    9,
    8,
    19,
    17,
    9,
    55,
    28,
    18,
    15,
    24,
    10,
    49,
    75,
    51,
    45,
    32,
    54,
    59,
    15,
    49,
    46,
    0,
    21,
    0,
    65,
    48,
    45,
    79,
    13,
    1,
    2
]

key2 = 'RAINBOW'

key1 = [
    '\x03',
	' ',
	'&',
	'$',
	'-',
	'\x1e',
	'\x02',
	' ',
	'/',
	'/',
	'.',
	'/'
]

key = ''
for i in key1:
    key += chr(ord(i) ^ ord('A'))
key += ',' + 'RAINBOW'
print(key)

flag = ''
for i in range(len(cipher)):
    flag += chr(cipher[i] ^ ord(key[i % len(key)]))

print(flag)

#flag{Kitteh_save_galixy@flare-on.com}
```