---
title: "第七章编程测试"
description: 
date: 2026-11-27T17:43:46+08:00
slug: pta/exam/7
categories:
    - pta
tags:
# comments: true
# draft: true
math: true
build:
    list: always    # Change to "never" to hide the page from the list
---
## 7-1 输出数组元素

本题要求编写程序，对顺序读入的n个整数，顺次计算后项减前项之差，并按每行三个元素的格式输出结果。

**输入格式**：  
输入的第一行给出正整数n（1<n≤10）。随后一行给出n个整数，其间以空格分隔。

**输出格式**：  
顺次计算后项减前项之差，并按每行三个元素的格式输出结果。数字间空一格，行末不得有多余空格。

**输入样例**：
```c
10
5 1 7 14 6 36 4 28 50 100
```
**输出样例**：
```c
-4 6 7
-8 30 -32
24 22 50
```
**完整代码**：
```c
#include <stdio.h>
int main(){
    int n;
    int num[10] = {};
    scanf("%d", &n);
    for(int i = 0;i < n;i++){
        scanf("%d", &num[i]);
        if(i != 0){
            int temp = num[i] - num[i-1];
            if(i % 3 == 0){
                printf("%d\n", temp);
            }else if(i != n - 1){
                printf("%d ", temp);
            }else{
                printf("%d", temp);
            }
        }
    }
}
```
## 7-2 打印数字下三角矩阵

n阶数字下三角矩阵是由1开始的自然数依次排列成的一个n行的下三角矩阵，例如，n=5、6时，数字下三角矩阵如输出样例所示。要求输入整数n，构造并输出n阶数字下三角矩阵。

**输入格式**:  
首先输入一个正整数T，表示测试数据的组数，然后是T组测试数据。每组测试输入一个正整数n（n不大于10)。

**输出格式**:  
对于每组测试，输出n阶数字下三角矩阵。每行的每两个数字之间留一个空格。

**输入样例**:
```c
2
5
6
```
**输出样例**:
```c
11
7 12
4 8 13
2 5 9 14
1 3 6 10 15
16
11 17
7 12 18
4 8 13 19
2 5 9 14 20
1 3 6 10 15 21
```
**完整代码**：
```c
#include <stdio.h>
int main(){
    int t;
    scanf("%d", &t);
    for(int i = 0;i < t;i++){
        int n, temp = 1;
        int num[10][10] = {};
        scanf("%d", &n);
        for(int j = 0;j < n;j++){
            for(int k = 0;k < j + 1;k++){
                num[k][j - k] = temp;
                temp++;
            }
        }
        int line = 1;
        for(int j = n - 1;j >= 0;j--){
            for(int k = 0;k < line;k++){
                if(k == line - 1){
                    printf("%d", num[k][j]);
                }else{
                    printf("%d ", num[k][j]);
                }
            }
            line++;
            printf("\n");
        }
    }
}
```