---
title: "[프로그래머스] 문자열을 정수로 바꾸기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-12-1
---

## 🔥 문제

문자열 s를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

## ✔️ 제한사항

- s의 길이는 1 이상 5이하입니다.
- s의 맨앞에는 부호(+, -)가 올 수 있습니다.
- s는 부호와 숫자로만 이루어져있습니다.
- s는 "0"으로 시작하지 않습니다.
  

## ✔️ 입출력 예

str이 "1234"이면 1234를 반환하고, "-1234"이면 -1234를 반환하면 됩니다. str은 부호(+, -)와 숫자로만 구성되어 있고, 잘못된 값이 입력되는 경우는 없습니다.


## 🤔 문제 해설

문자열을 변환하는 메소드 `stoi()`를 사용하면 간단하게 해결할 수 있다. `stoi()`는 `sting`에서 `int`로 데이터 타입을 변환하는 함수다. 이 함수는 따로 부호처리를 하지 않아도 자동으로 부호를 붙여서 반환된다.


## 👻 코드

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(string s) {
    int answer = stoi(s);
    return answer;
}
```
