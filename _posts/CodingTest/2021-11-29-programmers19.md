---
title: "[프로그래머스] 짝수와 홀수(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
정수 num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하는 함수, solution을 완성해주세요.

## ✔️ 제한사항

- num은 int 범위의 정수입니다.
- 0은 짝수입니다.

## ✔️ 입출력 예

|num|return|
|---|---|
|3|"Odd"|
|4|"Even"|

## 👻 코드

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(int num) {
    return num%2==0? "Even" : "Odd";
}
```
