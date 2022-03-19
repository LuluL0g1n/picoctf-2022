# basic-mod1
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158553868-baec7504-86f0-4490-a630-1761b5939667.png)

>Hint 1: Do you know what mod 37 means? 

>Hint 2: mod 37 means modulo 37. It gives the remainder of a number after being divided by 37.

[message (1).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8260412/message.1.txt)
## Cách giải
Với gợi ý của đề bài là mod 37, ta đưa toàn bộ các số của message thông qua module 37, ta được dãy số sau: [17,26,20,13,3,36,13,36,17,26,20,13,3,36,2,26,0,34,32,31,33,33]

Yêu cầu của đề bài là với những số từ 0-25 là chữ cái viết hoa, 26-35 là các số từ 0-9, và 36 là số gạch dưới, không còn gì khó khăn:
```py
import string
c = [54,211,168,309,262,110,272,73,54,137,131,383,188,332,39,396,370,182,328,327,366,70]
for i in c:
    print(i%37,end = ' ')
g = string.ascii_uppercase + string.digits+ "_"
d = [17,26,20,13,3,36,13,36,17,26,20,13,3,36,2,26,0,34,32,31,33,33]
for j in d:
    print(g[j],end='')
```
> Flag: picoCTF{R0UND_N_R0UND_C0A86577}
# basic-mod2
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158555425-75fcda90-722d-4ccd-a05d-259d04fb6d9b.png)

[message (2).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8260491/message.2.txt)

>Hint 1: Do you know what the modular inverse is?

>Hint 2: The inverse modulo z of x is the number, y that when multiplied by x is 1 modulo z

>Hint 3: It's recommended to use a tool to find the modular inverses
## Cách giải
Trước tiên, ta tìm dãy số mới của message khi qua module 41 :[22,3,28,26,16,9,26,24,23,10,36,4,16,31,10,17,5,22,14,21,9,26,38]

Hint cho ta biết ta phải tìm nghịch đảo modul của các số trên thông qua modulo 41. Ta lại có dãy số mới:[28,14,22,30,18,32,30,12,25,37,8,31,18,4,37,29,33,28,3,2,32,30,27]
```py
d = [22,3,28,26,16,9,26,24,23,10,36,4,16,31,10,17,5,22,14,21,9,26,38]
for j in d:
    print(pow(j,-1,41),end=',')
```

Đến đây ta làm y như bài basic-mod1. Tuy nhiên có 1 chút khác biệt. Ở bài 1 thì 0-25 là các chữ cái, nhưng ở đây là 1-26, cho nên ta phải làm khác 1 chút
```py
d = [28,14,22,30,18,32,30,12,25,37,8,31,18,4,37,29,33,28,3,2,32,30,27]
for j in d:
    print(g[j-1],end='')
```
> Flag: picoCTF{1NV3R53LY_H4RD_261CB530}
# credstuff
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158558505-74bc0f61-fda4-457c-802c-683678bf713e.png)

[leak.txt](https://github.com/LuluL0g1n/picoctf-2022/files/8260711/leak.txt)
## Cách giải
Đề yêu cầu tìm mật khẩu của người tên cultiris, và người dùng đầu tiên trong usernames.txt ứng với mật khẩu đầu tiên trong passwords.txt

Lợi dụng điều này, bằng cách dò song song vị trí của cả 2 tệp, ta tìm thấy mật khẩu bị mã hoá của người dùng cultiris là cvpbPGS{P7e1S_54I35_71Z3}

Đến đây thì cũng dễ đoán được ở đây dùng mã Caesar thôi. Đưa lên https://www.dcode.fr/caesar-cipher, và xài key =13 :))

>Flag: picoCTF{C7r1F_54V35_71M3}
# morse-code
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158562862-69659fda-1a8c-4184-b51a-27508ef6ea82.png)
## Cách giải
Mình dùng Audacity, có thể tham khảo thêm ở video này https://www.youtube.com/watch?v=Tqxqh2hej9o

>Flag: picoCTF{wh47_h47h_90d_w20u9h7}
# rail-fence
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158569464-3ec25830-aa43-4cc8-8e2f-696cce2f9a7d.png)
[message (3).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261215/message.3.txt)
## Cách giải
Xài https://www.dcode.fr/rail-fence-cipher nhé :))

>Flag: picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_EB4C7D74}
# substitution0
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158572186-39a45ed0-62e7-4fd1-919c-d9849d7399a0.png)

