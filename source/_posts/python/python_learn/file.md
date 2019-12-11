---
title: Python 檔案處理
date: 2018-02-10 17:06:53
tags: python
categories:
- python
- 語法學習
---
這篇我們來看看檔案的處理

## Open & close

我們要做檔案讀寫時，一定要相進行開啟檔案，我們使用 `open()`
>fileobj = open(filename,mode='r',encoding=None)
1. fileobj : 是接 open( ) return 的檔案物件
2. mode: 來指定檔案權限
3. encoding: 編碼
<!--more-->

以下是 mode 的 表示:

| mode type |                              意義                              |
| :-------: | :------------------------------------------------------------: |
|    `r`    |                           read only                            |
|    `w`    | write only，如果 file 不存在會產生一個新的。如果存在會從頭寫入 |
|    `x`    |           只能用在檔案不存在的時候，新建檔案並且寫入           |
|    `a`    |               如果檔案存在，從檔案尾端(EOF)寫入                |
|    `+`    |              如果是read可以write，是write可以read              |


使用完檔案之後要記得 `close( )`，將檔案關閉以節省資源。

如果忘記寫，當 function 結束時 Python 也會自己關掉，但還是不安全，如果在使用檔案的過程中發生了一些例外狀況，造成程式提早跳開時，這個開啟的檔案就會沒有被關閉。

所以我們可以使用 `with` 來幫忙我們。

```python
with open('poem') as file:
    file.write(data)
```
這樣就行了，方便很多。

## Write
使用 `write( )` 前 `open( )` 要有 `w` 的權限。
>bytes = file.write(data)

`write( )` 會 return 被寫入的 byte 數。但它跟 `print( )` 不一樣，他不會 自動在尾端加入`\n`。

我們也可以使用 `print( )` 來寫入到 file，只要在 file 裡給予目標檔案即可。
> print(data,file = myfile)

我們來實做一下，我們把詩經裡的<關鴡>寫入 poem 這個檔案。

```python
file = open('poem',mode='w',encoding='utf-8')

poem = '''關關雎鳩，在河之洲。窈窕淑女，君子好逑。

參差荇菜，左右流之。窈窕淑女，寤寐求之。

求之不得，寤寐思服。悠哉悠哉，輾轉反側。

參差荇菜，左右采之。窈窕淑女，琴瑟友之。

參差荇菜，左右芼之。窈窕淑女，鐘鼓樂之。'''

file.write(poem)

file.close()
```
結果:
![](/images/python/write.JPG)

## read() readline() readlines()

要使用 `read( )`，`open( )`， 要有 `r` 的權限。
> data = file.read(size)

`read( )`  return 他讀到的檔案內容， `size`是讀取檔案大小的上限，如果不寫的話是整份資料都讀取，如果檔案太大，那記憶體會哭的XD

我們來實做讀取剛剛的poem，但我們設置一次只能讀 10 個字元
```python
file = open('poem',mode='r',encoding='utf8')

MAX_READ = 10
poem = ''

while True:
    data = file.read(MAX_READ)
    if not data:
        break
    print('data',data)
    poem += data

print('--------- poem --------')
print(poem)
file.close()
```
結果:
![](/images/python/read.JPG)

當 `read( )` 沒讀到檔案時，會回傳 `''` 空字串，所以 `if not data` 會是 `True`。

我們也可以使用 `readline( )`一次讀入一行，什麼叫做一行? 就是讀到 `'\n'` 或者 EOF 就停止。跟 `read( )`一樣，沒讀到東西會 return 一個空字串。

```python
file = open('poem',mode='r',encoding='utf8')

poem = ''

while True:
    line = file.readline()
    if not line:
        break
    print('line',line)
    poem += line

print('--------- poem --------')
print(poem)
file.close()
```
結果
![](/images/python/readline.JPG)

每次讀一行都需要寫這個多 code，有沒有以較方便的方法呢?
我們可以使用 `readlines( )`， 他是把每一行都存入一個字串的 list(包括 `\n`)，所以我們就可以使用 for 來迭代。

我們 print `readlines( )`的結果出來。

![](/images/python/readlines.JPG)

## tell() & seek()
我們在做讀寫時， Python 都會追蹤我們在的檔案位置。 `tell()` 會從檔案的開頭起，return 你的位移值。
`seek( )`則是移動你的位移值到你想要的地方。

## 資料來源:
[Python 學習筆記 系列](https://ithelp.ithome.com.tw/users/20069378/ironman/1113)




