---
title: Python 變數
date: 2018-01-22 15:26:00
tags: python
categories:
- python
- 語法學習
---
今天來了解一下 Python 的變數，他有些地方和 C 語言有所不同。

## 淺談物件
了解變數之前，我們需要先了解一下 Python 物件這個概念。
在 Python 中，所有東西，像是 boolean、int、float、string 等等，甚至是 function 都是由物件(object)來實作。

物件就像是一個盒子，而盒子裡面包含了很多資料，像是他的值、可以使用的 function ，最重要的是他的 type。

type 的功用就是決定他裡面的資料是用來做什麼的，像是盒子外面貼個標籤說這裡面是蘋果。在 Python 中，如果有個物件他的 type 是 string，我們就可以知道裡面的 value 是存放一個字串，並且有 isdigit()、split()等等 function 可以使用。
<!--more-->

## 變數使用
那我們要使用這些資料or物件時，要怎麼告訴電腦? 總不能說:嘿電腦!我要存取"那個"資料。電腦怎麼知道那個是哪個。

所以我們需要幫他們取一個名字，就像人一樣需要一個名字，而這個名稱就是__***變數(variable)***__，我們使用`=`來 assign object 給這個變數，以下code來示範:
```python
a = 7 # 把 int(7) 給 a 這個變數
```
之後我們就可以用 a 來叫這個 7 了。

但是，但是，但是 ~
在 Python 中，變數只是名稱，assign 不會將 value copy ，所以只是指派一個名稱給這個物件而已，算是這個物件的 referrence。

這樣好像很難懂XD 來看圖片好了:
![](/images/python/assign.png)

以 a = 7 這個例子來做圖，大概就是長這樣子。a 這個名稱指向這個 int 物件。

如果是以下程式碼呢?
```python
a = 100
b = a
print('a: ',id(a),'b: ',id(b))
---------------執行結果---------------
a:  1436754416 b:  1436754416

```
他們是指著同一塊 object，樣子如下圖:
![](/images/python/assign2.png)

所以當 b 更改值時 我們會發現 a 不會更著改動，也就是 b 指向其他的地方了
```python
a = 100
b = a
print('a: ',a,'b: ',b)
print('a: ',id(a),'b: ',id(b))
print('after update')
b = 50
print('a: ',a,'b: ',b)
print('a: ',id(a),'b: ',id(b))
---------------執行結果---------------
a:  100 b:  100
a:  1436754416 b:  1436754416
after update
a:  100 b:  50
a:  1436754416 b:  1436753616
```


那資料結構方面呢? 我們來看看 list:
```python
a = [0,1,2,3]
b = a
print('a: ',a,'b: ',b)
print('a: ',id(a),'b: ',id(b))
print('after update')
b = [1,2]
print('a: ',a,'b: ',b)
print('a: ',id(a),'b: ',id(b))
---------------執行結果---------------
a:  [0, 1, 2, 3] b:  [0, 1, 2, 3]
a:  24584400 b:  24584400
after update
a:  [0, 1, 2, 3] b:  [1, 2]
a:  24584400 b:  24574312
```
恩恩如預期的，b 被指向新的 list 物件。

那如果是 b = a ,後更改裡面的元素呢?
```python
a = [0,1,2,3]
b = a
print('a: ',a,'b: ',b)
print('a: ',id(a),'b: ',id(b))
print('after update')
b[0] = 100
print('a: ',a,'b: ',b)
print('a: ',id(a),'b: ',id(b))
---------------執行結果---------------
a:  [0, 1, 2, 3] b:  [0, 1, 2, 3]
a:  26878160 b:  26878160
after update
a:  [100, 1, 2, 3] b:  [100, 1, 2, 3]
a:  26878160 b:  26878160
```
哇! 沒想到 a 跟著換了，這也驗證了 a  和 b 是指向同一個物件。

關於這方面還有更深入的探討，可以去下面這篇文章:
[談談淺Copy]()

## 心得
Python 不像 C 語言，C 提供具名稱的記憶體儲存空間，一個變數包含了一個資料型態、儲存的值與儲存空間的位址值。
所以 C 每一個變數都是獨立個體，儘管 我們寫 b = a。

## 資料來源:
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)