[message (4).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261324/message.4.txt)
## Cách giải
Sử dụng đồng thời https://math.dartmouth.edu/~awilson/tools/frequency_analysis.html và https://www.dcode.fr/frequency-analysis 

Bằng việc thử các chữ cái trong dòng cuối cùng, trước dấu '{' là 'picoctf', rồi trước đó là 'the flag is', dần dà mở hết toàn bộ các chữ cái.

>Flag: picoctf{5ub5717u710n_3v0lu710n_7b755b1a}
# substitution1
# Đề bài
![image](https://user-images.githubusercontent.com/97771705/158574609-82354374-cb2b-4250-9804-3606bcaf5ce8.png)

[message (5).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261402/message.5.txt)

>Hint 1: Try a frequency attack

>Hint 2: Do the punctuation and the individual words help you make any substitutions?
## Cách giải
Không khác gì bài substitution0 :))

>Flag: picoctf{fr3qu3ncy_4774ck5_4r3_c001_e57444ac}
# substitution2
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158577399-76764906-9090-4674-a4f2-7005523bee22.png)

[message (6).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261541/message.6.txt)
## Cách giải
Bài này tìm khó hơn 2 bài trước xíu :))

![image](https://user-images.githubusercontent.com/97771705/158590750-f74b7e52-73a8-41ab-b28d-b2acdcb1b13b.png)

>Flag: picoctf{n6r4m_4n41y515_15_73d10u5_6cdaea76}
# transposition-trial
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158590933-409e0065-2cfd-4790-8af0-58eca5c786b9.png)

[message (7).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262118/message.7.txt)
## Cách giải
Quy luật của bài này khá đơn giản: với mỗi cụm 3 kí tự, đảo kí tự theo công thức 1->2  2->3  3->1

>Flag: picoctf{7R4N5P051N6_15_3XP3N51V3_5C82A0E0}
# Vigenere
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158598982-acfc4a42-0d9b-4896-88c0-0895191066c7.png)

[cipher.txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262426/cipher.txt)
## Cách giải
Chưa thấy câu nào dễ như này:)) Dùng mã Vigenere với key CYLAB ở đề bài

>Flag: picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_y23c13p5}
# diffie-hellman
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158599971-c21108d9-0c35-4ddd-8aeb-b9fe68611618.png)

[message (8).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262461/message.8.txt)

>Hint 1: Diffie-Hellman key exchange is a well known algorithm for generating keys, try looking up how the secret key is generated

>Hint 2: For your Caesar shift amount, try forwards and backwards.
## Cách giải
https://vi.wikipedia.org/wiki/Trao_%C4%91%E1%BB%95i_kh%C3%B3a_Diffie-Hellman

Đầu tiên, ta tính toán A = g^7 mod p và B = g^3 mod p. A = B = 8. Đây là bước tìm public key

Sau đó tìm secret key s = A^3 mod 13 hoặc B^7 mod 13. s = 5

Đưa lên https://www.dcode.fr/caesar-cipher, yêu cầu alphabet = 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ

>Flag: picoCTF{C4354R_C1PH3R_15_4_817_0U7D473D_2DBF03F7}
# Very Smooth
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158607102-7bb2d3cd-b6f7-4663-853e-ede2c483ae9c.png)

[output (1).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262772/output.1.txt)

