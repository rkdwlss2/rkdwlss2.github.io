---
layout: post
title:  "inflearn string"
date:   2022-12-11 14:59:36 +0900
categories: C++
---

문자열 다루는 알고리즘 문제


```cpp
//
//  inflearn1.cpp
//  cplusplus
//
//  Created by 강명진 on 2022/12/11.
//

#include <iostream>
#include <string>
#include <vector>
using namespace std;

vector<string> v;

int Size = INT8_MAX;

int main(){
    int n;
    cin>>n;
    for (int i= 0;i<n;i++){
        string str;
        cin>>str;
        int nowSize = str.size();
        if (Size>nowSize)Size=nowSize;
        v.push_back(str);
    }
    for (int i= 0;i<Size;i++){
        char now = v[0][i];
        for (auto str : v){
            char diffNow = str[i];
            if (now != diffNow){
                cout <<str.substr(0,i);
                return 0;
            }
        }
    }
    cout<<v[0].substr(0,Size);
    
    
}
```
