---
title: "[프로그래머스] 정수 내림차순으로 배치하기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

<br>

---
<br>

## ✔️ 제한사항
- n은 1이상 8000000000 이하인 자연수입니다.

<br>

---
<br>

## ✔️ 입출력 예
|n|return|
|---|---|
|118372|873211|

<br>

---
<br>

## 🤔 문제 해설

내림차순이라는 키워드를 보자마자 `sort` 함수가 생각났다.
입력값이 정수이므로, 각 자릿수의 수들을 정렬하려면 `string`으로 변환하여 사용하고, 결과값을 `long long` 으로 바꿔주면 될 것이라고 생각했다.


<br>

---

## 👻 코드

```cpp
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

long long solution(long long n) {
    long long answer = 0;

    string str = to_string(n);
    sort(str.begin(), str.end(), greater<char>());
    answer = stoll(str); //string -> long long

    return answer;
}
```

---

<br>
<br>