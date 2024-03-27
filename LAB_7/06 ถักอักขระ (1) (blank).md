##  ถักอักขระ (1)
จงเติมโค้ดเพื่อให้โปรแกรมสามารถทำงานได้อย่างสมบูรณ์ โดยที่ฟังก์ชัน int charcount(char *s) จะนับจำนวนอักขระที่ปรากฏอยู่ในสายอักษรที่ส่งผ่านเข้ามาในฟังก์ชันตั้งแต่อักขระตัวแรกจนถึงอักขระตัวสุดท้ายก่อนหน้าอักขระนัลล์ (null character)

ส่วนฟังก์ชัน void charweave(char *s,char *result) จะถักอักขระโดยเก็บผลลัพธ์ของการถักนี้ไว้ในตัวแปร result การถักอักขระมีลักษณะดังนี้ สมมติให้ตัวแปร s มีอักขระอยู่ n ตัวและรูปแบบการเรียงของอักขระเป็น   
$C1C2C3C4...Cn$  
ดังนั้นผลลัพธ์ที่ได้จากถักจะมีลักษณะเป็น  
 $C1CnC2Cn-1C3Cn-2C4Cn-3...Cn-1C2CnC1$

**ตัวอย่างผลลัพธ์**
```
String: hello, world
Output: hdellrloow,  ,woolrlledh
```
```
String: 12345
Output: 1524334251
```
```cpp
#include <stdio.h>

int charcount(char *s)
{
    ??????
    ??????
    ??????
}

void charweave(char *s,char *result)
{
    ??????
    ??????
    ??????
}

int main()
{  char str[100],result[200];

   printf("String: ");
   gets(str);   /* read a line of characters from the input to "str" variable */
   charweave(str,result);
   printf("Output: %s\n",result);
   return 0;
}
```
## Code
```cpp
#include <stdio.h>

int charcount(char *s)
{
    int i;
    for (i = 0; s[i]; i++);
    return i;
}

void charweave(char *s,char *result)
{
    int i, e = 0, j;
    char news[100];
    for (i = 0; s[i]; i++) news[i] = s[i];
    news[i] = '\0';
    j = charcount(news) - 1;
    for (i = 0; i < charcount(news) * 2; i++)
    {
        if (i % 2 == 0)
        {
            result[i] = news[e];
            e++;
        }
        else 
        {
            result[i] = news[j];
            j--;
        }
    }
    result[i] = '\0';
    return result;
}

int main()
{  char str[100],result[200];

   printf("String: ");
   gets(str);   /* read a line of characters from the input to "str" variable */
   charweave(str,result);
   printf("Output: %s\n",result);
   return 0;
}

```
