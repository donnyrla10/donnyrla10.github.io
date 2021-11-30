---
title: "[프로그래머스] 자릿수 더하기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-30
---

## 🔥 문제

자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

## ✔️ 제한사항

- N의 범위 : 100,000,000 이하의 자연수

## ✔️ 입출력 예

|n|return|
|---|---|
|123|6|
|987|24|

## 🤔 문제 해설

두 가지 방법으로 생각해봤다.
1. 자연수를 10으로 나눠 각 자릿수를 더하는 방법
2. 자연수를 문자열로 변경해하고 '0'을 빼줘서 아스키코드를 이용하는 방법


## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

vector<int> solution(long long n) {
    vector<int> answer;
    while(n!=0){
        answer.push_back(n%10);
        n/=10;
    }
    return answer;
}
```

→ 지난 문제들에서 꾸준히 나왔던 방법으로, 10으로 나눈 나머지로 각 자릿수를 일의 자릿수부터 차례대로 구할 수 있다. 

## 👻 코드(2)

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int n){
    int answer = 0;
    string s = to_string(n);
    for(int i = 0; i < s.size(); i++) answer += (s[i] - '0');

    return answer;
}
```

→ 이 방법은, to_string(n) 함수를 통해 자연수 n을 문자열로 변환시킨다. 문자열은 각 원소인 문자를 인덱스로 랜덤 접근할 수 있기 때문에 편리하게 사용할 수 있다. 그리고 각 문자는 아스키코드를 가지고 있는데, 문자에 '0'를 빼주면 해당 문자의 값을 알 수 있다. 