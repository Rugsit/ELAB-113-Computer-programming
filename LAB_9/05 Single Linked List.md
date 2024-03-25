## สร้าง list อย่างง่าย
ให้นิสิตเขียนโปรแกรมเพื่อสร้างลิสต์อย่างง่ายใช้เองโดยไม่ใช้ array แต่ละ element ในลิสต์จะเป็น node (struct) ที่มีตัวแปร value (int) เป็นค่าที่เก็บไว้ใน node และตัวแปร next ซึ่งจะชี้ไปยัง node ต่อไป ค่า next ของ node สุดท้ายจะเป็น NULL เราสามารถเรียกใช้ลิสต์ผ่าน pointer ซึ่งชี้ไปยังโหนดแรกของลิสต์นั้น

ฟังก์ชันที่ใช้กับลิสต์มีสองฟังก์ชันคือ insertNode() ซึ่งจะเพิ่ม node เข้าไปในลิสต์ โดยจะรับค่าที่จะเพิ่มและ pointer ซึ่งชี้ไปที่โหนดแรกของลิสต์ แล้วจะทำการสร้างโหนดใหม่ที่เก็บค่านั้นและเพิ่มเข้าไปในลิสต์ การเพิ่มโหนดนั้นจะเรียงลำดับค่าของโหนดจากน้อยไปมากให้ด้วย (ดังนั้นลิสต์จะเรียงลำดับค่าอยู่เสมอ) ฟังก์ชันที่สองคือ printList() ซึ่งจะพิมพ์ค่าของโหนดในลิสต์ออกมาทีละค่าโดยเว้นช่องว่างระหว่างค่าและขึ้นบรรทัดใหม่เมื่อพิมพ์ค่าสุดท้าย

#### คำแนะนำ
* การเพิ่มโหนดนั้นอาจเพิ่มได้ทั้งท้ายลิสต์ หน้าลิสต์ และระหว่างกลาง ควรเขียนโค้ดให้ครบทุกกรณี
* ระวังกรณีพิเศษคือเมื่อลิสต์ยังว่างอยู่ตอนใส่โหนดครั้งแรก

```cpp
#include <stdio.h>
#include <stdlib.h>

??????
??????
void printList(node *pList) {
    ??????
    ??????
    ??????
}

?????? insertNode(??????) {
    ??????
    ??????
    ??????
}

int main() {
  int i, value;
  node *pList=NULL;

  for (i = 0; i < 10; i++) {
    scanf(" %d", &value);
    ??????    

  }

  printList(pList);
}
```

## Code
```cpp
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
    int data;
    struct node *next;
}node;

void printList(node *pList) {
    for (pList;;pList = pList->next)
        {
            if(!pList)
            {
                printf("\n");
                break;
            }
            printf("%d ", pList->data);
        }
}

node * insertNode(int input, node *head) {
    node *newnode = (node *)malloc(sizeof(node));
    node *prev = NULL;
    node *current = NULL;
    newnode->data = input;
    newnode->next = NULL;
    if (head == NULL)
    {
        head = newnode;
        return head;
    }
    if (head != NULL && head->data > input)
    {
        newnode->next = head;
        head = newnode;
        return head;
    }
    for (current = head; current; current = current->next)
    {
        if (current->data > input) break;
        prev = current;

    }
    prev->next = newnode;
    newnode->next = current;
    return head;
}

int main() {
  int i, value;
  node *pList=NULL;

  for (i = 0; i < 10; i++) {
    scanf(" %d", &value);
    pList = insertNode(value, pList);    
  }

  printList(pList);
}
```