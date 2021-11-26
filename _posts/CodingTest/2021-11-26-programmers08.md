---
title: "[프로그래머스] 문자열 내 마음대로 정렬하기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-26
---

## 🔥 문제
문자열로 구성된 리스트 strings와, 정수 n이 주어졌을 때, 각 문자열의 인덱스 n번째 글자를 기준으로 오름차순 정렬하려 합니다. 예를 들어 strings가 ["sun", "bed", "car"]이고 n이 1이면 각 단어의 인덱스 1의 문자 "u", "e", "a"로 strings를 정렬합니다.

<br>

---
<br>

## ✔️ 제한사항
- strings는 길이 1 이상, 50이하인 배열입니다.
- strings의 원소는 소문자 알파벳으로 이루어져 있습니다.
- strings의 원소는 길이 1 이상, 100이하인 문자열입니다.
- 모든 strings의 원소의 길이는 n보다 큽니다.
- 인덱스 1의 문자가 같은 문자열이 여럿 일 경우, 사전순으로 앞선 문자열이 앞쪽에 위치합니다.

<br>

---
<br>

## ✔️ 입출력 예
|strings|n|return|
|---|---|---|
|["sun", "bed", "car"]|1|["car", "bed", "sun"]|
|["abce", "abcd", "cdx"]|2|["abcd", "abce", "cdx"]|

<br>

---
<br>

## 🤔 문제 해설

이번 문제는 입력받은 배열 속 각 문자열들을 n번째 문자를 기준으로 정렬한다. 

1. 각 문자열 속 n번째 문자를 기준으로 각 문자열을 sort()함수를 통해 오름차순으로 정렬
2. 만약 n번째의 문자가 같다면 전체 문자열의 사전순으로 오름차순 정렬

sort()함수를 통해 간편하게 정렬할 수 있다. 

```cpp
sort(strings.begin(), strings.end(), compare);
```
`strings.begin()`: iterator를 통해 strings의 첫번째 원소를 가리킨다.<br>
`strings.end()`: iterator를 통해 strings의 마지막 원소의 다음을 가리킨다.<br>
`compare`: 정렬 함수

이 문제의 정렬 조건을 compare 함수에 정렬한다.
```cpp
bool compare(string a, string b){
    return a[i]==b[i]? a<b : a[i] < b[i];
}
```

만약 비교하는 문자열의 n번째 인덱스 원소가 같다면 

THEN, 문자열의 사전순으로 정렬하기 위해 `a < b` 비교 <br>
ELSE, 문자열의 n번째 인덱스 원소 `a[i] < b[i]` 비교

<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
int i;

bool compare (string a, string b) {
    return a[i] == b[i] ? a < b : a[i] < b[i];
}

vector<string> solution(vector<string> strings, int n) {
    i = n;
    sort (strings.begin(), strings.end(), compare);
    return strings;
}
```

---

문자열을 인덱스로 접근하는 것과 sort()속 정렬 기준 변경에 대해 알고 있는지에 대해 묻는 문제라고 생각한다. ⍩ ⍩ ⍩
<br>
<br>