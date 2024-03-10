สร้าง class ชื่อ Hero ที่ประกอบด้วย data member ต่อไปนี้

* name เก็บข้อมูลชื่อของ Hero
* level เก็บข้อมูลเลเวลของ Hero (เป็นจำนวนเต็มบวก)  

class Hero มี member function ดังนี้

* constructor ที่รับ Parameter 2 ค่า คือ ชื่อและเลเวลตามลำดับ
* getter ของชื่อ
* getter ของเลเวล
## Code
```cpp
#include <iostream>
#include <string>
using namespace std;

class Hero
{
private:
    string name;
    int level;
public:
    Hero(string name, int level) : name(name), level(level) {}
    string getName()
    {
        return name;
    } 
    int getLevel()
    {
        return level;
    }
};


int main()
{
   // สร้าง object เพื่อทดสอบด้วยตัวเอง
}
```
