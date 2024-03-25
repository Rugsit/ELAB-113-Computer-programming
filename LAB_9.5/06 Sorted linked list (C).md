**สร้างรายการเชื่อมต่อแบบเรียงลำดับข้อมูล (ภาษา C)**
ให้ผู้เรียนสร้างโครงสร้างข้อมูลแบบ linked list (ใช้วิธีใดก็ได้) สำหรับข้อมูลประเภทจำนวนเต็มและข้อมูลใน linked list ต้องเรียงลำดับจากน้อยไปมาก พร้อมสร้างฟังก์ชั่นในการจัดการ 3 ฟังก์ชั่น คือ insert delete และ print

* insert รับค่าเป็นจำนวนเต็มหนึ่งตัวเพื่อเพิ่มเข้าไปใน linked list
* delete รับค่าเป็นจำนวนเต็มหนึ่งตัวเพื่อลบข้อมูลทุกตัวที่มีค่าเท่ากับจำนวนเต็มนั้น
* print แสดงข้อมูลทั้งหมดใน linked list (แสดงออกทาง stdout หนึ่งบรรทัด)

โปรแกรมจะรับคำสั่งผ่านทาง stdin โดยคำสั่งมีทั้งหมด 4 คำสั่งคือ

* i k เป็นคำสั่ง insert: เพิ่มข้อมูล k เข้าไปใน linked list
* d k เป็นคำสั่ง delete: ลบข้อมูลที่มีค่าเท่ากับ k ทุกตัวออกจาก linked list
* p เป็นคำสั่ง print: แสดงข้อมูล
* q เป็นคำสั่ง quit: จบการทำงาน
**ตัวอย่างข้อมูลส่งออก**
```
input> p
[ ]
input> i 5
input> i 4
input> i 1
input> p
[ 1 4 5 ]
input> i 10
input> i 4
input> d 4
input> d 2
input> i 9
input> d 5
input> i 6
input> p
[ 1 6 9 10 ]
input>q
```
## Code
```cpp
#include <stdio.h>
#include <stdlib.h>

typedef struct linked
{
    int data;
    struct linked *next;
}Link;

void printList(Link *list)
{
    printf("[ ");
    for (list; list; list = list->next)
    {
        printf("%d ", list->data);
    }
    printf("]\n");
}

Link *insertList(Link *head, int data)
{
    Link *newnode;
    Link *current = NULL;
    Link *previous = NULL;
    newnode = (Link *)malloc(sizeof(Link));
    newnode->next = NULL;
    newnode->data = data;
    if (head == NULL) head = newnode;
    if (head != NULL && head->data > data)
    {
        newnode->next = head;
        head = newnode;
        return head;
    }
    for (current = head; current; current = current->next)
    {
        if (current->data > data) break;
        previous = current;
    }
    previous->next = newnode;
    newnode->next = current;
    
    return head;
}

Link *deleteList(Link *head, int data)
{
    Link *temp;
    Link *pre = NULL;
    Link *cur = NULL;
    if (head == NULL) return head;
    while(head->data == data)
    {
        temp = head;
        head = head->next;
        temp->next = NULL;
        free(temp);
        if (head == NULL) break;
    }
    for (cur = head; cur; cur = cur->next)
    {
        temp = cur;
        if (cur->data == data)
        {
            pre->next = temp->next;
            temp->next = NULL;
            cur = pre;
            free(temp);
        }
        pre = cur;
    }
    return head;
}

int main()
{
    char command, buffer;
    int data;
    Link *head = NULL;
    while(command != 'q')
    {
        printf("input> ");
        command = getchar();
        if(command == 'p')
        {
            getchar();
            printList(head);
        }
        else if(command == 'i')
        {
            scanf("%d", &data);
            getchar();
            head = insertList(head, data);
        }
        else if(command == 'd')
        {
            scanf("%d", &data);
            getchar();
            head = deleteList(head, data);
        }
        else if (command == 'q') break;
        
    }
}
```