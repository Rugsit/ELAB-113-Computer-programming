## Stock Log File
ตามุและตามิ สองพี่น้องเปิดร้านขายเสื้อผ้าขนาดใหญ่แถวประตูน้ำ ตามุเป็นคนใจดี เขียนโปรแกรมจัดการระบบขายเสื้อผ้าด้วยตัวเอง โปรแกรมของตามุจะเก็บบันทึกการขายเสื้อผ้าแยกไว้เป็นวันละไฟล์

รูปแบบของข้อมูลในไฟล์บันทึกการขายเสื้อผ้าของโปรแกรมที่ตามุเขียนเป็นดังนี้

* บรรทัดที่ 1 เป็นจำนวนประเภทของเสื้อผ้าที่ขายได้ในวันนั้น
* บรรทัดที่ 2 เป็นต้นไป เป็นรายละเอียดของเวลาที่ขายเสื้อผ้า ประเภทเสื้อผ้าที่ขาย จำนวนที่ขาย และราคาที่ขาย มีรูปแบบคือ **ปีเดือนวัน,เวลา,ชื่อประเภทเสื้อผ้า,จำนวนที่ขาย,ราคาขาย**

ตามิเป็นคนขี้เหนียว เห็นทีว่าตามุที่เป็นคนใจดี จะขายเสื้อผ้าได้กำไรน้อย เพราะตามุชอบใจอ่อนกับลูกค้าที่น่ารัก ๆ อยู่เสมอ จึงเขียนโปรแกรมเพื่อสรุปจำนวนและยอดขายของเสื้อผ้าแต่ละประเภทจากไฟล์บันทึกการขายเสื้อผ้าที่ได้จากโปรแกรมที่ตามุเขียน

เมื่อวันที่ 1 เมษายน 2017 ที่ผ่านมา เป็นวันเมษาคนโง่ ผู้คนเลยไม่ค่อยออกไปที่ไหน วันนั้นไฟล์บันทึกมีรายการน้อยมาก เหมาะแก่การนำมาเป็นไฟล์ตัวอย่างในการเขียนโปรแกรม ตามิจึงไปขอไฟล์ตามุ และได้ไฟล์ซึ่งมีข้อมูลดังนี้

**ข้อมูลในไฟล์ stock-log-20170401.txt**
``` 
4
20170401,12:54:00,T Shirt L,1,120.00
20170401,12:56:32,Boxer,2,90.00
20170401,13:12:34,T Shirt L,2,200.00
20170401,13:12:34,Boxer,2,98.00
20170401,14:29:17,T Shirt M,4,480.00
20170401,16:39:27,Shorts M,1,120.50
20170401,17:12:34,T Shirt L,3,350.00
```
ตามิต้องการเขียนโปรแกรม เพื่อสรุปข้อมูลให้ได้ดังนี้
```
    Product Name    |Amount|     Total
T Shirt L           |     6|    670.00
Boxer               |     4|    188.00
T Shirt M           |     4|    480.00
Shorts M            |     1|    120.50
```
จะเห็นว่า ผลลัพธ์เรียงลำดับประเภทสินค้าจากประเภทสินค้าแรกที่ปรากฏในไฟล์  

จงช่วยตามิเขียนโปรแกรมเพื่อให้ได้ผลลัพธ์ตามความต้องการของตามิ โดยใน main จะรับชื่อไฟล์จาก standard input และส่งชื่อไฟล์นี้ไปให้ฟังก์ชัน reportStock

**ตัวอย่างโปรแกรม**
```
stock-log-20170401.txt
    Product Name    |Amount|     Total
T Shirt L           |     6|    670.00
Boxer               |     3|    139.00
T Shirt M           |     4|    480.00
Shorts M            |     1|    120.50
```
```cpp
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

typedef struct _product {
    char name[30];
    int amount;
    double totalCost;
} Product;

void printStock(Product stock[], int nStock)
{
    int i;
    printf("%-20s|%6s|%-10s\n", "    Product Name", "Amount", "     Total");
    for (i = 0; i < nStock; i++) {
        printf("%-20s|%6d|%10.2lf\n",
            stock[i].name, stock[i].amount, stock[i].totalCost);
    }
}

??????
??????
??????


int main()
{
    char filename[20];
    scanf("%s", filename);
    reportStock(filename);
}
```
## Code
```cpp
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

typedef struct _product {
    char name[30];
    int amount;
    double totalCost;
} Product;

void printStock(Product stock[], int nStock)
{
    int i;
    printf("%-20s|%6s|%-10s\n", "    Product Name", "Amount", "     Total");
    for (i = 0; i < nStock; i++) {
        printf("%-20s|%6d|%10.2lf\n",
            stock[i].name, stock[i].amount, stock[i].totalCost);
    }
}

void reportStock(char filename[20])
{
    FILE *fp;
    int n = 0, product_index = 0, i = 0, target_index = 0, amount_product = 0;
    char c, match = 0;
    char buffer[100] = {0};
    char *token;
    char *endptr;
    fp = fopen(filename, "r");
    fscanf(fp, "%d", &n);
    Product products[n];
    for (i = 0; i < n; i++)
    {
        products[i].amount = 0;
        products[i].totalCost = 0;
    }
    while (!feof(fp))
    {
        fgets(buffer, 100, fp);
        token = strtok(buffer, ",");
        product_index = 0;
        match = 0;
        while (token != NULL)
        {  
            token = strtok(NULL, ",");
            product_index++;
            if (product_index == 2)
            {
                for (i = 0; i < n; i++)
                {
                    if(strcmp(products[i].name, token) == 0)
                    {
                        target_index = i;
                        match = 1;
                        break;
                    }
                }
                if (!match)
                {
                    target_index = amount_product;
                    strcpy(products[amount_product].name, token);
                    amount_product++;
                }
            }
            else if (product_index == 3)    
                products[target_index].amount += strtol(token, &endptr, 10); 
            else if (product_index == 4)
                products[target_index].totalCost += strtod(token, &endptr); 
        }
    }
    fclose(fp);
    printStock(products, n);
}


int main()
{
    char filename[20];
    scanf("%s", filename);
    reportStock(filename);
}
```