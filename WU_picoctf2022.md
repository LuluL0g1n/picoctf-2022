# basic-mod1
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158553868-baec7504-86f0-4490-a630-1761b5939667.png)

>Hint 1: Do you know what mod 37 means? 

>Hint 2: mod 37 means modulo 37. It gives the remainder of a number after being divided by 37.

[message (1).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8260412/message.1.txt)
## Cách giải
>Với gợi ý của đề bài là mod 37, ta đưa toàn bộ các số của message thông qua module 37, ta được dãy số sau: [17,26,20,13,3,36,13,36,17,26,20,13,3,36,2,26,0,34,32,31,33,33]

>Yêu cầu của đề bài là với những số từ 0-25 là chữ cái viết hoa, 26-35 là các số từ 0-9, và 36 là số gạch dưới, không còn gì khó khăn:
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
>Trước tiên, ta tìm dãy số mới của message khi qua module 41 :[22,3,28,26,16,9,26,24,23,10,36,4,16,31,10,17,5,22,14,21,9,26,38]

>Hint cho ta biết ta phải tìm nghịch đảo modul của các số trên thông qua modulo 41. Ta lại có dãy số mới:[28,14,22,30,18,32,30,12,25,37,8,31,18,4,37,29,33,28,3,2,32,30,27]
```py
d = [22,3,28,26,16,9,26,24,23,10,36,4,16,31,10,17,5,22,14,21,9,26,38]
for j in d:
    print(pow(j,-1,41),end=',')
```

>Đến đây ta làm y như bài basic-mod1. Tuy nhiên có 1 chút khác biệt. Ở bài 1 thì 0-25 là các chữ cái, nhưng ở đây là 1-26, cho nên ta phải làm khác 1 chút
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
>Đề yêu cầu tìm mật khẩu của người tên cultiris, và người dùng đầu tiên trong usernames.txt ứng với mật khẩu đầu tiên trong passwords.txt

>Lợi dụng điều này, bằng cách dò song song vị trí của cả 2 tệp, ta tìm thấy mật khẩu bị mã hoá của người dùng cultiris là cvpbPGS{P7e1S_54I35_71Z3}

>Đến đây thì cũng dễ đoán được ở đây dùng mã Caesar thôi. Đưa lên https://www.dcode.fr/caesar-cipher, và xài key =13 :))

>Flag: picoCTF{C7r1F_54V35_71M3}
# morse-code
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158562862-69659fda-1a8c-4184-b51a-27508ef6ea82.png)
## Cách giải
>Mình dùng Audacity, có thể tham khảo thêm ở video này https://www.youtube.com/watch?v=Tqxqh2hej9o

>Flag: picoCTF{wh47_h47h_90d_w20u9h7}
# rail-fence
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158569464-3ec25830-aa43-4cc8-8e2f-696cce2f9a7d.png)
[message (3).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261215/message.3.txt)
## Cách giải
>Xài https://www.dcode.fr/rail-fence-cipher nhé :))

>Flag: picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_EB4C7D74}
# substitution0
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158572186-39a45ed0-62e7-4fd1-919c-d9849d7399a0.png)

[message (4).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261324/message.4.txt)
## Cách giải
>Sử dụng đồng thời https://math.dartmouth.edu/~awilson/tools/frequency_analysis.html và https://www.dcode.fr/frequency-analysis 

>Bằng việc thử các chữ cái trong dòng cuối cùng, trước dấu '{' là 'picoctf', rồi trước đó là 'the flag is', dần dà mở hết toàn bộ các chữ cái.

>Flag: picoctf{5ub5717u710n_3v0lu710n_7b755b1a}
# substitution1
# Đề bài
![image](https://user-images.githubusercontent.com/97771705/158574609-82354374-cb2b-4250-9804-3606bcaf5ce8.png)

[message (5).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261402/message.5.txt)

>Hint 1: Try a frequency attack

>Hint 2: Do the punctuation and the individual words help you make any substitutions?
## Cách giải
> Không khác gì bài substitution0 :))

>Flag: picoctf{fr3qu3ncy_4774ck5_4r3_c001_e57444ac}
# substitution2
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158577399-76764906-9090-4674-a4f2-7005523bee22.png)

[message (6).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8261541/message.6.txt)
## Cách giải
>Bài này tìm khó hơn 2 bài trước xíu :))

![image](https://user-images.githubusercontent.com/97771705/158590750-f74b7e52-73a8-41ab-b28d-b2acdcb1b13b.png)

>Flag: picoctf{n6r4m_4n41y515_15_73d10u5_6cdaea76}
# transposition-trial
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158590933-409e0065-2cfd-4790-8af0-58eca5c786b9.png)

[message (7).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262118/message.7.txt)
## Cách giải
>Quy luật của bài này khá đơn giản: với mỗi cụm 3 kí tự, đảo kí tự theo công thức 1->2  2->3  3->1

>Flag: picoctf{7R4N5P051N6_15_3XP3N51V3_5C82A0E0}
# Vigenere
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158598982-acfc4a42-0d9b-4896-88c0-0895191066c7.png)

[cipher.txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262426/cipher.txt)
## Cách giải
> Chưa thấy câu nào dễ như này:)) Dùng mã Vigenere với key CYLAB ở đề bài

>Flag: picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_y23c13p5}
# diffie-hellman
## Đề bài
![image](https://user-images.githubusercontent.com/97771705/158599971-c21108d9-0c35-4ddd-8aeb-b9fe68611618.png)

[message (8).txt](https://github.com/LuluL0g1n/picoctf-2022/files/8262461/message.8.txt)

>Hint 1: Diffie-Hellman key exchange is a well known algorithm for generating keys, try looking up how the secret key is generated

>Hint 2: For your Caesar shift amount, try forwards and backwards.
## Cách giải

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











