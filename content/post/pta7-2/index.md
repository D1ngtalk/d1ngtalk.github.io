---
title: "7-2 二维数组"
description: 
date: 2026-11-22T15:07:46+08:00
categories:
    - pta
tags:
# comments: true
# draft: true
build:
    list: always    # Change to "never" to hide the page from the list
---
## 7-2 求矩阵各行元素之和
本题要求编写程序，求一个给定的m×n矩阵各行元素之和。  

**输入格式**：  
输入第一行给出两个正整数m和n（1≤m,n≤6）。随后m行，每行给出n个整数，其间以空格分隔。  

**输出格式**：  
每行输出对应矩阵行元素之和。  

**输入样例**：  
```c
3 2
6 3
1 -8
3 12
```
**输出样例**：  
```c
9
-7
15
```

**解析**：  
先看输入格式：  
* 输入第一行给出**两个正整数**m和n（1≤m,n≤6），  
  
可以看出，需要两个整型变量 `m` 和 `n` 存储输入： 
```c
int m,n;
```
* 随后**m行**，**每行给出n个整数**，其间以空格分隔。  

可以看出，至少需要一个循环，来进行多行的输入，循环的次数为 `m` ：
```c
for(int i = 0;i < m;i++){

}
```
再看题目要求，来确定循环体内我们需要做什么：  
* 求一个给定的m×n矩阵各行元素之和。  

要求的是每一行的元素之和，也就是输入要求的：**m行**，**每行给出n个整数**。  

所以我们需要一个整型变量 `sum` ，用于储存每行计算的结果，还需要在循环里嵌套一个循环，进行 `n` 次输入。我们使用整型变量 `temp` 来存储每一次的输入，并将每次获取的输入累加到 `sum` 里：
```c
for(int i = 0;i < m;i++){
    int sum = 0;                # 储存每行计算结果
    for(int j = 0;j < n;j++){   # 进行n次输入循环
        int temp;               # 储存输入
        scanf("%d", &temp);
        sum += temp;            # 将输入累加进sum
    }
}
```
最后看输出要求：
* 每行输出对应矩阵行元素之和。  

由于PTA平台的特性，每次输入都是一次性的，所以我们可以在获取到每行的输入后直接输出结果。
```c
for(int i = 0;i < m;i++){
    int sum = 0;
    for(int j = 0;j < n;j++){
        int temp;
        scanf("%d", &temp);
        sum += temp;
    }
    printf("%d\n", sum); # 在每行结束后直接输出结果
}
```

**完整代码**:
```c
#include <stdio.h>
int main(){
    int m, n, sum = 0;
    scanf("%d%d", &m, &n);
    for(int i = 0;i < m;i++){
        sum = 0;
        for(int j = 0;j < n;j++){
            int temp;
            scanf("%d", &temp);
            sum += temp;
        }
        printf("%d\n", sum);
    }
}
```

## 7-3 计算天数
本题要求编写程序计算某年某月某日是该年中的第几天。

**输入格式**:  
输入在一行中按照格式“yyyy/mm/dd”（即“年/月/日”）给出日期。注意：闰年的判别条件是该年年份能被4整除但不能被100整除、或者能被400整除。闰年的2月有29天。 

**输出格式**:  
在一行输出日期是该年中的第几天。

**输入样例1**:
```c
2009/03/02
```
**输出样例1**:
```c
61
```
**输入样例2**:
```c
2000/03/02
```
**输出样例2**:
```c
62
```

**完整代码**：
```c
#include <stdio.h>
int main(){
    int year, month, day, result = 0;
    scanf("%d/%d/%d", &year, &month, &day);
    int isBigMonth = 1, isBigYear = 0;
    if((year % 4 == 0 && year % 100 != 0) || year % 400 == 0){
        isBigYear = 1;
    }
    if(month == 1){
        printf("%d", day);
        return 0;
    }
    result += month / 2;
    if(month > 2){
        result += (month - 2) * 30;
        result += 28 + isBigYear;
    }else{
        result += 30;
    }
    result += day;
    printf("%d", result);
    return 0;
}
```

## 7-4 判断上三角矩阵
上三角矩阵指主对角线以下的元素都为0的矩阵；主对角线为从矩阵的左上角至右下角的连线。

本题要求编写程序，判断一个给定的方阵是否上三角矩阵。

**输入格式**：  
输入第一行给出一个正整数T，为待测矩阵的个数。接下来给出T个矩阵的信息：每个矩阵信息的第一行给出一个不超过10的正整数n。随后n行，每行给出n个整数，其间以空格分隔。

**输出格式**：  
每个矩阵的判断结果占一行。如果输入的矩阵是上三角矩阵，输出“YES”，否则输出“NO”。

**输入样例**：
```c
3
3
1 2 3
0 4 5
0 0 6
2
1 0
-8 2
3
1 2 3
1 4 5
0 -1 6
```

**输出样例**：
```c
YES
NO
NO
```

**完整代码**：
```c
#include <stdio.h>
int main(){
    int t;
    scanf("%d", &t);
    for(int i = 0;i < t;i++){
        int n;
        int isTrue = 1;
        scanf("%d", &n);
        for(int j = 0;j < n;j++){
            for(int k = 0;k < n;k++){
                int num;
                scanf("%d", &num);
                if(k < j && num != 0){
                    isTrue = 0;
                }
            }
        }
        if(isTrue){
            printf("YES\n");
        }else{
            printf("NO\n");
        }
    }
}
```

## 7-5 打印杨辉三角
本题要求按照规定格式打印前N行杨辉三角。

**输入格式**：  
输入在一行中给出N（1≤N≤10）。

**输出格式**：  
以正三角形的格式输出前N行杨辉三角。每个数字占固定4位。

**输入样例**：
```c  
6
```
**输出样例**：  
```c
        1
       1   1
      1   2   1
     1   3   3   1
    1   4   6   4   1
   1   5  10  10   5   1
```
**完整代码**：
```c
#include <stdio.h>
int main(){
    int n;
    scanf("%d", &n);
    int num[n][10] = {};
    for(int i = 0;i < n;i++){
        for(int k = 1;k < n-i;k++){
            printf(" ");
        }
        for(int j = 0;j < i+1;j++){
            if(j == 0 || j == i+1){
                num[i][j] = 1;
            }else{
                num[i][j] = num[i-1][j] + num[i-1][j-1];
            }
            printf("%4d", num[i][j]);
        }
        printf("\n");
    }
}
```
