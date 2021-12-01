---
title: "[프로그래머스] 서울에서 김서방 찾기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-12-1
---

## 🔥 문제

String형 배열 seoul의 element중 "Kim"의 위치 x를 찾아, "김서방은 x에 있다"는 String을 반환하는 함수, solution을 완성하세요. seoul에 "Kim"은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.


## ✔️ 제한사항

- seoul은 길이 1 이상, 1000 이하인 배열입니다.
- seoul의 원소는 길이 1 이상, 20 이하인 문자열입니다.
- "Kim"은 반드시 seoul 안에 포함되어 있습니다.  
- 

## ✔️ 입출력 예

|seoul|return|
|---|---|
|["Jane", "Kim"]|"김서방은 1에 있다"|


## 🤔 문제 해설

`algorithm`에는 `find()` 함수가 있다. 이것을 통해 간단하게 원하는 값을 찾을 수 있다.

`find()` 함수의 원형은

```cpp
template <class InputIt, class T>
InputIt find(InputIt first, InputIt last, const T& value)
```

`first`부터 `last`까지 순회하면서 `value`와 일치하는 첫 번째 원소를 가리키는 반복자를 리턴하고 일치하는 원소가 없다면 last 반복자를 리턴한다. 

여기서 주의할 점은, `find()`함수는 반복자, 즉 주소를 반환하기 때문에, 시작점인 `seoul.begin()`을 빼줘야 해당 원소의 인덱스를 구할 수 있다. 


## 👻 코드

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

string solution(vector<string> seoul) {
    string answer = "김서방은 ";
    int index = find(seoul.begin(), seoul.end(), "Kim")- seoul.begin();
    answer += to_string(index);
    answer += "에 있다";
    return answer;
}
```
