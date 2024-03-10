กำหนดให้ Class Circle ที่มี attributes ดังนี้

* จุดศูนย์กลางของวงกลม (center) เป็นข้อมูลชนิด point (struct _point)
* รัศมีของวงกลม (radius) เป็นข้อมูลชนิด double

และ Object ที่ instantiate จาก Class Circle มี behaviors ดังนี้

* Constructor เพื่อกำหนดค่า center และ radius ของ object ตามลำดับ
* คืนค่าพื้นที่ของตนเอง (ชนิด double) ผ่าน method area()
* คืนค่าระยะทางจากจุดที่รับผ่าน parameter ถึงจุดศูนย์กลางของตนเอง ผ่าน method distanceFromCenter(point pt)
* คืนค่า 1 เมื่อกำหนดจุดให้ แล้วตรวจสอบแล้วว่าจุดนั้นไม่เกินขอบเขตของวงกลม
หรือ คืนค่า 0 เมื่อกำหนดจุดให้ แล้วตรวจสอบแล้วว่าจุดนั้นอยู่นอกขอบเขตของวงกลม ผ่าน method contains(point pt)

ให้เขียนโปรแกรมเพื่อรับข้อมูลจุดศูนย์กลาง (บรรทัดที่ 1) และรัศมีของวงกลม (บรรทัดที่ 2) แล้วนำไปสร้าง Object จาก Class Circle
จากนั้นรับจุด P บนพิกัด XY (บรรทัดที่ 3) เพื่อแสดงผลข้อมูลต่อไปนี้โดยใช้ behaviors ของ Object ที่สร้างจาก Class Circle
บรรทัดที่ 4 แสดงพื้นที่ของวงกลม (object ที่สร้างขึ้น)
บรรทัดที่ 5 แสดงระยะจากจุดศูนย์กลางของวงกลม (object ที่สร้างขึ้น) ถึงจุด P
บรรทัดที่ 6 แสดงผลลัพธ์ว่าจุด P อยู่นอกขอบเขตของวงกลม (object ที่สร้างขึ้น) หรือไม่

* ถ้าเกินขอบเขต ให้แสดงข้อความ This point is not in this circle.
* ถ้าไม่เกินขอบเขต ให้แสดงข้อความ This circle contains this point.
**ตัวอย่างโปรแกรม 1**
```
Center of Circle: 0 0
Radius of Circle: 5
Point to Check: 3.3 4.4
Area of Circle is 78.5398
Distance from Center to Point (3.3, 4.4) is 5.5
This point is not in this circle.
```
**ตัวอย่างโปรแกรม 2**
```
Center of Circle: 7.5 -2.5
Radius of Circle: 7.2
Point to Check: 6.9 0
Area of Circle is 162.86
Distance from Center to Point (6.9, 0) is 2.57099
This circle contains this point.
```
## Code
```cpp
#include <iostream>
#include <iomanip>
#include <cmath>

using namespace std;

typedef struct _point {
    double xPosition;
    double yPosition;
} point;

class Circle // เขียน Class Circle เอง

int main()
{
    point center, P;
    double radius;
    char buffer[100];
    cout << "Center of Circle: ";
    cin >> center.xPosition >> center.yPosition;
    cout << "Radius of Circle: ";
    cin >> radius;
    cout << "Point to Check: ";
    cin >> P.xPosition >> P.yPosition;

    Circle c1(center, radius);
    sprintf(buffer, "Area of Circle is %g\n", c1.area());
    cout << buffer;
    sprintf(buffer, "Distance from Center to Point (%g, %g) is %g\n", P.xPosition, P.yPosition, c1.distanceFromCenter(P));
    cout << buffer;
    sprintf(buffer, c1.contains(P) ? "This circle contains this point." : "This point is not in this circle.");
    cout << buffer;
    return 0;

}

```