---
comefrom: buu
tools: [uncompyle6]
encryptdecrypt: []
whatfile: [pyc]
language: [python]
score: 1
flag: "flag{{this_must_be_the_best_encryption_method_evr_henceforth_this_is_the_new_Advanced_Encryption_Standard_anyways_i_dont_really_have_a_good_vid_but_i_really_enjoy_this_song_i_hope_you_will_enjoy_it_aswell!_youtube.com/watch?v=E5yFcdPAGv0}}"
tags:
- re
- vm
---

[[Python逆向]]
python虚拟机
看代码就明白了
```python
# uncompyle6 version 3.8.0
# Python bytecode 3.6 (3379)
# Decompiled from: Python 3.9.6 (tags/v3.9.6:db3ff76, Jun 28 2021, 15:26:21) [MSC v.1929 64 bit (AMD64)]
# Embedded file name: circ.py
# Compiled at: 2019-12-14 02:29:55
# Size of source mod 2**32: 5146 bytes
zero = 0
one = ~zero * ~zero
two = one + one


def 䯂(opcode):
    t1 = zero
    t2 = zero
    reg = [zero] * two ** (two * two)
    data = [zero] * 100
    flag = []
    while opcode[t1][zero] != 'exit':
        cmd = opcode[t1][zero].lower()
        paras = opcode[t1][one:]
        if cmd == '뉃':
            reg[paras[zero]] = reg[paras[one]] + reg[paras[two]]
        else:
            if cmd == '렀':
                reg[paras[zero]] = reg[paras[one]] ^ reg[paras[two]]
            else:
                if cmd == '렳':
                    reg[paras[zero]] = reg[paras[one]] - reg[paras[two]]
                else:
                    if cmd == '냃':
                        reg[paras[zero]] = reg[paras[one]] * reg[paras[two]]
                    else:
                        if cmd == '뢯':
                            reg[paras[zero]] = reg[paras[one]] / reg[paras[two]]
                        else:
                            if cmd == '륇':
                                reg[paras[zero]] = reg[paras[one]] & reg[paras[two]]
                            else:
                                if cmd == '맳':
                                    reg[paras[zero]] = reg[paras[one]] | reg[paras[two]]
                                else:
                                    if cmd == '괡':
                                        reg[paras[zero]] = reg[paras[zero]]
                                    else:
                                        if cmd == '뫇':
                                            reg[paras[zero]] = reg[paras[one]]
                                        else:
                                            if cmd == '꼖':
                                                reg[paras[zero]] = paras[one]
                                            else:
                                                if cmd == '뫻':
                                                    data[paras[zero]] = reg[paras[one]]
                                                else:
                                                    if cmd == '딓':
                                                        reg[paras[zero]] = data[paras[one]]
                                                    else:
                                                        if cmd == '댒':
                                                            reg[paras[zero]] = zero
                                                        else:
                                                            if cmd == '묇':
                                                                data[paras[zero]] = zero
                                                            else:
                                                                if cmd == '묟':
                                                                    reg[paras[zero]] = input(
                                                                        reg[paras[one]])
                                                                else:
                                                                    if cmd == '꽺':
                                                                        data[paras[zero]] = input(
                                                                            reg[paras[one]])
                                                                    else:
                                                                        if cmd == '돯':
                                                                            print(
                                                                                reg[paras[zero]])
                                                                        else:
                                                                            if cmd == '뭗':
                                                                                print(
                                                                                    data[paras[zero]])
                                                                            else:
                                                                                if cmd == '뭿':
                                                                                    t1 = reg[paras[zero]]
                                                                                else:
                                                                                    if cmd == '뮓':
                                                                                        t1 = data[paras[zero]]
                                                                                    else:
                                                                                        if cmd == '뮳':
                                                                                            t1 = flag.pop()
                                                                                        else:
                                                                                            if cmd == '믃':
                                                                                                if reg[paras[one]] > reg[paras[two]]:
                                                                                                    t1 = paras[zero]
                                                                                                    flag.append(
                                                                                                        t1)
                                                                                                    continue
                                                                                            else:
                                                                                                if cmd == '꽲':
                                                                                                    reg[7] = zero
                                                                                                    for i in range(len(reg[paras[zero]])):
                                                                                                        if reg[paras[zero]] != reg[paras[one]]:
                                                                                                            reg[7] = one
                                                                                                            t1 = reg[paras[two]]
                                                                                                            flag.append(
                                                                                                                t1)

                                                                                                else:
                                                                                                    if cmd == '꾮':
                                                                                                        괢 = ''
                                                                                                        for i in range(len(reg[paras[zero]])):
                                                                                                            괢 += chr(
                                                                                                                ord(reg[paras[zero]][i]) ^ reg[paras[one]])

                                                                                                        reg[paras[zero]] = 괢
                                                                                                    else:
                                                                                                        if cmd == '꿚':
                                                                                                            괢 = ''
                                                                                                            for i in range(len(reg[paras[zero]])):
                                                                                                                괢 += chr(
                                                                                                                    ord(reg[paras[zero]][i]) - reg[paras[one]])

                                                                                                            reg[paras[zero]] = 괢
                                                                                                        else:
                                                                                                            if cmd == '떇':
                                                                                                                if reg[paras[one]] > reg[paras[two]]:
                                                                                                                    t1 = reg[paras[zero]]
                                                                                                                    flag.append(
                                                                                                                        t1)
                                                                                                                    continue
                                                                                                            else:
                                                                                                                if cmd == '뗋':
                                                                                                                    if reg[paras[one]] > reg[paras[two]]:
                                                                                                                        t1 = data[paras[zero]]
                                                                                                                        flag.append(
                                                                                                                            t1)
                                                                                                                        continue
                                                                                                                else:
                                                                                                                    if cmd == '똷':
                                                                                                                        if reg[paras[one]] == reg[paras[two]]:
                                                                                                                            t1 = paras[zero]
                                                                                                                            flag.append(
                                                                                                                                t1)
                                                                                                                            continue
                                                                                                                    else:
                                                                                                                        if cmd == '뚫':
                                                                                                                            if reg[paras[one]] == reg[paras[two]]:
                                                                                                                                t1 = reg[paras[zero]]
                                                                                                                                flag.append(
                                                                                                                                    t1)
                                                                                                                                continue
                                                                                                                        else:
                                                                                                                            if cmd == '띇':
                                                                                                                                if reg[paras[one]] == reg[paras[two]]:
                                                                                                                                    t1 = data[paras[zero]]
                                                                                                                                    flag.append(
                                                                                                                                        t1)
                                                                                                                                    continue
        t1 += one


䯂([
    [
        '꼖', zero, 'Authentication token: '],
    [
        '꽺', zero, zero],
    [
        '꼖', 6, 'á×äÓâæíäàßåÉÛãåäÉÖÓÉäàÓÉÖÓåäÉÓÚÕæïèäßÙÚÉÛÓäàÙÔÉÓâæÉàÓÚÕÓÒÙæäàÉäàßåÉßåÉäàÓÉÚÓáÉ·Ôâ×ÚÕÓÔÉ³ÚÕæïèäßÙÚÉÅä×ÚÔ×æÔÉ×Úïá×ïåÉßÉÔÙÚäÉæÓ×ÜÜïÉà×âÓÉ×ÉÑÙÙÔÉâßÔÉÖãäÉßÉæÓ×ÜÜïÉÓÚÞÙïÉäàßåÉåÙÚÑÉßÉàÙèÓÉïÙãÉáßÜÜÉÓÚÞÙïÉßäÉ×åáÓÜÜ\x97ÉïÙãäãÖÓ\x9aÕÙÛ\x99á×äÕà©â«³£ï²ÕÔÈ·±â¨ë'],
    [
        '꼖', two, two ** (3 * two + one) - two ** (two + one)],
    [
        '꼖', 4, 15],
    [
        '꼖', 3, one],
    [
        '냃', two, two, 3],
    [
        '뉃', two, two, 4],
    [
        '괡', zero, two],
    [
        '댒', 3],
    [
        '꾮', 6, 3],
    [
        '꼖', zero, 'Thanks.'],
    [
        '꼖', one, 'Authorizing access...'],
    [
        '돯', zero],
    [
        '딓', zero, zero],
    [
        '꾮', zero, two],
    [
        '꿚', zero, 4],
    [
        '꼖', 5, 19],
    [
        '꽲', zero, 6, 5],
    [
        '돯', one],
    [
        'exit'],
    [
        '꼖', one, 'Access denied!'],
    [
        '돯', one],
    [
        'exit']])

```
这是处理过部分乱码的程序

