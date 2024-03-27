## เปลี่ยน String เป็นอักษรตัวใหญ่
ให้นิสิตเขียนฟังก์ชันชื่อ stoupper() ซึ่งจะรับสตริงมาหนึ่งตัว จากนั้นจะสร้างสตริงก์ใหม่ที่นำอักษรภาษาอังกฤษตัวเล็กจากสตริงก์เก่ามาเปลี่ยนเป็นอักษรตัวใหญ่ (Capital Letter) อักษรที่ไม่ใช่ตัวเล็กนั้นจะเหมือนเดิม จากนั้นจะรีเทิร์น pointer ไปที่สตริงใหม่นี้

นิสิตไม่สามารถใช้ฟังก์ชันใดใน string.h ได้ แต่สามารถใช้ฟังก์ชันใน ctype.h ได้ (เช่น toupper() เป็นต้น)

**ตัวอย่าง 1**
```
Hello,World
HELLO,WORLD
```
**ตัวอย่าง 2**
```
c3t-WiCoS
C3T-WICOS
```
```cpp
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#define static "use malloc"

?????? stoupper(const ??????) {
    ??????
    ??????
    ??????
}

int main(){
	char s[100];
	char* result;

	scanf("%s",s);
	result = stoupper(s);
        if (result == s) printf("ERROR.\n");
	printf("%s\n",result);
}
```

## Code
```cpp
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#define static "use malloc"

char *stoupper(const char s[]) {
    int i;
    char *str = (char *)malloc(sizeof(char)*100);
    for (i = 0; s[i]; i++)
    {
        if (str[i] <= 'z' && s[i] >= 'a') 
        {
            str[i] = toupper(s[i]);
        }
        else str[i] = s[i];
    }
    str[i] = '\0';
    return str;
}

int main(){
	char s[100];
	char* result;

	scanf("%s",s);
	result = stoupper(s);
    if (result == s) printf("ERROR.\n");
	printf("%s\n",result);
}
```