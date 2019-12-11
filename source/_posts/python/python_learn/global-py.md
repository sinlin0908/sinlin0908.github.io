---
title: Python 命名空間
date: 2018-02-01 17:26:25
tags: python
categories:
- python
- 語法學習
---
## 什麼是命名空間

每一個 function or class 等等都有定義自己的命名空間。
假如你在 fun1( ) 有一個 variable 叫做 X，又在 fun2( ) 裡面有個 variable 也叫做 X，
雖然名稱一樣，但是他們對應的卻是不一樣的東西，而且也不跨界使用。
來看看例子:
```python
def print_animal():
    animal = 'cat'
    print(animal)

def print_cat():
    print(animal)

if __name__ =='__main__':
    print_animal()
    print_cat()
---------------執行結果---------------
line 6, in print_cat
    print(animal)
NameError: name 'animal' is not defined
```
電腦會報錯!，因為 `print_cat()` 沒有定義 `animal` 這個 variable
<!--more-->

## Global Variable
程式主要部份是全域空間，在那裡命名的 variable 就叫做 global variable。

```python
animal = 'cat'  #global variable

def print_animal():
    print('print_animal:',animal)

def print_cat():
    print('print_cat',animal)

if __name__ =='__main__':
    print_animal()
    print_cat()
---------------執行結果---------------
print_animal: cat
print_cat cat

```
這樣大家都可以取得 animal 的 value。

But!!! 如果想在 function 裡面取得 global variable 的 value ，並且更改他
電腦會丟一個錯誤給你
```python
animal = 'cat'  #global variable

def print_animal():
    print('before print_animal:',animal)
    animal = 'dog'
    print('after_access: ',animal )

if __name__ =='__main__':
    print_animal()
    print('after print_animal: ',animal)
---------------執行結果---------------
in print_animal
    print('before print_animal:',animal)
UnboundLocalError: local variable 'animal' referenced before assignment
```
那如果寫成這樣呢?
```python
animal = 'cat'
print('before print_animal: ',animal,id(animal))
def print_animal():
    animal = 'dog'
    print('after_access: ',animal,id(animal) )

if __name__ =='__main__':
    print_animal()
    print('after print_animal: ',animal, id(animal))
---------------執行結果---------------
before print_animal:  cat 26597248
after_access:  dog 24142752
after print_animal:  cat 26597248
```
是輸出了 dog 沒有錯，但是此時的 animal 已經是 local variable 了

那要怎麼存取 global variable 而不是變成 local variable?
我們使用 `global key word`

```python
# -*- coding: utf-8 -*-
animal = 'cat'
print('before print_animal:',animal)
def print_animal():
    global animal  #不能寫成 global animal = 'dog'!
    animal = 'dog'
    print('after_access: ',animal )

if __name__ =='__main__':
    print_animal()
    print('after print_animal: ',animal)
---------------執行結果---------------
before print_animal: cat
after_access:  dog
after print_animal:  dog
```
這樣我們就可以自由存取 global variable

## 資料來源:
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)