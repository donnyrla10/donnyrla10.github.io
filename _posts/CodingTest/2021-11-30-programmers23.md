---
title: "[프로그래머스] 정수 제곱근 판별(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-30
---

## 🔥 문제

임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.


## ✔️ 제한사항

- n은 1이상, 50000000000000 이하인 양의 정수입니다.


## ✔️ 입출력 예

|n|return|
|---|---|
|121|144|
|3|-1|

### 입출력 예 설명

**입출력 예#1**121은 양의 정수 11의 제곱이므로, (11+1)를 제곱한 144를 리턴합니다.

**입출력 예#2**3은 양의 정수의 제곱이 아니므로, -1을 리턴합니다.


## 🤔 문제 해설

수학 내장 함수를 사용하면 간단하게 해결할 수 있다. 

`sqrt(n)` : 매개변수 n의 제곱근을 구하는 함수

`powl(a, n)` : 매개변수 a의 n승을 구하는 함수로, 반환형이 long doulbe 입니다.<br>
→ `double pow(double x, double y)`<br>
→ `float powf(float x, float y)`
추가적으로 있다.

`sqr()`함수로 n의 제곱근을 구해 `answer`에 넣고, 그 값을 이용해 `powl()`함수로 `answer`의 `2승`이 `n`인지 삼항 연산자를 통해 체크를 했다.
<br>만약 `n`이라면 `+1`한 제곱을 리턴하고, 아니라면 `-1`을 리턴하도록 했다.


## 👻 코드

```cpp
#include <string>
#include <vector>
#include <math.h>
using namespace std;

long long solution(long long n) {
    long long answer = sqrt(n);

    return powl(answer, 2) == n ? powl(answer + 1, 2) : -1;
}
```
