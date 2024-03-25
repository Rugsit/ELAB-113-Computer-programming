## Music Playlist
จงเขียนคลาส MusicPlaylist เพื่อแทนเพลย์ลิสต์ของเพลง ซึ่งมีพฤติกรรมดังนี้

1. สามารถเก็บเพลงได้มากถึง 20 เพลง
2. เพิ่มเพลงลงเพลย์ลิสต์ ผ่าน method add(string)
3. เลือกลำดับของเพลงที่ต้องการจะฟังจากเพลย์ลิสต์ ด้วย method setCurrentTrack(int)
4. เล่นเพลงที่เลือกจากลำดับของเพลง ด้วย method play() ในที่นี้ให้ return string ของเพลงที่ตรงกับลำดับที่เลือก
```cpp
#include <iostream>
#include <string>
using namespace std;

??????
??????
??????

int main()
{
    MusicPlaylist mp;
    mp.add("Shape of You");
    mp.add("That's What I Like");
    mp.add("Humble");
    mp.setCurrentTrack(1);
    cout << mp.play() << endl; // แสดงเพลงลำดับที่ 1 คือ Shape of You
}
```

## Code
```cpp
#include <iostream>
#include <string>
using namespace std;

class MusicPlaylist 
{
private:
    string music[20];
    int total_music = 0;
    int current;
public:
    void add(string new_music)
    {   
        music[total_music] = new_music;
        total_music++;
    }
    void setCurrentTrack(int num){current = num - 1;}
    string play() {return music[current];}
};


int main()
{
    MusicPlaylist mp;
    mp.add("Shape of You");
    mp.add("That's What I Like");
    mp.add("Humble");
    mp.setCurrentTrack(1);
    cout << mp.play() << endl; // แสดงเพลงลำดับที่ 1 คือ Shape of You
}
```

