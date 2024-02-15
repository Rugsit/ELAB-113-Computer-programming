## **พื้นฐาน Switch / Case**  

โจทย์ข้อนี้ต้องการให้นิสิตสามารถเขียนคำสั่ง Switch / Case พื้นฐานได้ โดยจะให้สร้างโปรแกรมคำนวณค่าทางคณิตศาสตร์ โดยเริ่มต้นผู้ใช้งานจะใส่ค่าสองค่าเข้าไปก่อน (x กับ y) จากนั้นจะมีเมนูมาให้เลือกว่าจะคำนวณค่าอะไร  

**ตัวอย่างผลลัพธ์ที่ 1**  
```
Input x: 15
Input y: 2
x = 15.0000, y = 2.0000
[a]:Add [s]:Subtract [m]:Multiply [d]:Divide [M]:modulo [^]: x ^ y
Command? a
x + y = 17.0000
```
**ตัวอย่างผลลัพธ์ที่ 2**  
```
Input x: 3.1416
Input y: 2.5
x = 3.1416, y = 2.5000
[a]:Add [s]:Subtract [m]:Multiply [d]:Divide [M]:modulo [^]: x ^ y
Command? ^
x ^ y = 17.4935
```
**ตัวอย่างผลลัพธ์ที่ 3**
```
Input x: 15
Input y: 2
x = 15.0000, y = 2.0000
[a]:Add [s]:Subtract [m]:Multiply [d]:Divide [M]:modulo [^]: x ^ y
Command? m
x * y = 30.0000
```
**ตัวอย่างผลลัพธ์ที่ 4**
```
Input x: 22.5
Input y: 1.8
x = 22.5000, y = 1.8000
[a]:Add [s]:Subtract [m]:Multiply [d]:Divide [M]:modulo [^]: x ^ y
Command? M
x mod y = 0.9000
```

## Code
```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main() {
    char input_x[10], input_y[10];
    printf("Input x: ");
    gets(input_x);
    printf("Input y: ");
    gets(input_y);

    double x, y;
    char input_command;

    x = atof(input_x);
    y = atof(input_y);

    printf("x = %5.4f, y = %5.4f\n", x, y);
    printf("[a]:Add [s]:Subtract [m]:Multiply [d]:Divide [M]:modulo [^]: x^y\n");
    printf("Command? ");
    input_command = getchar();

    switch (input_command) {
        case 'a':
            printf("x + y = %5.4lf\n", x+y);
            break;
        case 's':
            printf("x - y = %5.4lf\n", x-y);
            break;
        case 'm':
            printf("x * y = %.4lf", x * y);
            break;
        case 'd':
            printf("x / y = %.4lf", x / y);
            break;
        case 'M':
            printf("x mod y = %.4lf", fmod(x, y));
            break;
        case '^':
            printf("x ^ y = %.4lf", pow(x, y));
            break;
        default:
            rintf("Unknown Command.\n");
            break;
    }
    return 0;

}
```