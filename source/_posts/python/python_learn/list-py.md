---
title: Python 的 list
date: 2018-01-23 20:51:52
tags: python
categories: 
- python
- 語法學習
---

## 為什麼要用到 list ?

  舉個例子:
```python
 names = 'Rogers Stark Thor Loki Natasha'
```
<!--more-->

雖然 names 可以存取人名，但是如果要增加或者存取其中一個人的名字就GG。

所以我們使用 list 來存取這些人名，list在python是以[]來表示的。

而且list內容是__***可以更改的***__，像是排序、加入、刪除等等。

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
```

## 取得 list 的值

這時我想要得到Jenny，該怎麼取呢？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

print(names[4])

---------執行結果-------

Jenny


```
等等Jenny不是在第五個嗎？怎麼會是names[4]？
這是因為電腦存數據時，__***不是從1開始算的,是從0開始算起的***__，所以Jenny是在第四個。
我們可以使用[index]來取出list的值囉，跟C語言的array類似。

那...能不能一次把 'Tim'和'Amy'取出來？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
print(names[2:3])

---------執行結果---------

['Tim']
   
```
奇怪？[2:3] 不是2~3的意思嗎？怎麼只有Tim一個人？

哦~~原來我用法錯誤！！
正確是這樣

> [Start:End-1] 
> end是要減1的
> 使用[Start:End-1] return 是一個 list 喔！


如果我不知道list有幾個，但我想取出最後一個怎麼辦？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
print(names[-1])

---------執行結果---------
Jenny

```

所以正的(包含0)就是從左到右取值，負的就是從右到左取值，所以倒數第二個就是names[-2]


那這樣取全部是不是這樣？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
print(names[0:-1])


---------執行結果---------
['Mike', 'John', 'Tim', 'Amy']


```
拉雞！又不對，阿！我忘了是__*** 使用[Start:End-1]***__

所以應該是names[0:0]，但這個很鳥欸 = =

有個更牛逼的方法，就是如果你要頭跟尾就空白。

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

print(names[:2]) # 第0個到第1個
print(names[1:]) # 第1個到最後1個
print(names[:])  # 全部

---------執行結果---------

['Mike', 'John']
['John', 'Tim', 'Amy', 'Jenny']
['Mike', 'John', 'Tim', 'Amy', 'Jenny']

```

棒！果然如預期！

## 加入元素

喔喔 突然要加一個人，要怎麼加呢？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
names.append("Curry")
    
print("After append() ",names)

---------執行結果---------
['Mike', 'John', 'Tim', 'Amy', 'Jenny','Curry']


```
`append()`是list內建function功能是加進list的`尾端`

但是我想加到list的任何位置怎麼辦？

```python

names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
names.insert(1,"insert1_Jack")
names.insert(3,'insert3_Tom')

---------執行結果---------
['Mike', 'insert1_Jack', 'John', 'insert3_Tom', 'Tim', 'Amy', 'Jenny']

```
原本在[1]的'John'被往後移一格了，'Tim'也是，代表`insert()`不會取代原來的元素。

## 串接list

要把一個list接在令一個list要怎麼用呢？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
others = ['Tom','Curry']

names.append(others)
print(names)

---------執行結果---------
['Mike', 'John', 'Tim', 'Amy', 'Jenny', ['Tom', 'Curry']]


```
好像不是這樣弄呢...others被當成一個項目加尾端了

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
others = ['Tom','Curry']
names.extend(others)
print(names)

---------執行結果---------
['Mike', 'John', 'Tim', 'Amy', 'Jenny', 'Tom', 'Curry']

```

喔喔使用`extend()`救解決了這個問題

## 取代

那如果names第二個要改成Faker要怎麼取代呢？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']
names[1] = 'Faker'
print(names)

---------執行結果---------
['Mike', 'Faker', 'Tim', 'Amy', 'Jenny']

```
有了John被改成我們要的Faker了 

## 刪除

那怎麼刪除人名呢？
有三種方法，我們來刪除Amy。

```python

names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

# 三種方法delete

# 1. names.remove("Amy")
# 2. del names[3]
# 3. names.pop(3)

names.pop(3)   #使用pop()
print(names)

---------執行結果---------
['Mike', 'John', 'Tim', 'Jenny']

```
1. remove():
	如果不確定該項目的index，就可以使用 `remove(value)` 的方式來刪除。
2. del:
	del 是python 的陳述式，__***並不是list內建的 function***__，如果要刪除的項目是最後一個，del會釋出list物件的記憶體。
3. pop():
	使用該項目的index做移除，如果沒有index，default為-1。


## 尋找index

如果我想知道 Jenny的index是多少該怎麼辦呢？
我們可以這樣寫:

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']


print(names.index('Jenny'))

---------執行結果---------
4
```
恩！Jenny真的在[4]。


## 複製

我們想要複製一個list

首先來看 " = " 指派的方法：

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

new = names
print(names)
print(new)

---------執行結果---------
['Mike', 'John', 'Tim', 'Amy', 'Jenny']
['Mike', 'John', 'Tim', 'Amy', 'Jenny']

```
嗯嗯 如我們預期 new 的值跟 names 一樣。

