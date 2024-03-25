## SquareRectangle inherit Rectangle
สี่เหลี่ยมผืนผ้า (Rectangle) คือ สี่เหลี่ยมที่มีมุมภายในทุกมุมเป็นมุมฉาก ประกอบด้วยด้านสูง (height) และด้านกว้าง (width)

เราสามารถสร้างคลาส Rectangle เพื่อแทนสี่เหลี่ยมมุมฉาก ที่เก็บข้อมูลด้านสูงและด้านกว้างของสี่เหลี่ยม
และมี method การหาพื้นที่ (area) และความยาวรอบรูป (circumference)
สี่เหลี่ยมจัตุรัส (Square Rectangle) คือ สี่เหลี่ยมผืนผ้าที่มีด้านสูงเท่ากับด้านกว้าง

ดังนั้น เราสามารถสร้างคลาส SquareRectangle เพื่อแทนสี่เหลี่ยมจัตุรัส ที่สืบทอดคุณลักษณะและพฤติกรรมของสี่เหลี่ยมมุมฉากได้

----------------
จงเติมส่วนของโปรแกรมด้านล่าง ให้ SquareRectangle สืบทอดคุณลักษณะและพฤติกรรมของ Rectangle
และ implement การทำงานของคลาสทั้งสอง ให้ทำงานอย่างถูกต้อง
```cpp
#include <iostream>
#include <cmath>
using namespace std;

class Rectangle
{
private:
    double width;
    double height;
public:
    Rectangle(double width, double height);
    double area();
    double circumference();
    double getWidth();
    double getHeight();
};

class SquareRectangle ??????

{
private:
    double side;
public:
    SquareRectangle(double side);
    double getSide();
};


?????
?????
?????



int main()
{
    int tc;
    double width, height;
    double side;
    Rectangle rectangle(0, 0);
    SquareRectangle sqRec(0);
    cin >> tc;
    switch (tc) {
        case 1:
            cin >> width;
            cin >> height;
            rectangle = Rectangle(width, height);
            cout << "Rectangle" << endl;
            cout << "Width: " << rectangle.getWidth() << endl;
            cout << "Height: " << rectangle.getHeight() << endl;
            cout << "Area: " << rectangle.area() << endl;
            cout << "Circumference: " << rectangle.circumference() << endl;
        break;

        case 2:
            cin >> side;
            sqRec = SquareRectangle(side);
            cout << "Square Rectangle" << endl;
            cout << "Width: " << sqRec.getWidth() << endl;
            cout << "Height: " << sqRec.getHeight() << endl;
            cout << "Side: " << sqRec.getSide() << endl;
            cout << "Area: " << sqRec.area() << endl;
            cout << "circumference: " << sqRec.circumference() << endl;
        break;
    }
}

```

## Code
```cpp
#include <iostream>
#include <cmath>
using namespace std;

class Rectangle
{
private:
    double width;
    double height;
public:
    Rectangle(double width, double height);
    double area();
    double circumference();
    double getWidth();
    double getHeight();
};

class SquareRectangle : public Rectangle

{
private:
    double side;
public:
    SquareRectangle(double side);
    double getSide();
};

Rectangle::Rectangle(double width, double height) : width(width), height(height) {}

double Rectangle::area() {return width * height;}
double Rectangle::circumference() {return 2 * (width + height);}
double Rectangle::getWidth() {return width;}
double Rectangle::getHeight() {return height;}

SquareRectangle::SquareRectangle(double side) : Rectangle(side, side), side(side) {}
double SquareRectangle::getSide() {return getWidth();}


int main()
{
    int tc;
    double width, height;
    double side;
    Rectangle rectangle(0, 0);
    SquareRectangle sqRec(0);
    cin >> tc;
    switch (tc) {
        case 1:
            cin >> width;
            cin >> height;
            rectangle = Rectangle(width, height);
            cout << "Rectangle" << endl;
            cout << "Width: " << rectangle.getWidth() << endl;
            cout << "Height: " << rectangle.getHeight() << endl;
            cout << "Area: " << rectangle.area() << endl;
            cout << "Circumference: " << rectangle.circumference() << endl;
        break;

        case 2:
            cin >> side;
            sqRec = SquareRectangle(side);
            cout << "Square Rectangle" << endl;
            cout << "Width: " << sqRec.getWidth() << endl;
            cout << "Height: " << sqRec.getHeight() << endl;
            cout << "Side: " << sqRec.getSide() << endl;
            cout << "Area: " << sqRec.area() << endl;
            cout << "circumference: " << sqRec.circumference() << endl;
        break;
    }
}
```