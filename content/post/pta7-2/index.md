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

## 7-4 判断上三角矩阵

## 7-5 打印杨辉三角