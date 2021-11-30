---
title: "[프로그래머스] 이상한 문자 만들기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-30
---

## 🔥 문제

문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

## ✔️ 제한사항

- 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
- 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

## ✔️ 입출력 예

|s|return|
|---|---|
|"try hello world"|"TrY HeLlO WoRlD"|

### 입출력 예 설명
"try hello world"는 세 단어 "try", "hello", "world"로 구성되어 있습니다. 각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 바꾸면 "TrY", "HeLlO", "WoRlD"입니다. 따라서 "TrY HeLlO WoRlD" 를 리턴합니다.


## 🤔 문제 해설

조건을 다시 보면,
- **단어**별로 짝수 홀수 인덱스를 판단해야 한다. 

짝수 → 대문자
홀수 → 소문자


## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    int flag = 0;
    for(int i=0; i < s.length(); i++){
        if(s[i] != ' '){ //공백이 아니라면
            if(flag == 0){ //짝수
                answer += toupper(s[i]);
                flag = 1;
            }
            else{ //홀수
                answer += tolower(s[i]);
                flag = 0;
            }
        }
        else{ //공백이라면
            answer += " ";
            flag = 0; //초기화
            
        }
    }
    return answer;
}
```

변수 flag는 짝수 홀수를 구분해주는 용도로 사용했다.
문자열 전체를 도는 반복문을 통해 각 문자를 검사한다. 

만약 공백이 아니고 짝수면 대문자로 (toupper()함수 -> 대문자 변환 함수), 홀수면 소문자로 (tolower()함수 -> 소문자 변환 함수) 그리고 flag를 각 경우에 따라 변경해준다. 

그리고 만약 공백이라면, answer에 공백을 추가하고 flag를 0으로 초기화해준다. 단어별 홀짝 인덱스 판단을 해야되므로!