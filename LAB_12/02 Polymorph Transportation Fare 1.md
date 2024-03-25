## Transportation Fare part 1
คลาส Transportation เป็นคลาสแทนการใช้บริการรถโดยสารชนิดต่าง ๆ มีพฤติกรรม

* fare() คืนค่า ค่าใช้จ่ายในการใช้บริการรถโดยสารชนิดต่าง ๆ

คลาส Taxi เป็นคลาสแทนการใช้บริการรถแท็กซี่ ซึ่งสืบทอดจากคลาส Transportation และให้มีสมบัติ polymorphism

การคำนวณค่าใช้จ่ายในการใช้บริการรถแท็กซี่ จะเริ่มต้นที่ 35 บาท และเพิ่มขึ้นตามระยะทางกิโลเมตรละ 2 บาท

Taxi มี method setDistance(double) ที่รับระยะทางหน่วยกิโลเมตร
และมี method fare() ที่คืนค่า ค่าใช้จ่ายในการใช้บริการรถแท็กซี่

จงเขียนคลาส Transportation และคลาส Taxi ให้เป็นไปตามข้อกำหนดข้างต้น
```cpp
#include <iostream>
using namespace std;

class Transportation
{
public:
    
 ?????? fare() = 0;
};

class Taxi ??????
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
        double distance;
        cin >> distance;
        Taxi taxi;
        taxi.setDistance(distance);
        cout << "Taxi fare: "
             << taxi.fare() << endl;
    } else if(tc == 2) {
        double distance;
        cin >> distance;
        Taxi taxi;
        taxi.setDistance(distance);
        Transportation *transport = &taxi;
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

class Taxi : public Transportation

{
private:
    double distance = 0;
public:
    void setDistance(double distance)
    {
        if (distance > 0)
            this->distance = distance;
    }
    double fare() 
    {
        return 35 +  distance * 2;
    }
};

int main()
{
    int tc;
    cin >> tc;
    if (tc == 1) {
        double distance;
        cin >> distance;
        Taxi taxi;
        taxi.setDistance(distance);
        cout << "Taxi fare: "
             << taxi.fare() << endl;
    } else if(tc == 2) {
        double distance;
        cin >> distance;
        Taxi taxi;
        taxi.setDistance(distance);
        Transportation *transport = &taxi;
        cout << "Transporataion fare: "
             << transport->fare() << endl;
    }
}
```