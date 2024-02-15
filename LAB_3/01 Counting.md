Write a program that get an integer n and print the number from n down to 0 if n >= 0

**Example 1**  
```
13
13
12
11
10
9
8
7
6
5
4
3
2
1
0
```
**Example 2**
```
0
0
```
**Example 3**
```
-1
```
**Example 4**
```
1
1
0
```
Complete the program below
## Code
```c
#include <stdio.h>
#include <stdlib.h>
int main() {
    // Write C code here
    char number_str[10];
    int number;
    
    fgets(number_str, 10, stdin);
    number = atoi(number_str);
    
    for (int i = number; i >= 0; i--)
    {
        printf("%d\n", i);
    }
    return 0;
}
```