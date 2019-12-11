---
title: Python 物件
date: 2018-02-12 16:52:30
tags: python
categories:
- python
- 語法學習
---
今天要來看 Python 的物件導向，其實我在大二上的物件導向課的內容都快忘光光了，所以這個篇文章可能不太詳細。

## 什麼是物件
物件裡面有 data (通常為變數，稱為屬性) 與 方法or動作 (通常為 function)，代表一個具體的東西。

其實我覺得很難解釋和表達這個名詞，我是這麼想的，就像我，我是一個人，人一定有身高體重，然後人會走路和跳舞等等的動作，我就是一個物件的概念。身高體重就是 data，動作就是 function。那 class 就是定義人這個名詞，則是比較抽象的。

或者像是 Python 裡面 `String` 這個變數型態就是一個 `class`，而我們創建的字串(`str(96)`)就是一個物件，它的屬性就是字串內容(`'96'`)和 type ，而方法就是它裡面內建的 function。

好吧，有解釋跟沒解釋一樣，等到我比較了解再來更改好了。
<!--more-->

來看 code:
```python
class Person():
    pass

me = Person()
```
我們定義一個 class 叫做 Person，我們用 `me = Person()` 來建立一個 Person 物件叫做 me。

## 把玩物件

我們來實作個，題目為計算 BMI 好了。我們建立一個 `class` 叫做 Human，裡面有身高體重兩個屬性，並且有兩個方法一個是初始化，一個是計算 BMI

首先要有身高體重
```python
class Human():
    def __init__(self,height = 0,weight = 0):
        self.height = height
        self.weight = weight

me = Human(height =180,weight =70)
```
以上 code 就是 class 的定義方式，而比較特別的地方是 `__init__( )` 和 `self` :
1. `__init__( )`: 是特殊的 Python 名稱，是用來初始化一個物件。
2. `self`: 是指他 reference 至自己本身這個物件，就是 self 代表這個物件本身。java, c++ 中的 this 是差不多的東西。

我們來看`me = Human(height =180,weight =70)`這行所作的事情:

* 查看 `Human` class 的定義
* 在記憶體中建立(實體)一個物件
* call 該物件的 `__init__`，並把物件給 `self`。
* 在物件中儲存引數內容
* return 物件，並將 `me` 指定給這個物件

我們定義好身高體重了，接下來是加入 BMI 測量的 function:
```python
class Human():
    def __init__(self,height=0, weight=0):
        self.height = height
        self.weight = weight

    def compute_BMI(self):
        return self.weight/((self.height/100)**2)

def main():
    me = Human('Jack', height=180, weight=70)

    BMI = me.compute_BMI()  # 使用物件裡的 compute_BMI( )
    print(BMI)

if __name__ == '__main__':
    main()
---------------執行結果---------------
21.604938271604937
```

## 繼承
這時我們需要一個叫做 `Woman` 的 class ，裡面包括身高體重、三圍，然後計算 BMI 和 顯示三圍。
依照這個想法我們會這樣寫:

```python
class Woman():
    def __init__(self,height=0, weight=0,bust=0,waist=0,hip=0):
        self.height = height
        self.weight = weight
        self.bust = bust
        self.waist = waist
        self.hip = hip

    def compute_BMI(self):
        return self.weight/((self.height/100)**2)

    def print_BWH(self):
        print('B:{},W:{},H:{}'.format(self.bust,self.waist,self.hip))


def main():
    me = Woman(height=180, weight=70,bust=83,waist=64,hip=83)

    BMI = me.compute_BMI()
    me.print_BWH()
    print(BMI)

if __name__ == '__main__':
    main()

---------------執行結果---------------
B:83,W:64,H:83
21.604938271604937
```

我們會發現有些部分跟 `Human( )`有 87% 像，有些根本就是複製貼上，好像很方便。

不過如果是大程式呢，一次就幾千行程式，這樣複製貼上重複的 code 那不就更多了，在管理程式上是一大的麻煩，而且以後出社會工作並不會一個人幹完整個 project ，一定是團隊合作，如果我們寫出這種 code ，對其他組員來說是一大麻煩，所以我們需要用繼承的方式來減少重複的 code，不要當個雷組員。

```python
class Human():
    def __init__(self,height=0, weight=0):
        self.height = height
        self.weight = weight

    def compute_BMI(self):
        return self.weight/((self.height/100)**2)

class Woman(Human):
    def __init__(self,height=0, weight=0,bust=0,waist=0,hip=0):
        super().__init__(height=height,weight=weight)
        self.bust = bust
        self.waist = waist
        self.hip = hip

    def print_BWH(self):
        print('B:{},W:{},H:{}'.format(self.bust,self.waist,self.hip))
```
在 `Woman`的( ) 裡填上 Human 就繼承了

我們來看經過繼承後的 `Woman( )`:
* 我們使用 `super( )`來 call `Human( )` 的初始化，這樣我們就不用再寫一次一樣的code。
* 我們也不用再寫 `def compute_BMI(self)` 的定義了，因為 `Woman( )` 已經繼承了，就像你爸爸把公司交給你，你不需要再重新打造這個公司，直接接手。

