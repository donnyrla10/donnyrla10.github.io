---
title: "[프로그래머스] 같은 숫자는 싫어 (C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-24
---

## 🔥 문제
배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,

- arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
- arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.


<br>
배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

---
<br>

## ✔️ 제한사항
- 배열 arr의 크기 : 1,000,000 이하의 자연수
- 배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수


<br>

---
<br>

## ✔️ 입출력 예

|arr|answer|
|---|---|
|[1,1,3,3,0,1,1]|[1,3,0,1]|
|[4,4,4,3,3]|[4,3]|

<br>

---
<br>

## 🤔 문제 해설

두 가지 방법으로 코드를 작성했다.
1. 반복문을 통해 배열을 순차적으로 접근 
2. vector의 메소드를 통해 중복 원소 제거

코드와 함께 보면서 설명하도록 하겠다.

<br>

---
<br>

## 👻 코드(1)

```cpp
#include <vector>
#include <iostream>

using namespace std;

vector<int> solution(vector<int> arr) 
{
    vector<int> answer;
    answer.push_back(arr[0]);
    
    for(int i=1; i<arr.size(); i++){
        if(arr[i] != arr[i-1])
            answer.push_back(arr[i]);
    }
    return answer;
}
```
<br>

for문의 시작을 `1`로 했는데, 그 이유는 만약 `0`부터 시작하면 마지막 원소를 비교해서 넣을 수가 없게 된다. <br> 
즉, 현재 원소와 다음 원소를 비교해서 벡터에 삽입을 하게 되는데 마지막 원소는 비교할 다음 원소가 없기 때문에 원하는 값이 나오지 않는다. 그러므로 `1`부터 시작하여 앞의 원소와 비교를 하도록 해야한다. 반복문을 실행하기 전에 배열의 첫번째 원소는 먼저 벡터에 넣어줬는데, `index 1번`부터 앞의 원소와 비교를 하기 때문에 `index 0번`의 원소는 비교를 하지 않는다. 그러므로 첫번째 원소를 먼저 넣어주고, 중복 비교를 한다.

<br>

## 👻 코드(2)

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> arr) 
{
    vector<int> answer;
    arr.erase(unique(arr.begin(), arr.end()),arr.end());
    answer = arr;
    return answer;
}
```

`vector`의 `erase()`함수로 원소를 지울 수 있는데, `unique()`함수와 함께 사용하면 중복된 원소를 제거할 수 있다!!


```cpp
arr.erase(unique(arr.begin(), arr.end(), arr.end());
```

→ 중복 원소를 맨 뒤로 보내는 기능을 하는 `unique()`함수가 끝나면 `vector`의 쓰레기값(뒤로 밀린 중복값)의 첫번째 위치를 반환한다. 즉, 중복 원소를 맨 뒤로 보낸 곳의 위치를 반환한다는 것인데 이 부분부터 끝 원소까지 모두 지워주면 된다. <br>
<br>

> **간단한 `unique()` 설명**<br>
첫 원소의 주소와 마지막 원소의 다음 주소를 인자로 넘겨준다.
구간내의 중복된 원소를 구간의 끝부분으로 밀어주고 마지막 원소의 다음 주소를 리턴한다.
이때, 구간내의 원소들은 정렬되어 있어야한다.<br>
*보통 `erase()`와 함께 중복된 원소를 제거하는 방법으로 사용한다.*

<br>

---
## 👾 개인적인 생각

두 가지 방법을 생각하면서 어떤 것이 더 효율적인지를 고민하게 되었는데

시간적인 성능에서 보면, 2번 방법에서의 erase()는 vector의 임의 원소를 삭제 및 이동시키므로 O(n)이 나온다. 

그러므로 1번 방법인 for문의 시간 복잡도 O(n)과 별 차이가 없을 것이라고 생각한다. 

<br>

> 공부하면서 기록하였기 때문에 제가 아직 부족하여 틀렸을 수도 있습니다. 혹여 잘못되었다면 댓글로 꼭 말씀해주세요 🤭 **감사합니다~!! ⍩**


<br>