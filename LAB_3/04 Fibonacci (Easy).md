พิจารณาลำดับต่อไปนี้

 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...   
ลำดับดังกล่าวมีชื่อเรียกว่า "ลำดับฟีโบนัชชี Fibonacci's sequence" !!  
คุณอาจทราบมาว่าลำดับที่ n ของฟีโบนัชชีหาได้จาก F(n) = F(n-2) + F(n-1) โดย F(0) = 0 และ F(1) = 1  

แต่ลำดับที่ n ของฟีโบนัชชี สามารถคำนวณจากสูตรต่อไปนี้

$${F_n = (1 + \sqrt{5}) ^ n − (1 − \sqrt{5}) ^ n  \over 2 ^ n (\sqrt{5})}$$  

จงเขียนฟังก์ชัน int fibo(int n) เพื่อคำนวณเลขฟีโบนัชชีลำดับที่ n  
และใช้ฟังก์ชันดังกล่าว แสดงเลขฟีโบนัชชีลำดับที่ 0 ถึงลำดับที่ n เมื่อ n คือข้อมูลนำเข้า ซึ่งเป็นจำนวนเต็ม และ n >= 0

**Sample output 1:**
```
3
F(0) = 0
F(1) = 1
F(2) = 1
F(3) = 2
```
**Sample output 2:**
```
8
F(0) = 0
F(1) = 1
F(2) = 1
F(3) = 2
F(4) = 3
F(5) = 5
F(6) = 8
F(7) = 13
F(8) = 21
```

## Code
```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int fibo(int n)
{
    return (pow(1 + sqrt(5), n) - pow(1 - sqrt(5), n)) / (pow(2, n) * sqrt(5));
}

int main()
{
    char input_n[5];
    fgets(input_n, 5, stdin);
    int n, i;
    n = atoi(input_n);
    for (i = 0; i <= n; i++) 
    {
        printf("F(%d) = %d\n", i, fibo(i));
    }
    return 0;
}
```