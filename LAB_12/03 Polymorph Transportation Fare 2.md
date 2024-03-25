## Transportation Fare part 2
คลาส Transportation เป็นคลาสแทนการใช้บริการรถโดยสารชนิดต่าง ๆ มีพฤติกรรม

* fare() คืนค่า ค่าใช้จ่ายในการใช้บริการรถโดยสารชนิดต่าง ๆ

คลาส BmtaBus เป็นคลาสแทนการใช้บริการรถขสมก. ซึ่งสืบทอดจากคลาส Transportation และให้มีสมบัติ polymorphism

การคำนวณค่าใช้จ่ายในการใช้บริการรถขสมก. ครั้งละ 6.50 บาท ผ่าน method fare()

จงเขียนคลาส Transportation และคลาส BmtaBus ให้เป็นไปตามข้อกำหนดข้างต้น
```cpp
#include <iostream>
using namespace std;

class Transportation
{
public:
    ?????? fare() = 0;
};

class BmtaBus ??????
{
    ??????
    ??????
    ??????
};

int main()
{
    int tc;
    cin >> tc;
    if (tc == 1) {
        BmtaBus bus;
        cout << "BMTA Bus fare: "
             << bus.fare() << endl;
    } else if(tc == 2) {
        BmtaBus bus;
        Transportation *transport = &bus;
        cout << "Transporataion fare: "
             << transport->fare() << endl;
    }
}
```

## Code
```cpp
#include <iostream>
using namespace std;

class Transportation
{
public:
    virtual double fare() = 0;
};

class BmtaBus : public Transportation#include <iostream>
using namespace std;

class Transportation
{
public:
    
virtual double
 fare() = 0;
};

class BmtaBus
: public Transportation

{
public:
    double fare() {return 6.50;}

};

int main()
{
    int tc;
    cin >> tc;
    if (tc == 1) {
        BmtaBus bus;
        cout << "BMTA Bus fare: "
             << bus.fare() << endl;
    } else if(tc == 2) {
        BmtaBus bus;
        Transportation *transport = &bus;
        cout << "Transporataion fare: "
             << transport->fare() << endl;
    }
}
{
public:
    double fare() {return 6.50;}
};

int main()
{
    int tc;
    cin >> tc;
    if (tc == 1) {
        BmtaBus bus;
        cout << "BMTA Bus fare: "
             << bus.fare() << endl;
    } else if(tc == 2) {
        BmtaBus bus;
        Transportation *transport = &bus;
        cout << "Transporataion fare: "
             << transport->fare() << endl;
    }
}
```