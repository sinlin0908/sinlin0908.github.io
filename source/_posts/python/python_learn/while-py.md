---
title: Python While迴圈
date: 2018-01-30 14:18:40
tags: python
categories: 
- python
- 語法學習
---
我們這次來看 `while` 迴圈吧 !!

## While 迴圈怎麼寫?
```python
count = 0
while count <= 5:
    print(count)
    count+=1
---------------執行結果---------------
0
1
2
3
4
5

```
只要 while 為 True，就會一直執行不會中斷，等到 count <= 5 為 False 就會停止。
<!--more-->

## 用 Break 來中斷 While
如果我們希望 while 在某個情況下終止並跳出，但不知道何時發生，我們可以使用 `break`。

下面為無限迴圈，要求 user input 一個字並 print， user input q 時則跳出迴圈:

```python
while True:
    word = input("Please input a word [type q to quit]: ")
    if(word == 'q'):
        print('Break While loop!!')
        break
    print(word)
---------------執行結果---------------
Please input a word [type q to quit]: hello
hello
Please input a word [type q to quit]: 123
123
Please input a word [type q to quit]: q
Break While loop!!
```
## 使用 Continue
當我們用到某些狀況想要跳過，但是又不想跳出迴圈時，我們可以使用 `continue`。

以下程式為輸入數字，奇數print，偶數就跳過:

```python
while True:
    value = input("Please input a number [type q to quit]: ")
    if(value == 'q'):
        print('Break While loop!!')
        break
    number = int(value)

    if number % 2 == 0:
        print('Continue!!')
        continue

    print(number)
---------------執行結果---------------
Please input a number [type q to quit]: 12
Continue!
Please input a number [type q to quit]: 11
11
Please input a number [type q to quit]: q
Break While loop!!

```
## 使用 else 來檢查中斷
當我們使用 while 迴圈尋找一樣東西，找到並跳出迴圈;如果沒找到就印出訊息，就可以使用這個方法。
while 迴圈正常結束( 沒有 call `break` )，會把控制權給 `else`。

```python
numbers = [1,23,5]

index = 0
while index < len(numbers):
    number = numbers[index]
    if number % 2 == 0:
        print('Find even number',number)
        break
    index += 1
else:
    print('No even number found')  # break cannot run
---------------執行結果---------------
No even number found

```
由於 list 沒有偶數，所以 while 不會執行 `break`，所以跑完後直接到 else。


## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)