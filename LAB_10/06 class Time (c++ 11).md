## Time
Implement a class Time with three attributes: hour, minute, second. All of them are integer.

Write mutator (set) and accessor (get) methods of these attributes. The constructors and other methods are listed below.

|          |         |         |
| -------- | ------- | ------- |
|   | Time(int hour, int minute, int second)   | Construct and initialize Time object    |
|  | Time(int duration)     | Construct and initialize Time object. The duration parameter has second unit|
| int    | 	getDuration()   |return duration in seconds|
| Time    | add(Time other)    |	return Time that is the result of adding this Time and other Time together|
| int| subtract(Time other)    |	return duration in seconds between this Time and other Time|
| int| equals(Time other)   |return 1 if this Time and other Time are the same; otherwise, return 0|
| string| 	toString()   |return String of hour:minute:second, e.g., "09:08:04"|

**Note that**
0
Example of subtract the time :  
( a ) -> 02:02:02  
( b ) -> 01:01:01  
**(a) - (b) => 3661 sec.**  
**(b) - (a) => 82739 sec.**

ในข้อนี้ให้ใช้ฟังก์ชัน to_string() ใน **library** string ตามมาตรฐาน c++11 มาช่วย

## Code
```cpp
#include <iostream>
#include <cstdlib>
#include <sstream>
#include <cmath>
#include <string>
#include <iomanip>

using namespace std;

class Time
{
private:
    int hour;
    int minute;
    int second;
public:
    Time(int hour, int minute, int second)
    {
        int duration = (hour * 3600) + (minute * 60) + second; 
        this->hour = (duration / 3600) % 24;
        this->minute = (duration / 60) % 60;
        this->second = duration % 60;
    }
    Time(int duration)
    {
        hour = (duration / 3600) % 24;
        minute = (duration / 60) % 60;
        second = duration % 60;
    }



    int getHour() const {return hour;}
    int getMinute() const {return minute;}
    int getSecond() const {return second;}
    void setHour(int hour) {this->hour = hour;}
    void setMinute(int minute) {this->minute = minute;}
    void setSecond(int second) {this->second = second;}

    int getDuration()
    {
        return (hour * 3600) + (minute * 60) + second;
    }
    Time add(Time other)
    {
        int all_duration = other.getDuration() + this->getDuration();
        int h = (all_duration / 3600) % 24;
        int m = (all_duration / 60) % 60;
        int s = all_duration % 60;
        Time newtime(h, m, s);
        return newtime;
    }
    int subtract(Time other)
    {
        if(this->getDuration() - other.getDuration() < 0) 
            return (24 * 3600) - other.getDuration() + this->getDuration();
        else return this->getDuration() - other.getDuration();
    }
    int equals(Time other)
    {
        return getDuration() == other.getDuration();
    }
    string toString()
    {
        string s;
        s = (getHour() > 9 ? to_string(getHour()) : "0" + to_string(getHour())) + ":"
        +  (getMinute() > 9 ? to_string(getMinute()) : "0" + to_string(getMinute())) + ":"
        + (getSecond() > 9 ? to_string(getSecond()) : "0" + to_string(getSecond()));
        return s;
    }

};


int main()
{
   // implement program to test class Time
}

```