---
title: "[프로그래머스] 가운데 글자 가져오기 (C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-24
---

## 🔥 문제
단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

---

## ✔️ 제한사항

- s는 길이가 1 이상, 100이하인 스트링입니다.

---

## ✔️ 입출력 예

|s|return|
|---|---|
|"abcde"|"c"|
|"qwer"|"we"|

---

## 🤔 문제 해설

가운데 문자를 반환하면 되기 때문에
짝수와 홀수로 나눠서 가운데 문자를 구한다.

- 짝수의 경우, 문자열 길이를 2로 나눈 값에 1을 빼서 가운데 글자 2개를 반환<br>
예시) "qwer"의 문자열 길이는 4, 4/2=2. 
<br>→ 가운데 글자 2개를 반환해야 하므로 나눈 값에서 1을 빼고, 두 글자를 반환하도록 한다.
- 홀수의 경우, 문자열 길이를 2로 나눈 값으로 가운데 글자 1개 반환<br>
예시) "abcde" 의 문자열 길이는 5, 5/2=2

이때, c++의 string에는 substr() 함수가 있어 사용하면 된다. substr()는 부분 문자열 함수로, 문자열 일부를 리턴한다.

```cpp
s.substr(pos, count)
```
pos번째 문자부터 count 길이만큼의 문자열을 리턴한다. count가 없으면 끝까지 리턴한다.

---

## 👻 코드

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    answer = ((s.length()%2 == 0)? s.substr(s.length()/2-1,2): s.substr(s.length()/2,1));
    return answer;
}
```

→ 삼항 연산자를 사용해서 간단하게 코드를 작성했다.