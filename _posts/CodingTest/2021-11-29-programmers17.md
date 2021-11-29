---
title: "[프로그래머스] 문자열 다루기 기본(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
문자열 s의 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수, solution을 완성하세요. 예를 들어 s가 "a234"이면 False를 리턴하고 "1234"라면 True를 리턴하면 됩니다.
<br>

---
<br>

## ✔️ 제한사항
- s는 길이 1 이상, 길이 8 이하인 문자열입니다.

<br>

---
<br>

## ✔️ 입출력 예
|s|return|
|---|---|
|"a234"|false|
|"1234"|true|

<br>

---
<br>

## 🤔 문제 해설

두가지 방법을 생각했다.

1. 0 과 9 사이의 숫자가 아니라면 `false` 반환
2. `isdigit()`함수를 사용해서 숫자가 아니라면 `false` 반환


> `isgit()`함수: 헤더파일 `<cctype>`, 매개변수로 들어온 `char`가 10진수 숫자로 변경가능하면 `true`, 아니면 `false`.

<br>

우선 문자열 길이가 4 혹은 6인 것이 입력 조건이므로 조건에 맞지 않으면 false를 반환하는 조건문을 앞에 두어서 이 조건이 맞지 않으면 숫자인지 확인할 필요가 없도록 한다.

그 후, 반복문을 통해 문자열 속 문자들을 하나씩 조건문을 통해 숫자인지 확인하는 과정을 수행한다.


<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

bool solution(string s) {
    //문자열의 길이 4, 6가 아닌지 체크
    if(s.length() != 4 && s.length() != 6)  return false;
    //숫자인지 체크
    for(int i=0; i<s.length(); i++){
        if(s[i] < '0' || s[i] > '9') return false;
    }
    return true;
}
```

---

<br>

## 👻 코드(2)

```cpp
#include <string>
#include <vector>
using namespace std;

bool solution(string s) {
    if(s.length() != 4 && s.length() != 6)  return false;

    for (int i = 0; i < s.length(); i++){
        if (!isdigit(s[i])) return false;
    }
    return true;
}
```

---

<br>
<br>