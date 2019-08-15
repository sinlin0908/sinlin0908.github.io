---
title: Python Comprehensions
date: 2018-01-30 16:25:51
tags: python
categories: 
- python
- 語法學習

---

## 什麼是 Comprehensions(生成式)

我們可以用 `for` Loop 建立一個 1~5 的 list

```python
number_list = []
for number in range(0,6):
    number_list.append(number)
```
但是，要建立比較符合 Python 風格的方式，就是使用  Comprehensions。
用法如下:
>[ 輸入 list 的值 for 項目 in 可跌代的資料結構 ]

<!--more--> 

以下是例子:

```python
number_list = [number for number in range(0,6)]
print(number_list)
---------------執行結果---------------
[0, 10, 20, 30, 40, 50]

```
來說明第一行 code ，第一個 number 是要寫入 list 的 value ，第二個 number 是負責for迭代。

再看一個例子:

```python
number_list = [number*10 for number in range(0,6)]
print(number_list)
---------------執行結果---------------
[0, 10, 20, 30, 40, 50]

```
number 從 range() 取道值後，乘 10 在寫入 list。

假如我們從 0 到 10 中 選出偶數放入 list 該怎麼辦?
不擔心! Comprehensions 可以添加 if statement !!
{%note info %} [ 輸入 list 的值 for 項目 in 可跌代的資料結構 if 條件式 ]  {% endnote %}

```python
number_list = [number for number in range(0,11) if number % 2 == 0]
print(number_list)
---------------執行結果---------------
[0, 2, 4, 6, 8, 10]

```

生成式不只有 list 可以用 dict、set都可以使用 
除了 Tuple!! 

## 資料來源:
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)