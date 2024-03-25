## File Average Score
Read scores from the specified file. Then report the average value.

ให้เขียนโปรแกรมเพื่ออ่านข้อมูลคะแนนจากไฟล์ จากนั้นคำนวณหาค่าเฉลี่ยของคะแนนในไฟล์ดังกล่าว

โดยเขียนฟังก์ชัน findAverage ที่รับชื่อไฟล์ และคืนค่าเฉลี่ยของคะแนนในไฟล์

**Example 1**  
Suppose the file scores.txt contains the following:
```
89
42
70
85
33
26
29
65
27
84
```
Then the program's output should be:
```
scores.txt
Average score is 55.0000
```
**Example 2**  
The file [big-scores.txt](https://elab.cpe.ku.ac.th/elab_media/supplements/111/big-scores.txt) (click the link to download) contains 100 scores, which should produce the following output:
```
big-scores.txt
Average score is 64.6700
```
```cpp
#include <stdio.h>

double findAverage(char *filename)
{
    ??????
    ??????
    ??????
}

int main()
{
    char filename[20];
    double average;
    scanf("%s", filename);
    average = findAverage(filename);
    printf("Average score is %.4lf\n", average);
}
```
## Code
```cpp
#include <stdio.h>

double findAverage(char *filename)
{
    FILE *fp;
    int total_score = 0, score;
    double count = 0.0;
    fp = fopen(filename, "r");
    while(fscanf(fp, "%d", &score) != EOF)
    {
        total_score += score;
        count++;
    }

    fclose(fp);
    return total_score / count;

}

int main()
{
    char filename[20];
    double average;
    scanf("%s", filename);
    average = findAverage(filename);
    printf("Average score is %.4lf\n", average);
}
```