โปรแกรมมี class ชื่อ Hero ที่ประกอบด้วย data member ต่อไปนี้

* name เก็บข้อมูลชื่อของ Hero
* level เก็บข้อมูลเลเวลของ Hero (เป็นจำนวนเต็มบวก)

class Hero มี member function ดังนี้

* constructor ที่รับ Parameter 2 ค่า คือ ชื่อและเลเวลตามลำดับ
* getter ของชื่อ
* getter ของเลเวล
ให้เขียนโปรแกรมใน main function เพื่อรับข้อมูลชื่อ และเลเวล มาสร้าง object hero จาก class Hero
และให้แสดงชื่อและเลเวลจาก object ที่สร้าง โดยเว้นวรรคระหว่างชื่อและเลเวล  

**ตัวอย่างโปรแกรม**
```
HeroName 10
HeroName 10
```

## Code
```cpp
#include <iostream>
#include <string>

using namespace std;

class Hero // สร้าง class Hero ด้วยตัวเอง

int main()
{
    string name;
    int level;
    cin >> name >> level;
    Hero v1(name, level);
    cout << v1.getName() << " " << v1.getLevel();
    return 0;

}
```