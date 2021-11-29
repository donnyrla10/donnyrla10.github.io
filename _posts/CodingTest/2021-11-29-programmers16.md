---
title: "[프로그래머스] 평균 구하기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.

<br>

---
<br>

## ✔️ 제한사항
- arr은 길이 1 이상, 100 이하인 배열입니다.
- arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.

<br>

---
<br>

## ✔️ 입출력 예
|arr|return|
|---|---|
|[1,2,3,4]|2.5|
|[5,5]|10|

<br>

---
<br>

## 🤔 문제 해설

이 문제는 `<numeric>` 헤더파일에 있는 `accumulate()` 함수를 사용하면 간단하게 해결할 수 있다. 

`accumulate()`함수는
```cpp
template<class InputIt, class T>
constexpr // since C++20
T accumulate(InputIt first, InputIt last, T init)
{
    for (; first != last; ++first) {
        init = std::move(init) + *first; // std::move since C++20
    }
    return init;
}
```
함수의 내부를 보면, 3가지 인자를 받는다.<br>
첫번째 인자는 `first`로, 첫번째 원소를 가리킨다.<br>
두번째 인자는 `last`로, 마지막 원소의 다음을 가리킨다.<br>
세번째 인사는 `init`으로, 초기값이다.

`[first, last)` → `first` 인자부터 `last` 인자 전까지의 원소를 모두 더하는 것인데, 마지막 인자를 바로 초기값이다. 즉, `init` 값에 `first` 원소부터 더하는 것이다. 

여기서 주의할 것은, `accumulate`의 반환값 타입은 초기값의 타입이다. 


<br>

---
<br>

## 👻 코드

```cpp
#include <string>
#include <numeric>
#include <vector>

using namespace std;

double solution(vector<int> arr) {
    double answer = accumulate(arr.begin(), arr.end(), 0);
    return answer / arr.size();
}
```

---

<br>