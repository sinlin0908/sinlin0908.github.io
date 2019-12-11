---
title: Python 的 if-else
date: 2018-01-30 12:49:15
tags: python
categories:
- python
- 語法學習
---

之前講了一堆資料結構，現在來講判斷式 if-else 怎麼用好了

## If-else 的用法
在 C 語言裡面，if-else的寫法為:
```c
if(a)
{
    printf(a);
}
else if(b)
{
    printf(b);
}
else
{
    printf("None");
}
```
就是有 () 和 {} 所包圍，但是 Python不用，他只有":"
Python 寫久了 C 都會忘記加分號 = =
<!--more-->
```python
if a:
    print(a)
elif:
    print(b)
else:
    print("None")
```
尤其是 else if 的部分， Python 是寫成 `elif`，挺特別的。

## Python 比較、Boolean運算子
與 C 語言做個比較:

| 運算子 | Pthon |                    C                    |
| :----: | :---: | :-------------------------------------: |
|  相等  |  ==   |                   ==                    |
| 不相等 |  !=   |                   !=                    |
| 大小於 |  > <  |                   ><                    |
|  and   |  and  |                   &&                    |
|   or   |  or   | 兩條直槓 (好像會被md當作表格，無法表示) |
|  not   |  not  |                    !                    |
|  NULL  | None  |                  NULL                   |

Python 什麼時候會顯示 `false`:
1. None
2. '' 空字串
3. [] 空list
4. {} 空dict
等等

## If-else 慣用語
Python 有一些 官方比較建議的用法
1. 不要與 True 和 False 做比較:
X 錯誤!!!!:
```python
if a == True:
    print('true')
if b == False:
    print('false')
```
    O 正確!!:
```python
if a:
    print('true')
if not b:
    print('false')
```
2. strings、lists、 tuples 等等的資料結構，當空的時候就是 `false` 所以不用判斷長度為0:
X 錯誤!!!!:
```python
if len(data) == 0:
    print('empty!')
```
    O 正確!!:
```python
if not data:
    print('empty!')
```
3. 和 `None` 比較要使用 `is` 和 `is not`:
X 錯誤!!!!:
```python
if a == None:
    print('None!')
```
    O 正確!!:
```python
if a is None:
    print('None!')
```
4. 善用 `in` :
有時候我們的 data 有可能要和很多東西做比較，會寫成這樣
X 錯誤!!!
```python
if name == 'Mike' or name == 'Jenny' or name == 'Lulu':
    print('yes')
```
    看起來就很醜= =
    不如試試用 `in` 加上 `tuple`
    O 正確!!:
```python
if name in ('Mike','Jenny','Lulu'):
    print('yes')
```
## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)
[Python 慣用語](http://seanlin.logdown.com/)