```python
reg[0] = 'Authentication token: '

data[0] = input(reg[0])

reg[6] = 'á×äÓâæíäàßåÉÛãåäÉÖÓÉäàÓÉÖÓåäÉÓÚÕæïèäßÙÚÉÛÓäàÙÔÉÓâæÉàÓÚÕÓÒÙæäàÉäàßåÉßåÉäàÓÉÚÓáÉ·Ôâ×ÚÕÓÔÉ³ÚÕæïèäßÙÚÉÅä×ÚÔ×æÔÉ×Úïá×ïåÉßÉÔÙÚäÉæÓ×ÜÜïÉà×âÓÉ×ÉÑÙÙÔÉâßÔÉÖãäÉßÉæÓ×ÜÜïÉÓÚÞÙïÉäàßåÉåÙÚÑÉßÉàÙèÓÉïÙãÉáßÜÜÉÓÚÞÙïÉßäÉ×åáÓÜÜ\x97ÉïÙãäãÖÓ\x9aÕÙÛ\x99á×äÕà©â«³£ï²ÕÔÈ·±â¨ë'

reg[2] = 2 ** (3 * 2 + 1) - 2 ** (2 + 1)
# 120
reg[4] = 15

reg[3] = 1

reg[2] = reg[2] * reg[3]
# 120
reg[2] = reg[2] + reg[4]
# 135
reg[0] = reg[2]
# 135
reg[3] = 0

tmp = ''
for i in range(len(reg[6])):
    tmp += chr(ord(reg[6][i]) ^ reg[3])

reg[0] = 'Thanks'

reg[1] = 'Authorizing access...'

print(reg[0])

reg[0] = data[0]

tmp = ''
for i in range(len(reg[0])):
    tmp += chr(ord(reg[0][i]) ^ reg[2])
# 异或135

tmp = ''
for i in range(len(reg[0])):
    tmp += chr(ord(reg[0][i]) - reg[4])
# 减15

reg[5] = 19

reg[7] = 0
for i in range(len(reg[0])):
    if reg[0] != reg[6]:
        reg[7] = 1
        t1 = reg[5]
        flag.append(t1)
```
这是主逻辑伪代码，不能运行

