---
title: "[프로그래머스] 나누어 떨어지는 숫자 배열 (C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-24
---

## 🔥 문제
array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

<br>

---
<br>

## ✔️ 제한사항
- arr은 자연수를 담은 배열입니다.
- 정수 i, j에 대해 i != j 이면 arr[i] != arr[j] 입니다.
- divisor는 자연수입니다.
- array는 길이 1 이상인 배열입니다.

<br>

---
<br>

## ✔️ 입출력 예
|arr|divisor|return|
|---|---|---|
|[5,9,7,10]|5|[5,10]|
|[2,36,1,3]|1|[1,2,3,36]|
|[3,2,6]|10|[-1]|

<br>

---
<br>

## 🤔 문제 해설
입력값으로 들어온 arr 배열와 자연수 divisor를 사용해서 나누어 떨어지는 값을 answer에 넣고, answer를 정렬하면 되는 간단한 문제다. 만약 answer가 비었다면 -1을 반환하면 된다.

여기서 vector가 비었는지 확인하는 함수를 사용하면 된다.
```cpp
v.empty()
```


<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <algorithm>
#include <vector>

using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    for(int i=0; i<arr.size(); i++){
        if(arr[i] % divisor == 0) answer.push_back(arr[i]);
    }
    sort(answer.begin(), answer.end());
    if(answer.empty()) answer.push_back(-1);
    return answer;
}
```

<br>
