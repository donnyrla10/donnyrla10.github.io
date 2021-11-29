---
title: "[프로그래머스] 행렬의 덧셈(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

<br>

---
<br>

## ✔️ 제한사항
- 행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.

<br>

---
<br>

## ✔️ 입출력 예
|arr1|arr2|return|
|---|---|---|
|[[1,2],[2,3]]|[[3,4],[5,6]]|[[4,6],[7,9]]|
|[[1],[2]]|[[3],[4]]|[[4],[6]]|

<br>

---
<br>

## 🤔 문제 해설

이 문제는 단순한 행렬의 덧셈에 대한 문제다. <br>
문제에도 적혀있듯이 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 더한 결과를 반환하면 되는데,

`arr1의 첫번째 행의 첫번째 열의 원소 + arr2의 첫번째 행의 첫번째 열의 원소`

를 뜻한다. `arr1`을 반복문을 돌면서 `arr1`의 동일 행, 열에 `arr2`의 값을 더하는 식으로 구현하였다.


<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    for(int i=0; i<arr1.size(); i++){
        for(int j=0; j<arr1[0].size(); j++)
            arr1[i][j] += arr2[i][j];
    }
    return arr1;
}
```

---

<br>

## 🤓 내 생각

구현한 코드는 중첩코드로 시간복잡도 `O(n^2)`인데, 제한사항을 보면 arr1, arr2의 행과 열의 길이는 500이 넘지 않는다고 되어있다. 만약 arr1, arr2의 행과 열의 길이가 500이라면 

`500 * 500 = 250,000`

컴퓨터가 1초에 1억번 연산을 하고, 반복문 안의 구현 내용이 복잡하지 않는 것을 보면, 수행 속도 측면에서 나쁘지 않다고 생각한다. 

시간복잡도를 줄일 더 좋은 방법이 있다면 추후에 추가하도록 하겠다~~