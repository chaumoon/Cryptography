In RSA, a small e value can be problematic, but what about N? Can you decrypt this? values
https://mercury.picoctf.net/static/38f30029ab93478310e906d3d084a4c1/values
Hints 
Bits are expensive, I used only a little bit over 100 to save money

1. mở file values:
```
ecrypt my super sick RSA:
c: 240986837130071017759137533082982207147971245672412893755780400885108149004760496
n: 831416828080417866340504968188990032810316193533653516022175784399720141076262857
e: 65537
```
2. để mã hóa cần c, d, n -> tính d
dùng tool http://factordb.com/ để tách số n thành 2 số nguyên tố p và q

3. viết code mã hóa để tìm flag
```
from Crypto.Util.number import inverse, long_to_bytes
c = 240986837130071017759137533082982207147971245672412893755780400885108149004760496
n = 831416828080417866340504968188990032810316193533653516022175784399720141076262857
e = 65537
p =  1593021310640923782355996681284584012117
q = 521911930824021492581321351826927897005221
phi = (p-1)*(q-1)
d = pow(e, -1, phi)
m = pow(c, d, n)
print(long_to_bytes(m))
```
4. flag: picoCTF{sma11_N_n0_g0od_23540368}
