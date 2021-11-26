---
title: "[프로그래머스] 문자열 내 p와 y의 개수(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-26
---

## 🔥 문제
대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.

예를 들어 s가 "pPoooyY"면 true를 return하고 "Pyy"라면 false를 return합니다.

<br>

---
<br>

## ✔️ 제한사항
- 문자열 s의 길이 : 50 이하의 자연수
- 문자열 s는 알파벳으로만 이루어져 있습니다.

<br>

---
<br>

## ✔️ 입출력 예
|s|answer|
|---|---|
|"pPoooyY"|true|
|"Pyy"|false|

<br>

---
<br>

## 🤔 문제 해설
이 문제에서 중요한 조건은 바로 대소문자를 구별하지 않는다는 것이다.

이 문제에 대해 두 가지 방식으로 생각해봤는데,
1. 입력받은 문자열 속 문자를 순회하면서 `'p'`와 `'P'` 개수와 `'y'`와 `'Y`'개수 구하기
2. 입력받은 문자열을 소문자 혹은 대문자로 변경한 후, `'p'`와 `'y'` 개수 구하기
 
2번째 방법의 경우, 굳이 문자열을 변경하고, 개수를 구할 필요는 없을 것 같다.

입력받은 문자열 속 문자를 `'p'`, `'P'`, `'y'`, `'Y'` 와 비교하고 
알파벳 p와 y의 개수를 세었다. 그 후, 두 알파벳의 개수가 같다면 `true`, 같지 않으면 `false`를 반환한다.
그리고 알파벳 `p`와 `y` 둘 다 문자열에 없다면 `0`, `0`으로 `true`를 반환한다.

<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <iostream>
using namespace std;

bool solution(string s)
{
    int counts[2] = {0, 0};
    bool answer = true;
    
    for(int i=0; i<s.length(); i++){
        if(s[i] == 'p' || s[i] == 'P')  counts[0]++;
        else if(s[i] == 'y' || s[i] == 'Y')  counts[1]++;
    }
    
    return counts[0]==counts[1] ? answer : !answer;
}
```

---

<br>
<br>