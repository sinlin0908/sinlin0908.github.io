---
title: Python 的 Function
date: 2018-01-30 17:16:05
tags: python
categories: 
- python
- 語法學習
---
## Function 定義
在 Python function 以 `def`來定義

```python
def printHello(name = 'Bob'):
    """如果是Jack 印出 hello world"""
    if name == 'Jack':
        print('hello world!')
    else:
        print('who are you?')
    return 0

printHello()
printHello('Jenny')
printHello('Jack')
---------------執行結果---------------
who are you?
who are you?
hello world!

```
<!--more-->
來說說以上 code 吧!
1. `def` 是定義 function 的關鍵字
2. printHello 是 function name
3. (name): name 是 參數
4. name = 'Bob' 是預設參數
5. """ """ 是說明 function 用途跟用法
6. return 回傳值，不寫為 None

##  關於參數預設值

我們可以使用預設值來方便操作，但是它有個問題。
def 是個陳述，所以執行到 def 陳述時，就建立了該陳述相關的資源。
什麼意思?
看例子

```python
def buggy(arg,result =[]):
    result.append(arg)
    return result
    
print(buggy('a'))

print(buggy('b'))
---------------執行結果---------------
['a']  --> 相當正常
['a', 'b'] ---> ?????????
```
奇怪? 當我們第二次使用時，卻不是 ['b']!!
這是因為電腦從 code 上至下執行，當執行到`def buggy(arg,result =[]):`這行時，已經把 list 建好了。
就像之前說的，因為 def 是陳述句所以會先建立。
有點類似 C 語言會先宣告function，當使用到時再來定義。

那怎麼辦?
不要把可變資料型態(list,dict,tuple,set)當預設值!
```python
def buggy(arg):
    result = []
    result.append(arg)
    return result
    
print(buggy('a'))
print(buggy('b'))
---------------執行結果---------------
['a']
['b']

```
大功告成 XD

## 參數值使用 *
在 C C++ 裡 \* 表示 pointer ，但 Python 卻不是喔!
那是什麼?
如果你在參數中加入 \* ，他會把你傳到 function 的資料集合起來，變成一個 `Tuple` 型態。

```python
def printArgs(*arg):
    print(arg)
    
printArgs('apple','google','android','asus')
---------------執行結果---------------
('apple', 'google', 'android', 'asus')

```

也就是一個參數可以包含很多 data。

## 參數值使用 **
我們如果要把參數弄成 `dict` 型態呢?
我們使用 `**`

```python
def printKwargs(**kwarg):
    print('keyword argument:',kwarg)
    
printKwargs(Id = '6666',name = 'Bob',age = '18')
---------------執行結果---------------
keyword argument: {'Id': '6666', 'name': 'Bob', 'age': '18'}

```
## Function 當參數?
在 Python 的世界裡面所有東西都是一個 `Object`。
因此，你可以把 function 傳給一個 variable，把他們當作參數傳給另一個 function。

```python
def print_hundred():
    """ 只 print 100  """
    print('100')

def do_something(fun):
    fun()

if __name__ == '__main__':
    do_something(print_hundred)
---------------執行結果---------------
100

```
{%note warning %} 我們當參數傳入的是 'print_hundred'，而不是 'print_hundred( )'!! ( ) 代表 call 這個 function!! {% endnote %}

## Local Function
這個我覺得挺牛逼的XD
就是 function 裡面還可以加一個小 function 來使整個演算法更有組織，不用再而外寫一個小 function。

```python
def student(saying):
    def inner():
        return "We are the students who say:'{q}'".format(q =saying)

    return inner()
    
if __name__ == '__main__':
    print(student('hello world!'))

---------------執行結果---------------
We are the students who say:'hello world!'

```
Local function 可以使用主要 function 的資源

## lambda function
有些小 function 而外寫他有點浪費時間，所以我們可以使用 lambda 來取代。

例子: 
我們需要輸入一串水果名稱，並將其第一個字母大寫且尾巴加上驚嘆號

改良前:
```python
def print_fruit(fruits,fuc):
    for _fruit in fruits:
        print(fuc(_fruit))

def celebrate(fruit):
    return fruit.capitalize() + '!'

if __name__ == '__main__':
    fruits = ['apple','banana','orange','lemon']
    print_fruit(fruits,celebrate)
---------------執行結果---------------
Apple!
Banana!
Orange!
Lemon!
```
使用 lambda:
```python
def print_fruit(fruits,fuc):
    for _fruit in fruits:
        print(fuc(_fruit))

if __name__ == '__main__':
    fruits = ['apple','banana','orange','lemon']
    print_fruit(fruits, lambda fruit: fruit.capitalize() + '!')
---------------執行結果---------------
Apple!
Banana!
Orange!
Lemon!
```




## 資料來源:
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)






