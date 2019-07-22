# pwn
## [第一題]
(http://140.110.112.31/challenges#%E5%BC%B5%E5%85%83_Pwn-7)
先弄 IDA 逆向在看裡面內容滿足條件。
```python=
from pwn import *

r=remote("140.110.112.31 2117",2117)

#Stage 1
r.recvuntil('Stage 1\n')
r.sendline(str(0x100001))

#Stage2
r.recvuntil('Stage 2\n')
r.sendline(str(0x64))
r.sendline(str(0x100))
r.sendline(str(0x0FACEB00C))

#Stage3
r.recvuntil('Stage 3\n')
r.sendline(str(0x060107C))

r.interactive()
~                
```
