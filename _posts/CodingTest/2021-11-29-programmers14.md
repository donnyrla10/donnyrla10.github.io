---
title: "[프로그래머스] 핸드폰 번호 가리기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---
## 🔥 문제
프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

---
## ✔️ 제한사항

- s는 길이 4 이상, 20이하인 문자열입니다.


---
## ✔️ 입출력 예

|arr1|return|
|---|---|
|"01033334444"|"*******4444"|
|"027778888"|"*****8888"|

---
## 🤔 문제 해설

전체 문자열의 길이에서 4를 뺀 나머지 문자열을 "*"로 변경한다.

---
## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string phone_number) {
	string answer = phone_number;
    for(int i=0; i<answer.length()-4; i++)
        answer[i] = '*';  
    return answer;
}
```
