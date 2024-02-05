ตรวจสอบความถูกต้องของโปรแกรม ถ้าถูกต้องให้คัดลอกโปรแกรมใส่ด้านล่าง แต่ถ้าผิดให้แก้ไขให้ถูกต้อง
```c
#include <studio.h>
#include <stolib.h>
int main()
{
    char hour_str[3], min_str[3];
    int hour, min;

    printf("Enter hour: "):
    fget(hour_str, 3, stdin);

    printf("Enter minute: "):
    get(minstr);

    hour = atoi(hour_str);
    minute = atoi(minstr);

    printf("Time is %d:%d, hour, minute");
    return 0;
}
```
โดยให้แสดงผลตามตัวอย่างต่อไปนี้

**Sample output 1**
```
Enter hour: 9
Enter minute: 18
Time is 09:18
```

**Sample output 2**
```
Enter hour: 10
Enter minute: 7
Time is 10:07
```
**หมายเหตุ** เวลาส่วนของชั่วโมงและนาทีจำเป็นต้องแสดงเป็นเลข 2ตัว
ให้ใช้บรรทัดเท่ากับตัวอย่างโปรแกรม มิฉะนั้น ข้อนี้จะได้ 0 แม้ว่าจะ P ครบทุกตัว
## CODE
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    char hour_str[4], min_str[4];
    int hour, min;

    printf("Enter hour: ");
    fgets(hour_str, 4, stdin);

    printf("Enter minute: ");
    fgets(min_str, 4, stdin);

    hour = atoi(hour_str);
    min = atoi(min_str);

    printf("Time is %02d:%02d" , hour, min);
    return 0;
}
```