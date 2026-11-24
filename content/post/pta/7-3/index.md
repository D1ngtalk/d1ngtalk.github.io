---
title: "7-3 字符串"
description: 
date: 2026-11-24T18:43:46+08:00
slug: pta/7-3
categories:
    - pta
tags:
# comments: true
# draft: true
math: true
build:
    list: always    # Change to "never" to hide the page from the list
---
## 7-1 统计大写辅音字母

英文辅音字母是除A、E、I、O、U以外的字母。本题要求编写程序，统计给定字符串中大写辅音字母的个数。

**输入格式**：  
输入在一行中给出一个不超过80个字符、并以回车结束的字符串。

**输出格式**：  
输出在一行中给出字符串中大写辅音字母的个数。

**输入样例**：  
```c
HELLO World!
```
**输出样例**：
```c
4
```
**解析**：  

**完整代码**：
```c
#include <stdio.h>
int main(){
    int i = 0, count = 0;
    char str[80] = {};
    while((str[i] = getchar()) != '\n'){
        if(str[i] >= 'A' && str[i] <= 'Z'){
            switch(str[i]){
                case 'A':
                case 'E':
                case 'I':
                case 'O':
                case 'U':
                    break;
                default:
                    count ++;
            }
        }
        i++;
    }
    str[i] = '\0';
    printf("%d", count);
}
```

## 7-5 查找指定字符

本题要求编写程序，从给定字符串中查找某指定的字符。

**输入格式**：  
输入的第一行是一个待查找的字符。第二行是一个以回车结束的非空字符串（不超过80个字符）。

**输出格式**：  
如果找到，在一行内按照格式“index = 下标”输出该字符在字符串中所对应的最大下标（下标从0开始）；否则输出"Not Found"。

**输入样例1**：  
```c
m
programming
```

**输出样例1**：
```c
index = 7
```
**输入样例2**：
```c
a
1234
```

**输出样例2**：
```c
Not Found
```

**完整代码**：
```c
#include <stdio.h>
int main(){
    char c;
    char str[80] = {};
    int i = 0, index = -1;
    scanf("%c\n", &c);
    while((str[i] = getchar()) != '\n'){
        if(str[i] == c){
            index = i;
        }
        i++;
    }
    if(index == -1){
        printf("Not Found");
    }else{
        printf("index = %d", index);
    }
}
```
## 7-8 删除重复字符

本题要求编写程序，将给定字符串去掉重复的字符后，按照字符ASCII码顺序从小到大排序后输出。

**输入格式**：  
输入是一个以回车结束的非空字符串（少于80个字符）。

**输出格式**：  
输出去重排序后的结果字符串。

**输入样例**：
```c
ad2f3adjfeainzzzv
```
**输出样例**：
```c
23adefijnvz
```
**完整代码**：
```c
#include <stdio.h>
int main(){
    char str[80] = {};
    char result[80] = {};
    int i = 0;
    while((str[i] = getchar()) != '\n'){
        i++;
        for(int j = 0; j < i - 1;j++){
            if(str[i - 1] == str[j]){
                i--;
            }
        }
    }
    str[i] = '\0';
    
    for (int j = 0; j < i - 1; j++){
        for (int k = 0; k < i - 1 - j; k++){
            if (str[k] > str[k + 1]) {
                int temp;
                temp = str[k];
                str[k] = str[k + 1];
                str[k + 1] = temp;
            }
        }
    }
        
    for(int k = 0; k < i;k++){
        printf("%c", str[k]);
    } 
}
```