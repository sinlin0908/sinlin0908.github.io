---
title: Python 的 字典
date: 2018-01-28 22:06:19
tags: python
categories: 
- python
- 語法學習
---
## 什麼是字典?
字典和 list 類似，不同的是字典不會用[1]、[100]這種 index 來選擇項目。
字典是一個 __***key(鍵)-value(值)***__ 的數據類型，每個 key 都是`獨一無二`。

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}
print(student)

---------------執行結果---------------
{'stud0001': 'Mike', 'stud0003': 'Tom', 'stud0002': 'Jenny', 'stud0004': 'Bob'}

```
<!--more-->
嗯? 怎麼沒有按照順序?
因為字典是`不在乎項目的順序`，不像 list 有[0]、[1]......的順序。

## 字典取值
我們可以用 key 來找 value

方法一: [key]

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

print(student)
print(student['stud0001'])
print(student['stdu0005'])

---------------執行結果---------------
{'stud0001': 'Mike', 'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob'}
Mike

    print(student['stdu0005'])
KeyError: 'stdu0005'
```
因為字典裡面沒有'stdu0005'所以python就會報錯。

方法二: .get(key)

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

print(student)
print(student.get('stud0001'))
print(student.get('stud0005'))

---------------執行結果---------------
{'stud0001': 'Mike', 'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob'}
Mike
None

```
相較於方法一，.get(key)找不到時不會報錯，而是會回傳`None`

如果我們想知道所有 key 有什麼，可以使用 `.keys()`。
```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

print(student.keys())

---------------執行結果---------------
dict_keys(['stud0001', 'stud0002', 'stud0003', 'stud0004'])

```
那全部的 value 呢? 則使用 `.values()`。

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

print(student.values())

---------------執行結果---------------
dict_values(['Mike', 'Jenny', 'Tom', 'Bob'])

```
## 字典輸入
假如又多了一個學生，我們該怎麼加進 student 這個字典呢?
我們可以直接用 __***dict[key] = value***__。
當 key 存在時，舊的 value 會被 新的覆蓋。
當 key 不存在時，會建立一個新的。

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}
print(student)

student['stud0001'] = 'Jake'
student['stud0005'] = 'Lulu'
print(student)

---------------執行結果---------------
{'stud0001': 'Mike', 'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob'}
{'stud0001': 'Jake', 'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob', 'stud0005': 'Lulu'}

```
student因為原本沒有'stud0005'，所以新增了 Lulu。

## 字典刪除
刪除字典的項目有三種方法:
1. del:  Python 內建的通用刪除方法。
> del dict[key]

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

del student['stud0001'] 

print(student)

---------------執行結果---------------
{'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob'}

```
2. dict.pop()
> dict.pop(key)
```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

student.pop('stud0001') # 一定要指定一個key，不指定就會報錯

print(student)
---------------執行結果---------------
{'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob'}

```
3. dict.popitem
> dict.popitem() 沒有key隨機刪除
```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

student.popitem()

print(student)
---------------執行結果---------------
{'stud0001': 'Mike', 'stud0002': 'Jenny', 'stud0003': 'Tom'}
```

## 字典測試
如果不確定 這個 key 是否存在，我們可以使用 `in`。

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

print(student)
print('stud0001' in student)
print('stud0005' in student)

---------------執行結果---------------
{'stud0001': 'Mike', 'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob'}
True
False

```
## 字典 Update

我們可以使用 .update() 來更新我們的字典

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

new_stduent={
    'stud0001':'Jack',
    'stud0005':'Curry',
}

student.update(new_stduent)
print(student)

---------------執行結果---------------
{'stud0001': 'Jack', 'stud0002': 'Jenny', 'stud0003': 'Tom', 'stud0004': 'Bob', 'stud0005': 'Curry'}

```
student、new_student 都有 'stud001' 這個 key，所以 student 原來的 value 就被覆蓋，
而 student 原本沒有 'stud0005' 所以被建立了。

## 字典 print

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

for i in student:
    print(i)
---------------執行結果---------------
stud0001
stud0002
stud0003
stud0004

```
ㄜ......怎麼只有 key，那怎麼 print value?

```python
student ={
    'stud0001':'Mike',
    'stud0002':'Jenny',
    'stud0003':'Tom',
    'stud0004':'Bob',
}

for i in student:
    print(i,student[i])
---------------執行結果---------------
stud0001 Mike
stud0002 Jenny
stud0003 Tom
stud0004 Bob

```

## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)

