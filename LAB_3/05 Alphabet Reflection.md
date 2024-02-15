เขียนโปรแกรมเพื่อรับจำนวนเต็มบวก N (N <= 26) เพื่อแสดงรูปแบบสะท้อนขนาด N ของชุดตัวอักษร  

รูปแบบสะท้อนมีลักษณะดังนี้

#size N = 3  
c-b-a-b-c

#size N = 5  
e-d-c-b-a-b-c-d-e

#size N = 10  
j-i-h-g-f-e-d-c-b-a-b-c-d-e-f-g-h-i-j

**หมายเหตุ**

* หากไม่สามารถสร้างรูปแบบสะท้อนขนาด N ของชุดตัวอักษรได้ ให้พิมพ์ -
* ให้ใช้ Loop ในการแสดงรูปแบบสะท้อนดังกล่าว

**ตัวอย่างโปรแกรม 1**
```
3
c-b-a-b-c
```
**ตัวอย่างโปรแกรม 2**
```
5
e-d-c-b-a-b-c-d-e
```
**ตัวอย่างโปรแกรม 3**
```
0
-
```
**Hint**

ในภาษาซี สามารถแปลง character เป็น ascii code ด้วยวิธีนี้

int code;  
code = (int)'a'; // code = 97  
code = 'a'; // code = 97  
printf("%d", 'a'); // 97  

ในทำนองเดียวกัน สามารถแปลง ascii code เป็น character ด้วยวิธีนี้

char c;  
c = (char)97; // c = 'a'  
c = 97; // c = 'a'  
printf("%c", 97); // a  

## Code
```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>


int main()
{
  char num_str[10], start = 'a', stop = 'a';
  fgets(num_str, 10, stdin);
  int num = atoi(num_str), check = 0;
  start = 'a' + (num - 1); stop = start;
  while (start <= stop)
  {
    if (num <= 0 || num > 26)
    {
      printf("-");
      break;
    }
    printf("%c", start);
    if (num == 1) break;
    if (check == 0 || start != stop) printf("-");
    if ((start - 1) < 'a') check = 1;
    if (check) start++;
    else start--;
  }
}
```