---
title: "[프로그래머스] K번째 수(C++)"
categories:
- CodingTest
tags:
- [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-23
---

## 🔥 문제
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.<br>
예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면
1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

---

## ✔️ 제한사항
- array의 길이는 1 이상 100 이하입니다.
- array의 각 원소는 1 이상 100 이하입니다.
- commands의 길이는 1 이상 50 이하입니다.
- commands의 각 원소는 길이가 3입니다.

---

## ✔️ 입출력 예

|array|commands|return|
|---|---|---|
|[1,5,2,6,3,7,4]|[[2,5,3], [4,4,1], [1,7,3]]|[5,6,3]

→ [설명]<br>

[1, 5, 2, 6, 3, 7, 4]를 2번째부터 5번째까지 자른 후 정렬합니다. [2, 3, 5, 6]의 세 번째 숫자는 5입니다.
<br>[1, 5, 2, 6, 3, 7, 4]를 4번째부터 4번째까지 자른 후 정렬합니다. [6]의 첫 번째 숫자는 6입니다.
<br>[1, 5, 2, 6, 3, 7, 4]를 1번째부터 7번째까지 자릅니다. [1, 2, 3, 4, 5, 6, 7]의 세 번째 숫자는 3입니다.

---

## 🤔 문제 풀이

문제를 정리헤보면,
i, j, k 번째는 0부터 시작하는 것이 아니라 `1`부터 시작하는 것이다.
0부터 시작하는 것으로 헷갈리지 않도록 **주의**해야 한다.

각 케이스에서 나온 범위(i~j)의 원소를 어떻게 할지에 따라서 두 가지 방법으로 생각해보았다.

1. 범위 원소 배열을 따로 두고 그곳에 범위 원소만을 할당하고, 정렬(sort함수 이용)한 후에 k번째 원소를 찾는 것.
2. 원소 전체를 임의의 벡터 v에 할당하고 iterator로 범위를 가리키고 그 범위만 정렬하고, k번째 원소를 찾는 것.

---

## 👻 내 코드(1)

```cpp
#include <vector>
#include <algorithm>

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    vector<int> v;
    for(int i=0;i<commands.size();i++){
        for(int j=commands[i][0]-1;j<commands[i][1];j++){
            v.push_back(array[j]);
        }
        sort(v.begin(),v.end());
        answer.push_back(v[commands[i][2]-1]);
        v.clear();
    }
    return answer;
}
```

입력값으로 받는 2차원 배열 commands 에는 row에는 3가지 값이 있는데, 각각 (i, j, k)로 범위와 몇번째 값을 출력할지를 정한다. 중첩 for문을 통해 i~j 범위의 원소를 벡터 v에 할당했다. 

그 후, sort 함수를 통해 정렬을 하고 벡터 v의 k번째 값을 answer 에 넣어준다. v에 push_back()으로 넣었으므로 만약 v의 원소값을 초기화(clear())하지 않으면 다음 row 값이 추가된다. 그러므로 반복문이 다시 시작되기 전에 v를 초기화해준다.

`vector 2차원 배열의 row 개수는 v.size(), col의 개수는 v[0].size()`

이 방법은 코딩 문제를 풀기 시작한 초기에 생각했던 방법이다.
> 이 방법도 프로그래머스 테스트를 통과한다 '!'


## 👻 내 코드(2)
```cpp
#include <vector>
#include <algorithm>

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    vector<int> v;
    for(int i=0; i<commands.size(); i++){
        v = array;
        sort(v.begin()+ commands[i][0]-1, v.begin()+commands[i][1]);
        answer.push_back(v[commands[i][0] + commands[i][2] -2]);
    }
    return answer;
}
```

1번째 방법과 달리, 중첩 for문이 없다. 이 방법은 i, j 범위 원소를 따로 빼지 않고 전체 원소가 있는 배열에서 해당 범위만 정렬해서 k번째 원소를 찾는다. 

v = array; 이 부분이 왜 있는지 궁금할 수 있는데, 1번째 방법(v.clear())처럼 초기화를 해준 것이다. 

각 케이스를 for문으로 돌면서 범위 원소를 정렬해주는데, 만약 이 부분이 없다면 정렬된 것이 초기화되지 않기 때문에 정렬된 상태에서 해당 케이스를 진행하게 된다!

> 아무래도 for문이 2개가 돌아가는 1번째 방법보다는 2번째 방법이 좀 더 효율적이지 않을까 싶다. (아니라면 댓글로 알려주세요..!🤭)