## 覆寫

假如我們有一個 class 叫做 `Human( )` ，而裡面的功能只有 `talk( )` 用來說我是人類。

這時我們有一個 `Woman( )` 繼承 `Human( )`，但是我們想要 `talk( )` 用來輸出我是女人，這件事是可以實現的。只要重新定義就行了。

```python
class Human():
    def talk(self):
        print('I am Human!')

class Woman(Human):
    def talk(self):
        print("I am Woman!")

def main():
    human = Human()
    woman = Woman()

    human.talk()
    woman.talk()

if __name__ == '__main__':
    main()
---------------執行結果---------------
I am Human!
I am Woman!
```

## 私有屬性和方法
為了要讓城市有封裝性，有些語言像是 C++ 會設定 public 和 private 來保護資料，然後需要 get( ) 或 set( ) 來存取。

Python 並不這麼麻煩! 因為所有的屬性和方法都是共用的(public)，但如果不想讓外部存取，我們可以在屬性和方法的命名前加上`__`

那怎麼使用呢?
來實做個，我們有一個 class 叫做 `Duck( )`，他只有一個屬性叫做 `__name` ，這個是我們不希望有人直接存取他，有點像 C++ private 的概念。

```python
class Duck():
    def __init__(self,input_name):
        self.__name = input_name

    def print_name(self):
        print(self.__name)

def main():
    fowl = Duck('Mike')
    print(fowl.__name)  # 印看看 __name

if __name__ == '__main__':
    main()
---------------執行結果---------------
    print(fowl.__name)
AttributeError: 'Duck' object has no attribute '__name'
```
我們成功的不能印出`__name`，但其實並不是把變數變成私有化，而是打亂了他的名稱，如果我們使用 `_Duck__name` 是否能成功 print 出

```python
print(fowl._Duck__name)
---------------執行結果---------------
Mike
```
所以算是變向私有化XD

看完取，我來看看存

```python
def main():
    fowl = Duck('Mike')
    fowl.__name = 'Jojo'
    print(fowl.__name)
---------------執行結果---------------
Jojo
```
咦? 奇怪問什麼 `__name` 被改變了

不急我們用方法 ` print_name( )` 和 `print(fowl._Duck__name)`看看。
```python
def main():
    fowl = Duck('Mike')
    fowl.__name = 'Jojo'
    fowl.print_name()
    print(fowl._Duck__name)
---------------執行結果---------------
Mike
Mike
```
诶? 還是原本的

因為 `Duck` 的 `__name` 在外部叫做 `_Duck__name` 而不是 `__name`，所以 `fowl.__name` 是新的變數。

## Instance method & Class method & Static Method
在之前說到， `self` 為參考自己的物件，是一個實例方法(Instance method)。當我們 call 方法時，Python 會把物件交給 self。

什麼意思?

```python
class Number():
    def __init__(self,input_number):
        self.number = input_number
    def print_number(self):
        print('This is',self.number)

example = Number(10)
example.print_number()
```
`example = Number(10)`
`example.print_number()`
我們可以看成:
`example = Number(10)`
`Number.print_number(example,10)`

在`Number.print_number(example,10)`中，example 所參考的實例會交給 self，讓電腦知道你要用哪一個。
為什麼要這樣?

假如我們今天設置了很多個 `Number( )`的物件卻不使用self會發生什麼事?
```python
class Number():
    def __init__(input_number):
       number = input_number
    def print_number():
        print('This is',input_number)

example = Number(10)
example_2 = Number(50)
example_3 = Number(100)

example.print_number()
example_2.print_number()
example_3.print_number()
---------------執行結果---------------
    example = Number(10)
TypeError: __init__() takes 1 positional argument but 2 were given
```
由於 Python 不知道是誰要使用`__init__( )`所以他報錯了。

那如果我們不要使用`self`來指實例呢?
我們可以用 `@classmethod` 裝飾器(decrator)來說明接下來要使用__***Class method***__。

Class Method 會影響整個 class 也就是說你任何改變，會影響每一個物件。
但是第一個參數是 class 本身，也就是 `self` 改成 `cls`

```python
class Number():
    count = 0   # 計算 object 有幾個
    def __init__(self):
        Number.count += 1
    def talk(self):
        print('I am a Number!!')

    @classmethod
    def print_kids(cls):
        print('Number has',cls.count,'little object')

no1 = Number()
no2 = Number()
no2 = Number()

Number.print_kids()
---------------執行結果---------------
Number has 3 little object
```
但是他會影響其他的 object，有沒有辦法不影響?

我們可以用 __***Static Method***__，以 `staticmethod` 的 decorator 做開頭，不需要 `self` 和 `cls`

```python
class Human():
    @staticmethod
    def talk():
        print('I am a human')


Human.talk()
---------------執行結果---------------
I am a human
```

## 資料來源:
[精通 Python：運用簡單的套件進行現代運算](http://www.books.com.tw/products/0010690075)