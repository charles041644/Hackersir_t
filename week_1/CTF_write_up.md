# CTF_開工
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








