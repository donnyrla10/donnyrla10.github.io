---
title: "[프로그래머스] 문자열 내림차순으로 배치하기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-26
---

## 🔥 문제
문자열 s에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수, solution을 완성해주세요. s는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.

<br>

---
<br>

## ✔️ 제한사항
- str은 길이 1 이상인 문자열입니다.

<br>

---
<br>

## ✔️ 입출력 예
|s|return|
|---|---|
|"Zbcdefg"|"gfedcbZ"|

<br>

---
<br>

## 🤔 문제 해설

대문자와 소문자를 구별하는데, 대문자를 소문자보다 작은 것으로 간주한다고 한다. 그러므로, 내림차순으로 정렬하면 된다.
sort()함수에서 정렬 방식을 내림차순으로 하면 된다.
```cpp
greater<자료형>() // 내림차순

less<자료형>()    //오름차순
```
<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <algorithm>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = s;
    sort(answer.begin(), answer.end(), greater<char>());
    return answer;
}
```

---

<br>
<br>