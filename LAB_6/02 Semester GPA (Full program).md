เขียนโปรแกรมภาษาซี เพื่อคำนวณ GPA ในภาคการศึกษาหนึ่ง ของนิสิตหนึ่งคน โดยกำหนดให้ รับจำนวนวิชาที่เรียนทั้งหมดในภาคการศึกษาก่อน (จำนวนวิชาอย่างน้อย 1 วิชา) แล้วจึงรับ จำนวนหน่วยกิต และเกรด (เกรดที่โปรแกรมยอมรับ คือ A,a,B,b,C,c,D,d,F และ f เท่านั้น) ของแต่ละวิชา ในรูปแบบ credit,grade ให้ครบตามจำนวนวิชา แสดงผลดังรูปแบบในตัวอย่าง

ให้น้ำหนักของเกรด A, B, C, D, F เป็น 4, 3, 2, 1, 0 ตามลำดับ

**ตัวอย่างที่ 1**
```
Enter number of subject(s): 1
Enter credit,grade for subject #1: 4,b
GPA = 3.00
```
**ตัวอย่างที่ 2**
```
Enter number of subject(s): 8
Enter credit,grade for subject #1: 3,b
Enter credit,grade for subject #2: 3,b
Enter credit,grade for subject #3: 4,a
Enter credit,grade for subject #4: 3,a
Enter credit,grade for subject #5: 3,b
Enter credit,grade for subject #6: 3,A
Enter credit,grade for subject #7: 1,A
Enter credit,grade for subject #8: 1,a
GPA = 3.57
```

## Code
```cpp
#include <stdio.h>
#include <ctype.h>
int main()
{
    int subject, sumCredit = 0;
    double gpa , sum = 0.0;
    printf("Enter number of subject(s): ");
    scanf("%d", &subject);
    char grade;
    int credit[subject];
    double grades[subject];
    for (int i = 0; i < subject; i++){
        printf("Enter credit,grade for subject #%d: ", i + 1);
        scanf("%d, %c", &credit[i], &grade);
        sumCredit += credit[i];
        switch (tolower(grade))
        {
            case 'a':
                grades[i] = 4.0;
                break;
            case 'b':
                grades[i] = 3.0;
                break;
            case 'c':
                grades[i] = 2.0;
                break;
            case 'd':
                grades[i] = 1.0;
                break;
            case 'f':
                grades[i] = 0.0;
                break;
        }
    }
    for (int i = 0; i < subject; i++) sum += (grades[i] * credit[i]);
    gpa = sum / sumCredit;
    printf("GPA = %.2lf ", gpa);
}


```