>gen.py
```py
#!/usr/bin/python

from binascii import hexlify
from gmpy2 import *
import math
import os
import sys

if sys.version_info < (3, 9):
    math.gcd = gcd
    math.lcm = lcm

_DEBUG = False

FLAG  = open('flag.txt').read().strip()
FLAG  = mpz(hexlify(FLAG.encode()), 16)
SEED  = mpz(hexlify(os.urandom(32)).decode(), 16)
STATE = random_state(SEED)

def get_prime(state, bits):
    return next_prime(mpz_urandomb(state, bits) | (1 << (bits - 1)))

def get_smooth_prime(state, bits, smoothness=16):
    p = mpz(2)
    p_factors = [p]
    while p.bit_length() < bits - 2 * smoothness:
        factor = get_prime(state, smoothness)
        p_factors.append(factor)
        p *= factor

    bitcnt = (bits - p.bit_length()) // 2

    while True:
        prime1 = get_prime(state, bitcnt)
        prime2 = get_prime(state, bitcnt)
        tmpp = p * prime1 * prime2
        if tmpp.bit_length() < bits:
            bitcnt += 1
            continue
        if tmpp.bit_length() > bits:
            bitcnt -= 1
            continue
        if is_prime(tmpp + 1):
            p_factors.append(prime1)
            p_factors.append(prime2)
            p = tmpp + 1
            break

    p_factors.sort()

    return (p, p_factors)

e = 0x10001

while True:
    p, p_factors = get_smooth_prime(STATE, 1024, 16)
    if len(p_factors) != len(set(p_factors)):
        continue
    # Smoothness should be different or some might encounter issues.
    q, q_factors = get_smooth_prime(STATE, 1024, 17)
    if len(q_factors) != len(set(q_factors)):
        continue
    factors = p_factors + q_factors
    if e not in factors:
        break

if _DEBUG:
    import sys
    sys.stderr.write(f'p = {p.digits(16)}\n\n')
    sys.stderr.write(f'p_factors = [\n')
    for factor in p_factors:
        sys.stderr.write(f'    {factor.digits(16)},\n')
    sys.stderr.write(f']\n\n')

    sys.stderr.write(f'q = {q.digits(16)}\n\n')
    sys.stderr.write(f'q_factors = [\n')
    for factor in q_factors:
        sys.stderr.write(f'    {factor.digits(16)},\n')
    sys.stderr.write(f']\n\n')

n = p * q

m = math.lcm(p - 1, q - 1)
d = pow(e, -1, m)

c = pow(FLAG, e, n)

print(f'n = {n.digits(16)}')
print(f'c = {c.digits(16)}')

```
## Cách giải

# Sequences
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/159126237-1a2ea167-1afd-4694-9aa1-2bb9d0654bd8.png)

>sequences.py
```py
import math
import hashlib
import sys
from tqdm import tqdm
import functools

ITERS = int(2e7)
VERIF_KEY = "96cc5f3b460732b442814fd33cf8537c"
ENCRYPTED_FLAG = bytes.fromhex("42cbbce1487b443de1acf4834baed794f4bbd0dfb78a053d258da7c42b")

# This will overflow the stack, it will need to be significantly optimized in order to get the answer :)
@functools.cache
def m_func(i):
    if i == 0: return 1
    if i == 1: return 2
    if i == 2: return 3
    if i == 3: return 4

    return 55692*m_func(i-4) - 9549*m_func(i-3) + 301*m_func(i-2) + 21*m_func(i-1)


# Decrypt the flag
def decrypt_flag(sol):
    sol = sol % (10**10000)
    sol = str(sol)
    sol_md5 = hashlib.md5(sol.encode()).hexdigest()

    if sol_md5 != VERIF_KEY:
        print("Incorrect solution")
        sys.exit(1)

    key = hashlib.sha256(sol.encode()).digest()
    flag = bytearray([char ^ key[i] for i, char in enumerate(ENCRYPTED_FLAG)]).decode()

    print(flag)

if __name__ == "__main__":
    sol = m_func(ITERS)
    decrypt_flag(sol)

```
## Cách giải

# Sum-O-Primes
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/159126306-2e06998f-94ff-434a-87af-1ca599989ef8.png)

>gen.py
```py
#!/usr/bin/python

from binascii import hexlify
from gmpy2 import mpz_urandomb, next_prime, random_state
import math
import os
import sys

if sys.version_info < (3, 9):
    import gmpy2
    math.gcd = gmpy2.gcd
    math.lcm = gmpy2.lcm

FLAG  = open('flag.txt').read().strip()
FLAG  = int(hexlify(FLAG.encode()), 16)
SEED  = int(hexlify(os.urandom(32)).decode(), 16)
STATE = random_state(SEED)

def get_prime(bits):
    return next_prime(mpz_urandomb(STATE, bits) | (1 << (bits - 1)))

p = get_prime(1024)
q = get_prime(1024)

x = p + q
n = p * q

e = 65537

m = math.lcm(p - 1, q - 1)
d = pow(e, -1, m)

c = pow(FLAG, e, n)

print(f'x = {x:x}')
print(f'n = {n:x}')
print(f'c = {c:x}')

```

