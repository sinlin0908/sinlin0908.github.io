---
title: Python 的 try-except
date: 2018-02-01 20:03:11
tags: python
categories:
- python
- 語法學習
---

## 例外處理
當我們寫程式時，會發生一些錯誤，像是 list 超出範圍、 open file 卻找不到檔案等等。
這些電腦都會進行報錯，但是我們不想中斷程式，想繼續進行時該怎麼辦呢?

這時候我們就使用 try-exccept 語法。

舉個例子: 我們進行 open example.txt，但是事實上並沒有這個檔案會發生什麼事?

```python
# -*- coding: utf-8 -*-

file = open('example.txt','r')
---------------執行結果---------------
    file = open('example.txt','r')
FileNotFoundError: [Errno 2] No such file or directory: 'example.txt'
```
如預期的，電腦告訴我們找不到 example.txt 這個檔案。
<!--more-->

當遇到這個問題，我們想要問 user 是否要創這個檔案時，可以使用 `try` 的語法:

```python
# -*- coding: utf-8 -*-

try:
    file = open('example.txt','r')
except Exception as error:
    print('there is no file!')
    response = input("do you want to create new file?[y/n]: ")
    if response == 'y':
        file = open('example.txt','w')
    else:
        pass
else:
    print("open successfully!")
```
來說明這段 code:
1. 首先，我們先執行 `try` 來打開文件。
2. 如果有錯誤我們就執行 `except` 來處理錯誤，我們把錯誤的細節存放在 `error` 這個 variable，之後詢問 user 是否要創建這個檔案。
{%note warning %} 事實上有很多種 exception
運用 `某個Exception as error` 的方式來處理特定 exception，
這個例子是處理全部的 exception {% endnote %}
3. 第12行的 `else` 則是 `try`的語句沒有報錯時才來執行。

## 製作自己的 exception
 通常所有的 exception 都被定義在 Python 裡面，但我們也可以自己創建一個 exception。

 `except 是一個 class` ，他是 Exception 的 子類別。這個例子是製作一個 exception 叫做 UppercaseException，當遇到大寫的單字就會丟出這個 exception。

```python
# -*- coding: utf-8 -*-
class UppercaseException(Exception):
    pass

words = ['apple','cat','dog','MOMO']
for word in words:
    if word.isupper():
        raise UppercaseException(word)
---------------執行結果---------------
line 9, in <module>
    raise UppercaseException(word)
__main__.UppercaseException: MOMO

```

## 資料來源:
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)