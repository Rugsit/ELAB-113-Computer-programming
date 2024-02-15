ให้เขียนโปรแกรมเพื่อรับค่าจำนวนเต็มบวก 2 จำนวน M, N จากผู้ใช้ บรรทัดละจำนวน  
จากนั้นแสดงจำนวนเต็มบวกที่มากที่สุดที่หาร M และ N ลงตัว (ห.ร.ม. - GCD) และจำนวนเต็มบวกที่น้อยที่สุดที่ M และ N หารลงตัว (ค.ร.น. - LCM)  

**ตัวอย่างโปรแกรม 1**
```
10
15
GCD: 5
LCM: 30
```
**ตัวอย่างโปรแกรม 2**
```
1585
3261
GCD: 1
LCM: 5168685
```
**ตัวอย่างโปรแกรม 3**
```
138583
262211
GCD: 997
LCM: 36447329
```

**หมายเหตุ**

* ข้อมูลนำเข้าที่ใช้เป็นชุดทดสอบ มีค่าไม่เกิน 1,000,000,000
* LCM ในชุดทดสอบ มีค่าไม่เกิน 4,000,000,000


**Hint**

* ใช้ atoll() ในการเปลี่ยน input เป็น long long
* GCD จะไม่เกินจำนวนเต็มบวก M หรือ N แต่ LCM จะไม่ต่ำกว่าจำนวนเต็มบวก M หรือ N ดังนั้น ไม่ควรให้โปรแกรมหา LCM ก่อน
* วิธีหา GCD ที่มีประสิทธิภาพ คือ Euclidean algorithm
* จาก Hint แรก ควรหา LCM จากความสัมพันธ์ M * N = GCD * LCM

## Code 
```c
#include <stdio.h>
#include <stdlib.h>
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    char a_str[20], b_str[20];
    long long int a, b, t, o;
    fgets(a_str, 20, stdin);
    fgets(b_str, 20, stdin);
    a = atoll(a_str);
    b = atoll(b_str);
    o = a * b;
    while (b != 0)
    {
        t = b;
        b = a % b;
        a = t;
    }
    printf("GCD: %lld\n", a);
    printf("LCM: %lld", o / a);
    return 0;
}
```