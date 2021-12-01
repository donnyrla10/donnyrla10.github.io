---
title: "[프로그래머스] 수박수박수박수?(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-12-1
---

## 🔥 문제

길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.


## ✔️ 제한사항

- n은 길이 10,000이하인 자연수입니다.
  

## ✔️ 입출력 예

|n|return|
|---|---|
|3|"수박수"|
|4|"수박수박"|


## 🤔 문제 해설

문자 `'수'`, `'박'`을 배열에 넣고, 입력값 `n`만큼 반복문을 돌면서 `'수'`, `'박'`을 반복적으로 출력하면 된다.

여기서 `'수'`, `'박'`을 한번씩 출력하면 인덱스 `i = 2` 부터는 출력할 수 있는 원소가 없으므로 다시 첫번째 원소로 돌아가게 해야 한다. 이를 위해, `i`를 `ch` 배열의 길이만큼 나눈 나머지를 인덱스로 해서 접근한다.


## 👻 코드

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(int n) {
    string answer = "";
    string ch[2] = {"수", "박"};
    for(int i=0; i<n; i++)
        answer += ch[i%2];
    return answer;
}
```
