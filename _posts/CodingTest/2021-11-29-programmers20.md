---
title: "[프로그래머스] 제일 작은 수 제거하기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

<br>

---
<br>

## ✔️ 제한사항
- arr은 길이 1 이상인 배열입니다.
- 인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.


<br>

---
<br>

## ✔️ 입출력 예
|arr|return|
|---|---|
|[4,3,2,1]|[4,3,2]|
|[10]|[-1]|

<br>

---
<br>


## 👻 코드(1)

```cpp
#include <string>
#include <algorithm>
#include <vector>

using namespace std;

vector<int> solution(vector<int> arr) {
    vector<int> answer;
    vector<int> tmp = arr;
    sort(tmp.begin(), tmp.end());
    for(int i=0; i<arr.size(); i++){
        if(tmp[0] != arr[i])    answer.push_back(arr[i]);
    }
    return answer.empty() ? vector<int>(1,-1) : answer;
}
```

→ 공부를 많이 하지 않은 상태에서 작성한 코드다. 
`tmp`를 정렬하면 최소값이 맨 앞의 원소에 있게 되므로, 반복문을 돌면서 최소값과 `arr`에 있는 값과 비교해 최소값을 `answer`에 `push_back()`했다. 그 후, 반환하는 벡터가 비어있다면 `-1`을 반환하도록 했다. 

---

<br>

## 👻 코드(2)

```cpp
#include <string>
#include <algorithm>
#include <vector>

using namespace std;

vector<int> solution(vector<int> arr) {
    vector<int> answer = arr;
    
    int min = *min_element(answer.begin(), answer.end());
    int pos = find(answer.begin(), answer.end(), min) - answer.begin();
    answer.erase(answer.begin() + pos);
    return answer.empty() ? vector<int>(1, -1) : answer;

}
```

→ 먼저 `min_element()`함수를 통해, 최소값을 알아낸다. <br>

그 후, `find()`함수로 `answer` 속 최소값을 찾고 그 위치를 반환하는데, 이 때 `answer.begin()`을 빼준다. `vector`의 `find()`함수는 인자로 탐색할 범위와 탐색할 원소를 받는데, 해당 원소를 찾으면 반복자를 반환해주고 없으면 `end()`반복자를 반환한다. 반환 받은 반복자를 시작 반환자인 `begin()`을 빼줌으로써 해당 원소의 위치를 구할 수 있다.

이렇게 찾은 위치는 `pos`에 넣고, `erase()`함수를 통해 `pos` 위치의 원소를 지운다.  

---

<br>

👾 벡터의 함수를 사용하므로써, 1번 코드보다 깔끔하고 알아보기 쉬워졌다. 좀 더 공부를 해서 간결하고 다른 사람들이 알아보기 쉬운 코드를 작성하도록 노력해야겠다.