---
title: Python 的 tuple
date: 2018-01-28 20:08:15
tags: python
categories:
- python
- 語法學習
---
## 什麼是 Tuple?
基本上跟 list 差不多，只是 Tuple 建立之後，是__***不能更改的***__，所以又稱`Read only List`。

## 使用 Tuple
相對 List使用[]，Tuple使用`()`來建立。

Tuple只有兩個 function 可以用: `index()`、`count()`。

```Python
names = ("Rogers", "Stark", "Thor", "Loki", "Thor", "Thor")

print(names.index("Stark"))
print(names.count("Thor"))

---------------執行結果---------------
1
3
```
<!--more-->
## 使用時機
什麼時候會用到 Tuple?
1. function return 多值 or 傳入多值。
```python
def get_error_details():
    return (2, 'details')

(errnum, errstr) = get_error_details()
```
2. 存取一些不能被更改的資料
3. Swap:
在 C 語言寫 swap 通常要多一個 variable 當作暫存，但是python可以使用`Tuple`來實作:
```python
(x, y) = (y, x)
```

## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)
[Python 慣用語](http://seanlin.logdown.com/)
