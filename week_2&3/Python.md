# Python自動化樂趣
# WEEK_1
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
# WEEK_2
## 字串的操作 WEEK_1
- 原始字串使用r:
```python=
print(r'That is Charles\'s Cat')
```
- upper():大寫
- lower():小寫
- is字串檢測系列
    - isalpha()
    - isalnum()
    - isdecimal()
    - isspace()
    - istitle()
```python=
while True:
    print('Plz Enter Ur age ')
    age=input()
    if age.isdecimal():#檢測不是空的
        break
    print('plz enter a number for Ur age')
while True:
    print('select a new password(letter and numbers only)')
    password=input()
    if password.isalnum():# 檢測只有字母與數字
        break
    print('Password can only have letters and numbers')
```
- startswith():檢測字串起始字元
- endswith():檢測結束字元
- join():
```python=
', '.join(['cat', 'rat', 'bats'])#'cat, rat, bats'
```
- split():

```python=
'cat rat bats'.split('a')#['c', 't r', 't b', 'ts']
```
- rjust()
```python=
'Hello'.rjust(20, '*')
```
- ljust()
```python=
'Hello'.ljust(20, '*')
```
- center
```python=
'Hello'.center(20,'=')
```
### 應用:
```python=
def printPicnic(itemDict,LWidth,RWidth):
    print('PINIC ITEMS'.center(LWidth + RWidth , '-'))
    for i,j in itemDict.items():
            print(i.ljust(LWidth, '.')+ str(j).rjust(RWidth))
printItems={'sandwiches':4,'apples':5,'cups':1,'cookies':4}
printPicnic(printItems,12,5)
printPicnic(printItems,20,6)
```
- strip():刪除空白
    - rstrip()
    - lstrip()
- pyperclip:模組複製貼上
### sys:很神奇很玄的東西

## 正規表示式進行模式比對
- re.compile():
- group()
```python=
import re
phone_number=re.compile(r'(\d\d\d\d)-(\d\d\d\d\d\d)')
mo=phone_number.search('My number is 0988-058238.')
mo.group(1)
```

### 問號可作為可選擇性的比對:

```python=
batRegex=re.compile(r'Bat(wo)?man')
mo1=batRegex.search("Batman")
mo1.group()
```
### 使用星號比對符合零次或多次
```python=
batRegex=re.compile(r'Bat(wo)*man')
mo1=batRegex.search("Batwowowowowoman")
mo1.group()
```
### 使用大括號比對符合次數:
```python=
Regex=re.compile(r'(Ha){3}')
mo1=Regex.search("HaHaHa")
mo1.group()
```
### 使用加號比對符合一次或多次
### 貪婪與非貪婪比對
- 貪婪:盡可能找到最長符合的比對字串
```python=
Regex=re.compile(r'(Ha){3,5}')
mo1=Regex.search("HaHaHaHaHa")
mo1.group()
```
- 非貪婪:找到最短，大括號後面+上?

```python=
Regex=re.compile(r'(Ha){3,5}?')
mo1=Regex.search("HaHaHaHaHa")
mo1.group()
```
### findall():返回多個符合比對的東西
### 字元分類
- \d:0~9
- \D:0~9以外
- \w:任意字母數字底線字元
- \W:除了字母數字底線字元
- \s:空格、定位符號、換行符號(比對空白字元
- \S:除了空格、定位符號、換行符號
- [0-5]:比對0~5

```python=
Regex=re.compile(r'\d+\s\w+')
Regex.findall('12 dwefdewdf,11 qde,23 eqwdew')
```
### ^ :[^abc]在裡面使用，取得相反的字元分類
### ^:開頭是 ^條件後的開頭
### $:結尾處前符合條件
### . :萬用字元
### .*:比對尋找所有字元
- re.I:比對時不區分大小寫
- sub():
- 組合使用re.IGNORECASE、re.DOTALL、re.VERBOSE:使用 | 在re,compile("abc",re.DOTALL|re.IGNORECASE)

### 可實作:email、電話號碼

## 讀寫檔案
- 使用 os.path.join建立目錄
```python=
import os
myfile=['account.txt','detail.csv','invite.docx']
for file in myfile:
    print(os.path.join('D:\\User\\asweigart',file))
```
- os.getcwd()、os.chdir():查看工作目錄
- os.makedirs():建立新資料夾
- os.path.abspath():相對轉絕對路徑
- os.path.split():分成目錄名稱、基本名稱
### 找出檔案大小與file內容
- os.path.getsize(path):檔案大小位元數
- os.listdir(path):返回檔案名稱串列
- os.path.exits(path):檢查檔案與資料夾存在
- os.path.isfile(path):路徑存在且是檔案
- os.path.isdir(path):路徑存在且是資料夾
### 使用open()函式開啟檔案
### 使用read()讀取
- readlines():從檔案取得字串的串列

### 寫檔案
```python=
baconfile=open('bacon.txt','w')
baconfile.write('hello word\n')
baconfile.close()

baconfile=open('bacon.txt','a')
baconfile.write('bacon is not a vegetable')
baconfile.close()

baconfile=open('bacon.txt')
content=baconfile.read()
baconfile.close()

print(content)
```
### 使用shelve儲存變數:可將變數儲存二進位
```python=
import shelve
shelvefile=shelve.open('mydata')
cats=['a','b','c']
shelvefile['cats']= cats
shelvefile.close()

shelvefile=shelve.open('mydata')
type(shelvefile)

shelvefile['cats']

shelvefile=shelve.open('mydata')

list(shelvefile.keys())
==>['cats']
list(shelvefile.values())
==>[['a', 'b', 'c']]
```
# WEEK_3
##  檔案組織管理
### shutil模組
- 檔案與資料夾複製
```python=
import shutil,os
os.chdir('C:\\')
shutil.copy('C:\\spam.txt','C:\\delicious')
```

- 檔案和資料夾 搬移與改名
```python=
import shutil
sutil.move('C:\\bacon.txt','C:\\eggs')#搬移過去到eggs底下
sutil.move('C:\\bacon.txt','C:\\eggs\\new_bacon.txt')#改變bacon的名稱
```
- 永久刪除檔案和資料夾
	- os.unlink(path)刪除檔案
	- os.redir(path)資料夾必須是空的
	- os.rmtree(path)
- 刪除txt檔案
```python=
import os
for filename in os.listdir('C:\\'):
    if filename.endswith('.txt'):
        print(filename)
        #os.unlink(filename) 用於刪除檔案
```
### send2trash
- 送入資源回收桶
```python=
import send2trsh
file=open('spam.txt','a')#creates the file
file.write("12334")
file.colse()
send2trash.send2trash('spam.txt')
```