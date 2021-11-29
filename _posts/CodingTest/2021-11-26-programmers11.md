---
title: "[프로그래머스] 직사각형 별찍기(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-26
---
## 🔥 문제
이 문제에는 표준 입력으로 두 개의 정수 n과 m이 주어집니다. 별(*) 문자를 이용해 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 출력해보세요.

---
## ✔️ 제한사항

- n과 m은 각각 1000 이하인 자연수입니다.

---
## ✔️ 입출력 예

|입력|출력|
|---|---|
|5 3|***** <br> ***** <br> *****|

---
## 🤔 문제 해설

가로 길이 `n`, 세로 길이 `m` 를 입력 받는다.
`m`번 만큼 반복문을 돌면서 `n`개의 `"*"`를 출력하고 다음 줄로 넘어간다.

이렇게 중첩 반복문을 사용해서 문제를 해결할 수 있다.

---
## 👻 코드(1)

```cpp
#include <iostream>

using namespace std;

int main(void) {
    int n, m;
    cin >> n >> m;

    for(int i = 0; i < m; i++){
        for(int j = 0; j < n; j++) 
            cout << "*";
        cout << '\n';
    }
    return 0;
}
```

---
## 👻 코드(2)
```cpp
#include <iostream>

using namespace std;

int main(void) {
    int n, m;
    cin >> n >> m;

    string s;

    s.append(n, '*');

    for (int i = 0; i < m; ++i)
        cout << s << '\n';
    return 0;
}
```

이런 방법을 사용할 수도 있다. 
1번 코드의 경우, 중첩 반복문으로 시간복잡도가 `O(n^2)`이다. 그래서 이 for문을 줄이고 싶은데, 이것은 문자열을 조금 더 이용해보면 된다.

문자열 `s`을 생성하고 `n`만큼 `"*"`를 `append` 하고, 이 문자열을 `m`만큼 출력한다. 


