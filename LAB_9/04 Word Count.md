## Word Count

จงเขียนโปรแกรมในการนับจำนวนคำที่ได้รับมาจากผู้ใช้งาน โดยผู้ใช้งานจะป้อนคำเข้ามาในระบบเรื่อย ๆ
โปรแกรมสามารถบันทึกข้อมูลจำนวนคำที่ไม่ซ้ำกันได้ไม่เกิน 20 คำ (array data) และแต่ละคำ (word) มีความยาวไม่เกิน 20 ตัวอักษร
เมื่อผู้ใช้งานป้อนคำเข้าไปในระบบจนพอใจแล้วให้ หยุดโปรแกรมโดยการพิมพ์คำว่า exit
โปรแกรมจะหยุดทำงานพร้อมกับพิมพ์คำ (word) และจำนวนคำ (count) ที่ได้รับเข้ามาในระบบ

**ตัวอย่าง 1**
```
This
Is
BOOK
Book
Hello
Hello
Hello
exit
Output:
This = 1
Is = 1
BOOK = 1
Book = 1
Hello = 3
```
**ตัวอย่าง 2**
```
one
one
one
exit
Output:
one = 3
```
```cpp
#include<stdio.h>
#include<string.h>

struct Word {
    ??????
    ??????
    ??????
};

int main(){
        char input[21];
        int i, last_word = 0, find = 0;
        struct Word data[20] = {0};
        scanf("%20s", input);

        while(??????){
            ??????
            ??????
            ??????
        }

        printf("Output:\n");
        for(i=0;i<last_word;i++){
                printf("%s = %d\n", data[i].word, data[i].count);
        }
}
```
## Code
```cpp
#include<stdio.h>
#include<string.h>

struct Word {   
    char word[20];
    int count;
};

int main(){
        char input[21];
        int i, last_word = 0, find = 0;
        struct Word data[20] = {0};
        scanf("%20s", input);

        while(strcmp(input, "exit") != 0){
            int pre_find = find;
            for (i = 0; i < 20; i++)
            {
                if (strcmp(input, data[i].word) == 0)
                {
                    find++;
                    data[i].count++;
                }
            }
            if (pre_find == find)
            {
                strcpy(data[last_word].word, input);
                data[last_word].count++;
                last_word++;
                
            }
            scanf("%20s", input);

        }

        printf("Output:\n");
        for(i=0;i<last_word;i++){
                printf("%s = %d\n", data[i].word, data[i].count);
        }
}
```