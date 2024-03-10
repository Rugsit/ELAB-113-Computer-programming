ให้เขียน Class Circle ที่มี attributes ดังนี้

* จุดศูนย์กลางของวงกลม (center) เป็นข้อมูลชนิด point (struct _point)
* รัศมีของวงกลม (radius) เป็นข้อมูลชนิด double

และ Object ที่ instantiate จาก Class Circle มี behaviors ดังนี้

* Constructor เพื่อกำหนดค่า center และ radius ของ object ตามลำดับ
* คืนค่าพื้นที่ของตนเอง (ชนิด double) ผ่าน method area()
* คืนค่าระยะทางจากจุดที่รับผ่าน parameter ถึงจุดศูนย์กลางของตนเอง ผ่าน method distanceFromCenter(point pt)
* คืนค่า 1 เมื่อกำหนดจุดให้ แล้วตรวจสอบแล้วว่าจุดนั้นไม่เกินขอบเขตของวงกลม
หรือ คืนค่า 0 เมื่อกำหนดจุดให้ แล้วตรวจสอบแล้วว่าจุดนั้นอยู่นอกขอบเขตของวงกลม ผ่าน method contains(point pt)
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

class Circle
{
private:
    point center;
    double radius;
public:
    Circle(point center, double radius) : center(center), radius(radius) {}


    double area()
    {
        return M_PI * pow(radius, 2);
    }
    double distanceFromCenter(point pt)
    {
        double a = center.xPosition - pt.xPosition;
        double b = center.yPosition - pt.yPosition;
        return sqrt(pow(a, 2) + pow(b, 2));
    }
    int contains(point pt)
    {
        return distanceFromCenter(pt) > radius ? 0 : 1;
    }


};


int main()
{
   // สร้าง Object เพื่อทดสอบด้วยตัวเอง
}
```