如果我們更改 names 的值，new 會是如何？

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

new = names

names[0] = 'Faker'

print(names)
print(new)

---------執行結果---------
['Faker', 'John', 'Tim', 'Amy', 'Jenny']
['Faker', 'John', 'Tim', 'Amy', 'Jenny']

```

奇怪！我們只是更動了 names，結果 new 也更著改動了。

> 原因是 用 " = " new 只是 reference names同樣的list ，
> 所以 new 和 names 是用同一個list。
我們看以下 code，new 和 names 的address

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

new = names
print("names: ",id(names))
print("new: ",id(new))

---------執行結果---------
names:  140348091144264
new:  140348091144264

```
是一樣的！

> C 語言中 variable 是一個名稱並賦予一個 memmory address
> Python 卻是一個指向某個address 的 pointer

> 下圖為 Python variable 概念圖
![](/images/python/reference.png)



那怎麼獲得一個獨立的list?
有三種方式
1. .copy()
2. list()轉換
3. slice[:]

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny']

new1 = names.copy()
new2 = list(names)
new3 = names[:]

names[0] = 'Faker'

print(names)
print(new1)
print(new2)
print(new3)

---------執行結果---------
['Faker', 'John', 'Tim', 'Amy', 'Jenny']
['Mike', 'John', 'Tim', 'Amy', 'Jenny']
['Mike', 'John', 'Tim', 'Amy', 'Jenny']
['Mike', 'John', 'Tim', 'Amy', 'Jenny']

```
大功告成！

如果list中再加入一個list看看......

```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny',['GGG','zzz']]
new = names.copy()

names[5][0] = 'Love'
new[0] = 'Jake'

print(names)
print(new)

---------執行結果---------
['Mike', 'John', 'Tim', 'Amy', 'Jenny', ['Love', 'zzz']]
['Jake', 'John', 'Tim', 'Amy', 'Jenny', ['Love', 'zzz']]

```
奇怪? new 的第二層list怎麼跟著改變了，'GGG'也變成'Love'。
這個叫做 `shallow copy`，所謂的 `shallow copy` 就是只複製記憶體裡位置第一層的列表，而第二層還是有個指標指著同一個object。如下圖:
![](/images/python/shallow_copy.png)
所以當 names 更改第二層 list ，new 也會跟著更改。

我們來看是不是這樣:
```python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny',['GGG','zzz']]
new = names.copy()

# 更改 第一個元素
names[0]= 'xxxx'

print(id(names[0]))
print(id(new[0]))

#更改第二層 list
names[5][0] = 'love'
print(id(names[5]))
print(id(new[5]))

---------執行結果---------
24274016
19899808

24282136
24282136
```
真的是如此。
>喔對了! 我發現，當我還沒更改 names[0]時，兩者第一個元素的 id 是一樣，可見 Python 等到更改時，才生一個新的address 給 new[0]。

那怎麼 copy 整份 list 呢?
我們可以使用 `deep copy`， import copy 模組。

```python
import copy

names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny',['GGG','zzz'],'gogoro']

new = copy.deepcopy(names)

print(names)
print(new)

print('---- 更改後 -----')

names[5][0] = 'Love'
new[0] = 'Lala'

print(names)
print(new)
---------執行結果---------
['Mike', 'John', 'Tim', 'Amy', 'Jenny', ['GGG', 'zzz'], 'gogoro']
['Mike', 'John', 'Tim', 'Amy', 'Jenny', ['GGG', 'zzz'], 'gogoro']
---- 更改後 -----
['Mike', 'John', 'Tim', 'Amy', 'Jenny', ['Love', 'zzz'], 'gogoro']
['Lala', 'John', 'Tim', 'Amy', 'Jenny', ['GGG', 'zzz'], 'gogoro']
```
完成了!!
但大多數情況下，不需要獨立複製一份，如果當列表夠大時，做了deepcoy()會很占記憶體空間。

## 排序
Python 排序的是由小到大。
Python 提供兩個 function 供我們做排序:
1. sort(): 是 list function， 會就地排序 list 本身，也就是會更改原本的 list。
2. sorted(): 是通用 function ，會排序list，並 return copy list，不更改原來的 list。

```Python
names = ['Mike', 'John', 'Tim', 'Amy', 'Jenny','gogoro']
print('--- sort() ----')
names.sort()
print(names)

print('--- sorted() ---')
names2 = ['Mike', 'John', 'Tim', 'Amy', 'Jenny','gogoro']
new = sorted(names2)
print(names2)
print(new)
---------執行結果---------
--- sort() ----
['Amy', 'Jenny', 'John', 'Mike', 'Tim', 'gogoro']
--- sorted() ---
['Mike', 'John', 'Tim', 'Amy', 'Jenny', 'gogoro']
['Amy', 'Jenny', 'John', 'Mike', 'Tim', 'gogoro']

```



呼~~~ 終於結束了

## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)