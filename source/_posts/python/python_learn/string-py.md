---
title: Python 的 String
date: 2018-01-23 20:50:52
tags: python
categories:
- python
- 語法學習
---
## Python 字串
字串是一系列的字元，使用 `' '`或者`" "`來建立字串。
與其他語言不同的是，Python的字元是`不可改變的`，不能夠直接更改字串。

```Python
name = 'Blank'
name[0] = 'A'
print(name)

---------------執行結果---------------
name[0] = 'A'
TypeError: 'str' object does not support item assignment
```
但是可以將一部分字串複製到其他字串，來產生相同效果。
<!--more-->

## str()來轉換資料型態
我們可以使用 `str()`來將其他資料型態轉成字串:

```python
number = 98.8
number = str(number)
print(number,type(number))

number = 123
number = str(number)
print(number,type(number))

number = 1.0e4
number = str(number)
print(number,type(number))

---------------執行結果---------------
98.8 <class 'str'>
123 <class 'str'>
10000.0 <class 'str'>

```
## 用 + 來結合
我們可以使用 + 來串接字串

```python
a = 'hello'
b = 'world'

print(a+b)
---------------執行結果---------------
helloworld  #不會加上空格

```
## 用 len()來取得字串長度
```python
a = 'hello'
b = ''  #沒加東西
c = ' ' #空格
print(len(a))
print(len(b))
print(len(c))

---------------執行結果---------------
5
0
1

```
我們可以發現空格也算一個字元。

## 分割
當我們想要分割一個字串時我們可以使用`.split()`，使用一些分割符號將一個字串分解成一個短字串的`list`。

```python
mystring = 'I am a student. I like Python'
print(mystring.split(' ')) #以空白做分割

---------------執行結果---------------
['I', 'am', 'a', 'student.', 'I', 'like', 'Python']

```
## 結合
若我們想把一個值為短字串的list結合成一個字串，我們可以使用`.join()`，並提供將list串接的字串。
用法:
    string.join(list)

```python
names_list = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
names_string = ', '.join(names_list) #以 ', '做串接
print(names_string)

---------------執行結果---------------
Mike, John, Tim, Amy, Jenny

```
## 字元判斷 function
`.isalnum()`:
判斷字符串裡，是不是由數字或是大小寫英文字母組成的，為真就返回True，若是有包含特殊符號(包含空格和換行)的為就會返回False

```python
word = 'apple'
print(word.isalnum())

string = 'i am 123'
print(string.isalnum())

string2 = '@@ hello'
print(string2.isalnum())

---------------執行結果---------------
True
False
False

```
`.isalpha()`
判斷字符串，是不是所有字符都是為大小寫的英文字母，為真返回True，反則返回False

```python
word = 'apple'
print(word.isalpha())

num = '123'
print(num.isalpha())

---------------執行結果---------------
True
False

```
`.isdigit()`
判斷字符串中，是不是數字(整數)

```python
num = '123'
print(num.isdigit())

num2 = '123.88888'
print(num2.isdigit())

word = 'aaaa'
print(word.isdigit())

---------------執行結果---------------
True
False
False

```
還有一些 function 等到有用到再寫吧......

## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)