[output (2).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8309484/output.2.txt)
## Cách giải
Hint đề bài cho liên quan đến Square - căn bậc hai. Và đề bài cũng cho x = p + q, n = p * q. Chúng ta có thể áp dụng định lý Vi-Ét đảo đề tìm ra p và q
```py
import gmpy2
x = 287143741335562604639276799337916602395156635718684800533805966783611882634823570818570172368925153000925699717030260084702297966789535307439529101669474877058342066464737753760022604848301850326423613742024633583667628022624030722581235669019199146581332570222550601278905450467534553579488720091508594013456
n = 20282458399903387435420565424231159845720423177957886648325917351380028091397333155963612954650821203484615009181530177665840272834059492469546143439237563205203768800550549450863584193669903348504341414390629824316247389916105936107995512160823580632025395043807993620886409901515952033742185571629555911967238495792287750567037807101259634648450764125991082796203523534165751329296517240138135438460084533879601382416188798201178626388279068126744323280263478628024139719642686570825492978358814832418947763854002653688406229128981515012396561962375073164098150440094074159068335175646991629650424564441994975501063
c = 9278173516578431997880064779343178955209041085950649006761882406919480446548484048297746046169398378347003565901396909214767639919525204479182178950973893854214493663094791356431702037759145748094709219752767153964298128180779114221371406719209912843631220869991911883034243218367832866570766467833669949503446032136976624632491421620711890936280110668377532256028533088294598885271864460615079960919404679955451835969410511981264687427878333961897608650541435320684269093732631129457090523414461579612563147320873328024968983867156385188107690835686332964037803362790415052677118392808216696282685130540055268450854
delta = x*x - 4 * n
can = gmpy2.iroot(delta,2)[0]
if delta>=0:
    p = (int)(x + can )//2
    q = (int)(x - can )//2
    print(p,q)
```
Sau khi tìm được p và q ta tính như 1 bài RSA bình thường
>Flag: picoCTF{ee326097}
# NSA Backdoor
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/159126600-c86bfe7d-352e-40ba-843a-bd87ca9fc5d7.png)

[output (3).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8309502/output.3.txt)

>gen.py
```py
#!/usr/bin/python

from binascii import hexlify
from gmpy2 import *
import math
import os
import sys

if sys.version_info < (3, 9):
    math.gcd = gcd
    math.lcm = lcm

_DEBUG = False

FLAG  = open('flag.txt').read().strip()
FLAG  = mpz(hexlify(FLAG.encode()), 16)
SEED  = mpz(hexlify(os.urandom(32)).decode(), 16)
STATE = random_state(SEED)

def get_prime(state, bits):
    return next_prime(mpz_urandomb(state, bits) | (1 << (bits - 1)))

def get_smooth_prime(state, bits, smoothness=16):
    p = mpz(2)
    p_factors = [p]
    while p.bit_length() < bits - 2 * smoothness:
        factor = get_prime(state, smoothness)
        p_factors.append(factor)
        p *= factor

    bitcnt = (bits - p.bit_length()) // 2

    while True:
        prime1 = get_prime(state, bitcnt)
        prime2 = get_prime(state, bitcnt)
        tmpp = p * prime1 * prime2
        if tmpp.bit_length() < bits:
            bitcnt += 1
            continue
        if tmpp.bit_length() > bits:
            bitcnt -= 1
            continue
        if is_prime(tmpp + 1):
            p_factors.append(prime1)
            p_factors.append(prime2)
            p = tmpp + 1
            break

    p_factors.sort()

    return (p, p_factors)

while True:
    p, p_factors = get_smooth_prime(STATE, 1024, 16)
    if len(p_factors) != len(set(p_factors)):
        continue
    # Smoothness should be different or some might encounter issues.
    q, q_factors = get_smooth_prime(STATE, 1024, 17)
    if len(q_factors) == len(set(q_factors)):
        factors = p_factors + q_factors
        break

if _DEBUG:
    import sys
    sys.stderr.write(f'p = {p.digits(16)}\n\n')
    sys.stderr.write(f'p_factors = [\n')
    for factor in p_factors:
        sys.stderr.write(f'    {factor.digits(16)},\n')
    sys.stderr.write(f']\n\n')

    sys.stderr.write(f'q = {q.digits(16)}\n\n')
    sys.stderr.write(f'q_factors = [\n')
    for factor in q_factors:
        sys.stderr.write(f'    {factor.digits(16)},\n')
    sys.stderr.write(f']\n\n')

n = p * q
c = pow(3, FLAG, n)

print(f'n = {n.digits(16)}')
print(f'c = {c.digits(16)}')

```
## Cách giải





