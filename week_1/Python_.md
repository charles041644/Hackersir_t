# Python自動化樂趣
## 前置步驟_基礎與法(簡略)
- range(起始值,停止值)
- sys.exit:先import sys，用來結數
- def:陳述句
```python=
def hello(name):
    print('hello '+name)
hello('Alice')
hello('Bob')
```
- ramdom.randint(1,9):從1~9隨機存取數值，import ramdom。
- Nope:沒有值意思
- end:不換行
```python=
print('Hello',end='')
print('World')
```
- sep:把空格換成其他的
```python=
print('cat','dogs',sep=',')
```
- 區域名稱不能用在痊癒作用範圍
```python=
def spam():
    eggs=3
spam()
print(eggs)//會出錯
```
- 區域作用不能取用其他區域作用內的變數
```python=
def spam():
    eggs=99
    bacon()
    print(eggs)#會是99
def bacon():
    ham=101
    eggs=0
spam()
```
- 區域作用可以存取全域範圍
- global:直接宣告為全域變數
## 串列使用:'[ ]'
### 索引值
```python=
spam=['cat','bat','elephant']#分別可以用spam[0]=cat、spam[1]=bat
#、而spam[-1]=elephant
```
- len:取得list長度
- list可連接:+、可複製:*
- del:刪除list中的值
- 使用in/not in:可確定某個值是否在串列中
- 多重指定值；
```python=
a,b='Alice','Bob'
print(a)#Alice
print(b)#BOb
```
- index():搜尋串列值
- append(新值):直接插在最後面
- insert(位置值,新值)
- remove():移除
```python=
spam=['cat','bat','elephant']
spam.index('cat')#結果0
spam.append('ant')#['cat', 'bat', 'elephant', 'ant']
spam.insert(1,chicken)#['cat', 'chicken', 'bat', 'elephant', 'ant']
spam.remove('ant')#['cat', 'chicken', 'bat', 'elephant']
```
- sort():小到大排序
    - sort(reverse=True):逆續排列
    - 字串排列會根據ASCII順序排列
    - sort(key=str.lower)
## 多元組使用:()
- 多元組不可修改、刪除、新增
- 使用list()、tuple()轉換型別
```python=
tuple([1,2,3,'dog'])#(1,2,3,'dog')
list('hello')#['h', 'e', 'l', 'l', 'o']
```
### 參照:
```python=
spam=[0,1,2]
ch=spam
ch[1]='hello'
spam#[0,hello,2]
ch#[0,hello,2]複製spam的參照，
#所以修改spam=修改到ch，參照實際使用ID數字數值
```
```python=
def eggs(someParameter):
    someParameter.append('Hello')
spam=[1,2,3]
eggs(spam)
print(spam)#[1, 2, 3, 'Hello']
```
### copy:
```python=
import copy
spam=['A','B','C']
cheese=copy.copy(spam)
cheese[1]=42
spam#['A', 'B', 'C']
cheese#['A', 42, 'C']
```
## 字典
- 字典中項目排序沒有固定
- keys()
- values()
- items()
``` python=
spam={'color':'red','age':42}
for i in spam.values():
    print(i)
for i in spam.keys():
    print(i)
for i,v in spam.items():
    print('key='+ i + ' value= '+ str(v))
```
- get(某個key名稱,如果沒有則噴出該值):
- setdefault():如果某key不存在則設定預設值
### 檢查字元出現次數
```python=
message='q w e r eq w f j n o ew  jf e w a f e wafewf'
count={}
for c in message:
    count.setdefault(c,0)
    count[c]=count[c]+1
print (count)#{'q': 2, ' ': 18, 'w': 6, 'e': 6, 'r': 1, 'f': 5, 'j': 2, 'n': 1, 'o': 1, 'a': 2}
```
- pprint
```python=
import pprint
message='q w e r eq w f j n o ew  jf e w a f e wafewf'
count={}
for c in message:
    count.setdefault(c,0)
    count[c]=count[c]+1
pprint.pprint(count)
'''{' ': 18,
 'a': 2,
 'e': 6,
 'f': 5,
 'j': 2,
 'n': 1,
 'o': 1,
 'q': 2,
 'r': 1,
 'w': 6}'''
```
### 九宮格
```pytohm=
theBoard={'top-L': ' ','top-M': ' ','top-R': ' ',
         'mid-L': ' ','mid-M': ' ','mid-R': ' ',
         'low-L': ' ','low-M': ' ','low-R': ' '}
def printBoard(board):
    print(board['top-L']+'|'+board['top-M']+'|'+board['top-R'])
    print('-+-+-')
    print(board['mid-L']+'|'+board['mid-M']+'|'+board['mid-R'])
    print('-+-+-')
    print(board['low-L']+'|'+board['low-M']+'|'+board['low-R'])
turn ='X'
for i in range(9):
    printBoard(theBoard)
    print('Turn for '+ turn + ' Move on which space?')
    move=input()
    theBoard[move]=turn
    if turn =='X':
        turn='O'
    else:
        turn='X'
        
printBoard(theBoard)
    
```