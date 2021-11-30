---
title: "[프로그래머스] 자연수 뒤집어 배열로 만들기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-30
---

## 🔥 문제

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

## ✔️ 제한사항

- n은 10,000,000,000이하인 자연수입니다.

## ✔️ 입출력 예

|n|return|
|---|---|
|12345|[5,4,3,2,1]|

## 🤔 문제 해설

string이 아닌 long long 정수형으로 입력값이 들어오므로 10으로 나눈 나머지(일의 자리)를 answer에 넣어주면 된다. 

answer에 원소를 넣고, n을 10으로 나눠 업데이트를 시켜주면 while문을 돌면서 차례대로 일의 자릿수부터 자릿수가 증가하면서 answer에 값이 들어간다.


## 👻 코드

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(long long n) {
    vector<int> answer;
    while(n!=0){
        answer.push_back(n%10);
        n/=10;
    }
    return answer;
}
```