```python
cipher = 'á×äÓâæíäàßåÉÛãåäÉÖÓÉäàÓÉÖÓåäÉÓÚÕæïèäßÙÚÉÛÓäàÙÔÉÓâæÉàÓÚÕÓÒÙæäàÉäàßåÉßåÉäàÓÉÚÓáÉ·Ôâ×ÚÕÓÔÉ³ÚÕæïèäßÙÚÉÅä×ÚÔ×æÔÉ×Úïá×ïåÉßÉÔÙÚäÉæÓ×ÜÜïÉà×âÓÉ×ÉÑÙÙÔÉâßÔÉÖãäÉßÉæÓ×ÜÜïÉÓÚÞÙïÉäàßåÉåÙÚÑÉßÉàÙèÓÉïÙãÉáßÜÜÉÓÚÞÙïÉßäÉ×åáÓÜÜ\x97ÉïÙãäãÖÓ\x9aÕÙÛ\x99á×äÕà©â«³£ï²ÕÔÈ·±â¨ë'

flag = ''

for i in cipher:
    flag += chr((ord(i) + 15) ^ 135)

print(flag)

#flag{{this_must_be_the_best_encryption_method_evr_henceforth_this_is_the_new_Advanced_Encryption_Standard_anyways_i_dont_really_have_a_good_vid_but_i_really_enjoy_this_song_i_hope_you_will_enjoy_it_aswell!_youtube.com/watch?v=E5yFcdPAGv0}}
```
这是题解