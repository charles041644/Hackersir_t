# Web_筆記

### [DVWA_玩具](http://43.247.91.228:81/vulnerabilities/exec/#)
### [Nmap_掃port](https://nmap.org/)
### dirsearch
- [github_載點](https://github.com/maurosoria/dirsearch)
- 自動化掃描工具
- 侵略性掃描
### Sublist3r
- [github_載點](https://github.com/aboul3la/Sublist3r)
## 一、網路如何運行
- 瀏覽器請求伺服器
    - Http request
    - Http response


### Http method
- Get
    - 向伺服器請求資源 
- Post
    - 送訊息給伺服器


### Http Status
- 2XX:成功
- 3XX:重新導向
- 4XX:用戶端錯誤
- 5XX:伺服器端錯誤

## 二、GoogleHacking

## 三、GitHack漏洞
- 安裝
    - https://github.com/lijiejie/GitHack

![](https://i.imgur.com/xmkQt7p.png)

## 四、Local File Inclusion
- 網址上加上page=../flag回上一層，找尋Flag
- ../為相對路徑
- 雜技
    - ../../etc/password%00 

- 偽協議php://fiter/read/convert.base64-encode/resource=file.php

## 五、SQL injection
- 萬能鑰匙'or 1=1 #
- 雜技
    - 'or 1=1--  select 
    - ' /*!or*/ 1=1 #
![](https://i.imgur.com/tzqdncV.png)




## 六、XSS
### Reflected XSS
- 常以URL形式 使 使用者受害
    - url 後加上 <script>alert(document.cookie)</script>

### Stored XSS
- Sever端 把使用者輸入的惡意代碼 存入資料庫中
### DOM-base XSS
![](https://i.imgur.com/phLcudG.png)


