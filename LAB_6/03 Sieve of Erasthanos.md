## Sieve of Erasthanos
เป็นวิธีการหาค่า prime ตั้งแต่ 2 ถึง n เมื่อ n เป็นจำนวนเต็มบวก โดยเป็นการตัดค่าที่ไม่ใช่ prime ออกไปเรื่อยๆ ซึ่งมีวิธีการดังนี้

1. สร้างอาร์เรย์เก็บค่าตั้งแต่ 2 - n
2. เริ่มต้นที่ค่า p = 2
3. ตัดค่าที่ p หารลงตัวออกให้หมด
4. หาค่าต่อไปในอาร์เรย์ที่ยังไม่ถูกตัด ค่านี้เป็น prime ตัวต่อไป
5. ทำข้อ 3-4 ซ้ำจน p ยกกำลัง 2 มากกว่า n
6. ค่าที่เหลือเป็น prime

จงเขียนโปรแกรมหา prime เมื่อ n = 97 ด้วยวิธีนี้

ดูตัวอย่างการทำงานของโปรแกรมนี้ได้ที่ http://upload.wikimedia.org/wikipedia/commons/8/8c/New_Animation_Sieve_of_Eratosthenes.gif
```cpp
#include <stdio.h>
??????

int main() {

  int i, j;
  int A[ARRAY_SIZE] = {0};

  for (i = 2; i < ARRAY_SIZE; i++)
    A[i] = 1;

  for (??????) {
    ??????
    ??????
    ??????
  }

  for (i = 2; i < ARRAY_SIZE; i++)
    ??????
  printf("%d ",??????);

  printf("\n");

  return 0;
}
```
## Code
```cpp
#include <stdio.h>
#define ARRAY_SIZE 99

int main() {

  int i, j;
  int A[ARRAY_SIZE] = {0};

  for (i = 2; i < ARRAY_SIZE; i++)
    A[i] = 1;

  for (i = 2; i < ARRAY_SIZE; i++){
    if (pow(A[i], 2) > ARRAY_SIZE) break;
    if (A[i] == 0) continue;
    for (j = i + 1; j < ARRAY_SIZE; j++) if (j % i == 0) A[j] = 0;
  }

  for (i = 2; i < ARRAY_SIZE; i++) if (A[i] == 1)
  printf("%d ",i);

  printf("\n");

  return 0;
}
```