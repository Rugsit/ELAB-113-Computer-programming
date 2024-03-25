## Transportation Fare part 3
คลาส Transportation เป็นคลาสแทนการใช้บริการรถโดยสารชนิดต่าง ๆ มีพฤติกรรม

* fare() คืนค่า ค่าใช้จ่ายในการใช้บริการรถโดยสารชนิดต่าง ๆ
คลาส BTS เป็นคลาสแทนการใช้บริการรถไฟฟ้าบีทีเอส ซึ่งสืบทอดจากคลาส Transportation และให้มีสมบัติ polymorphism

การคำนวณค่าใช้จ่ายในการใช้บริการรถไฟฟ้าบีทีเอส จะเริ่มต้นที่ 15 บาท และเพิ่มขึ้นตามจำนวนสถานี สถานีละ 5 บาท

คลาส BTS มี method setStation(int) ที่รับจำนวนสถานีที่จะโดยสารไป
และมี method fare() ที่คืนค่า ค่าใช้จ่ายในการใช้บริการรถไฟฟ้าบีทีเอส

จงเขียนคลาส Transportation และคลาส BTS ให้เป็นไปตามข้อกำหนดข้างต้น
```cpp
#include <iostream>
using namespace std;

class Transportation
{
public:
    
    ?????? fare() = 0;
};

class BTS ??????
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
        int station;
        cin >> station;
        BTS bts;
        bts.setStation(station);
        cout << "BTS fare: "
             << bts.fare() << endl;
    } else if(tc == 2) {
        int station;
        cin >> station;
        BTS bts;
        bts.setStation(station);
        Transportation *transport = &bts;
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

class BTS : public Transportation

{
private:
    int station;
public:
    void setStation(int station) {this->station = station;}
    double fare() {return 15 + (station * 5);}

};

int main()
{
    int tc;
    cin >> tc;
    if (tc == 1) {
        int station;
        cin >> station;
        BTS bts;
        bts.setStation(station);
        cout << "BTS fare: "
             << bts.fare() << endl;
    } else if(tc == 2) {
        int station;
        cin >> station;
        BTS bts;
        bts.setStation(station);
        Transportation *transport = &bts;
        cout << "Transporataion fare: "
             << transport->fare() << endl;
    }
}
```