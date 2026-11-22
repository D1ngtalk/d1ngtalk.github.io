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
  
可以看出，需要两个整型变量m和n存储输入。  
* 随后**m行**，**每行给出n个整数**，其间以空格分隔。  

可以看出，至少需要一个循环，来进行多行的输入，循环的次数为m。

再看题目要求：  
* 求一个给定的m×n矩阵各行元素之和。  

要求的是每一行的元素之和，也就是输入的**m行**，**每行给出n个整数**。  
由于PTA平台的特性，每次输入都是一次性输入的，所以我们可以在获取到每行的输入后直接输出结果。

**代码**:
```c
#include <stdio.h>
int main(){
    int m, n, sum = 0;
    scanf("%d%d", &m, &n);
    int num[m][6];
    for(int i = 0;i < m;i++){
        sum = 0;
        for(int j = 0;j < n;j++){
            int temp;
            scanf("%d", &temp);
            num[i][j] = temp;
            sum += temp;
        }
        printf("%d\n", sum);
    }
}
```

