---
title: Python 的 For 迴圈
date: 2018-01-30 15:20:56
tags: python
categories:
- python
- 語法學習
---
上一篇我們談到 `while` ，這篇我們就來談 `for`

我們把 while迴圈 的找偶數的程式碼改成用 `for` 實做
```python
numbers = [1,23,5]

for number in numbers:
    if number % 2 == 0:
        print('Find even number',number)
        break
else:
    print('No even number found')
---------------執行結果---------------
No even number found

```
<!--more-->

## Continue  Break 和 else
跟 while 那篇一樣就不再贅述了

可以參考這篇[Python While迴圈](https://sinlin0908.github.io/2018/01/30/while-py/#more)

## 用 range() 來產生數字序列
在 C 語言要取 array 全部的值時會用以下做法:

```c
for(int i = 0;i<end;i++)
{
    printf(array[i]);
}
```
而 python 則是使用 `range()` 來產生 0 ~ end 的數字
用法是 range(start,stop-1,step)

```python
for index in range(0,len(mylist)):
    print(mylist[index])

```

## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)