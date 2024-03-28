## เส้นทางแห่งนักบวช
หมากรุกสากลเป็นเกมส์ที่เล่นบนกระดานตารางขนาด 8x8 ช่อง โดยตัวนักบวช (Bishop) นั้นสามารถเดินเป็นเฉียงได้สี่ทิศทาง (ซ้ายบน ขวาบน ซ้ายล่าง ขวาล่าง) และระยะการเดินนั้นไม่จำกัด (ยกเว้นสุดขอบกระดาน) ให้นิสิตเขียนฟังก์ชัน bishopMoves() ซึ่งรับตำแหน่งของนักบวชมา แล้วกำหนดตำแหน่งที่นักบวชเดินไปได้ โดยกำหนดให้ช่องซ้ายบนสุดมีตำแหน่งเป็น 0 0 และช่องขวามือล่างสุดมีตำแหน่งเป็น 7 7

จากนั้นให้นิสิตพิมพ์ตารางหมากรุกโดยแสดงตำแหน่งของนักบวชด้วยอักษร B และแสดงตำแหน่งที่นักบวชเดินไปได้ด้วยอักษร X ถ้านักบวชเดินไปยังตำแหน่งนั้นไม่ได้ให้พิมพ์ช่องว่าง (space bar)

**ตัวอย่างผลลัพธ์ที่ 1**  
```
Enter Bishop's X Y position: 3 4
  0 1 2 3 4 5 6 7
------------------
0| | | | | | | |X|
------------------
1|X| | | | | |X| |
------------------
2| |X| | | |X| | |
------------------
3| | |X| |X| | | |
------------------
4| | | |B| | | | |
------------------
5| | |X| |X| | | |
------------------
6| |X| | | |X| | |
------------------
7|X| | | | | |X| |
------------------
```
```cpp
#include <stdio.h>
#define BOARD_SIZE 8

void bishopMoves(??????) {
    ??????
    ??????
    ??????
}

int main() {
    ??????
    ??????
    ??????
}

```
## Code
```cpp
#include <stdio.h>
#define BOARD_SIZE 8

void bishopMoves(int x, int y, char table[BOARD_SIZE][BOARD_SIZE]) {
    int i = y + 1, j = x + 1, check = 1;
    while (1)
    {
        if (x == 0 && y == 7) break;
        if (i < 0 || j < 0) break;
        if (i > 7 || j > 7)
        {
            check = 0;
            i = y - 1; j = x - 1;
        }
        table[i][j] = 'X';
        if (check)
        {
            j++; i++;
        }
        else
        {
            j--; i--;
        }
        
    }
    i = y - 1 ; j = x + 1; check = 1;
    while (1)
    {
        if (i > 7 || j < 0) break;
        if (j > 7 || i < 0)
        {
            check = 0;
            i = y + 1; j = x - 1;
            if (i > 7 || j < 0) break;
        }
        table[i][j] = 'X';
        if (check)
        {
            j++; i--;
        }
        else
        {
            j--; i++;
        }
        
    }
}

int main() {
    int x, y;
    char table[BOARD_SIZE][BOARD_SIZE];
    for(int i = 0; i < BOARD_SIZE; i++)
    for(int j = 0; j < BOARD_SIZE; j++)
    table[i][j] = ' ';
    printf("Enter Bishop's X Y position: ");
    scanf("%d %d", &x, &y);
    table[y][x] = 'B';
    bishopMoves(x, y, table);
    printf("  0 1 2 3 4 5 6 7\n");
    for(int i = 0; i < BOARD_SIZE; i++)
    {
        printf("------------------\n%d", i);
        for(int j = 0; j < BOARD_SIZE; j++) printf("|%c", table[i][j]);
        printf("|\n");
    }
    printf("------------------");
}

```