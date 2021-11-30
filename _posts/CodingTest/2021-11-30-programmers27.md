---
title: "[프로그래머스] 약수의 합(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-30
---

## 🔥 문제

정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

## ✔️ 제한사항

- n은 0 이상 3000이하인 정수입니다.

## ✔️ 입출력 예

|n|return|
|---|---|
|12|28|
|5|6|


### 입출력 예 설명

**입출력 예** 112의 약수는 1, 2, 3, 4, 6, 12입니다. 이를 모두 더하면 28입니다.

**입출력 예** 25의 약수는 1, 5입니다. 이를 모두 더하면 6입니다.


## 🤔 문제 해설

단순하게 생각해서, 1부터 n까지 반복문을 돌려서 나누어 떨어지면 약수이므로 answer에 더해줬다.

반복문 하나로 O(n)이 걸릴거 같은데, 
1초에 약 1억번의 연산을 하면, 30000번이야 충분하다고 생각한다.ㅋㅋ... 더 좋은 방법이 있는지 찾아보도록 하겠다.

## 👻 코드

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    for(int i=1; i<=n; i++){
        if(n%i==0) answer+=i;
    }
    return answer;
}
```
