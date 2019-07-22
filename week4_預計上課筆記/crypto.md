# crypto
[台灣好厲駭](https://hackmd.io/a42SAsXjRdmIDSsT1TQQgg?view)
### 第一題 [crypto XORmagic](http://140.110.112.30/challenges#xor-magic)
安裝 XORtool 然後打指令 使用工具
![](https://i.imgur.com/ZipwXNX.png)

### 第二題 [AES](https://id0-rsa.pub/problem/26/)

```

m1:"Deposit amount: "
c1:5797791557579e322e619f12b0ccdee8
m2:"One million doll"
c2:b1e952572d6b8e00b626be86552376e2
m3:"ars"
c3:fdf526bd557b045bce65a3b3e300b55e

答案:

5797791557579e322e619f12b0ccdee8b1e952572d6b8e00b626be86552376e2fdf526bd557b045bce65a3b3e300b55e
```

### 第三題 [BABYRSA](http://140.110.112.30/challenges#babyRSA)
![](https://i.imgur.com/dlycwuE.png)

```python=
from Crypto.PublicKey import RSA
import gmpy2
from Crypto.Util.number import *

key = RSA.importKey(open("pub.pem", "rb").read())

e = key.e
n = key.n
phi_n=( 270613060120468613971049355250995010949-1)*( 317961772531370599800029965079161987889-1)

d = int(gmpy2.invert(e, phi_n))
c = open("flag.enc","rb").read()

c = bytes_to_long(c)


m = pow(c,d,n)
print (long_to_bytes(m))
#print(e)
#print(n)

```

### 第四題 [RSA_1](http://140.110.112.30/challenges#YANG_RSA-1)
```python=
q = 3006300461
r = 12218233223644524650141958853163065112163255395621655741865064529020634406575730714768264558014607893896434523845321502371618344594488810317052606914954669
n = 83092583783534841000145280642003842283533340442637642451258941907393275732996256523893438356692786223410880194199043046345864683398238392329295750150314289824255749149834103
e = 11
c = 32392151763267291269610586564983347951891395196084251182633225594245167922176424232164117237142038355860036871811244158149537196288428230971760474130300660929743492107190512

phi = (p-1)*(q-1)*(r-1)
d = int(gmpy2.invert(e, phi))
m = pow(c,d,n)
print(long_to_bytes(m))
```