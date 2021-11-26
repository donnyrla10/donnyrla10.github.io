---
title: "[프로그래머스] x만큼 간격이 있는 n개의 숫자(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-26
---

## 🔥 문제
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

<br>

---
<br>

## ✔️ 제한사항
- x는 -10000000 이상, 10000000 이하인 정수입니다.
- n은 1000 이하인 자연수입니다.

<br>

---
<br>

## ✔️ 입출력 예
|a|n|answer|
|---|---|---|
|2|5|[2,4,6,8,10]|
|4|3|[4,8,12]|
|-4|2|[-4,-8]|

<br>

---
<br>

## 🤔 문제 해설

제한 조건이 `x는 -10000000 이상, 10000000 이하인 정수입니다.` 이므로 int가 아닌 long long 타입을 사용했다. 

반복문을 통해, n개의 값을 출력해야하는데, 각 값들이 x씩 증가해야 한다. 이 것에 대해서 두 가지 방법을 사용했는데

1. answer에 x값을 곱한 i를 push_back(). 여기서 i는 반복문이 돌 때마다 1씩 증가한다. 즉, x의 배수를 추가한다.
2. n개를 x로 초기화한 answer를 선언한다. 그 후 반복문을 돌면서 해당 값의 앞 원소 값과 x를 더한 값을 해당 벡터의 값을 업데이트한다.

<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer;
    int i=1;
    while(n--!=0){
        answer.push_back(x * i++);
    }
    return answer;
}
```
---

## 👻 코드(2)

```cpp
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer(n, x);
    for (int i = 1; i < n; i++){
        answer[i] = answer[i - 1] + x;
    }
    return answer;
}
```
---

<br>
<br>