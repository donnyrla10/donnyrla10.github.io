---
title: "[프로그래머스] 최대공약수와 최소공배수(C++)"
categories: 
    - CodingTest
tags:
    - [Programmers, Algorithm, C++, CodingTest]
toc: true
toc_sticky: true
date: 2021-11-29
---

## 🔥 문제
두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.

<br>

---
<br>

## ✔️ 제한사항
- 두 수는 1이상 1,000,000이하의 자연수입니다.

<br>

---
<br>

## ✔️ 입출력 예
|n|m|return|
|---|---|---|
|3|12|[3,12]|
|2|5|[1,10]|


<br>

---
<br>

## 🤔 문제 해설

최대공약수: 두 자연수에 대하여 공통된 약수 중 가장 큰 자연수<br>
최소공배수: 두 자연수에 대하여 공통된 배수 중 가장 작은 자연수

![최대공약수,최소공배수](_posts/images/최대공약수최소공배수.jpg)


<br>

---
<br>

## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

vector<int> solution(int n, int m) {
    vector<int> answer;
    int min = n < m ? n : m;
    int a = 1, b = 1;
    
    for(int i = min; i > 0; i--){
        //최소공배수
        if(i == 1){
            b = a * n * m; 
            break;
        }
        //최대공약수
        if(n % i == 0 && m % i == 0){
            a *= i;   
            n /= i;   
            m /= i;  
        }
    }
    answer.push_back(a);
    answer.push_back(b);
    return answer;
}
```

(코드 1) 입력받은 n, m 중에서 작은 값을 min 변수에 넣는다. min을 기준으로 반복문을 수행하면서 최대공약수와 최소공배수를 구할 것이다.

min으로 n, m 을 나눠서 나누어 떨어지는 수가 있다면 a에 곱해준다. 그리고, n 과 m 은 나눠진 값으로 업데이트 시켜준다. 이렇게 곱한 값이 최대공약수가 된다.
그 후, 최소공배수는 최대공약수와 업데이트된 n과 m 값을 곱해주면 된다.

---

<br>

## 👻 코드(1)

```cpp
#include <string>
#include <vector>

using namespace std;

int gcd(int a, int b) { // 단, a가 b보다 커야함.
    int r;
    while ((a % b) > 0)  {
        r = a % b; //나머지
        a = b;
        b = r;
    }
    return b;
}

vector<int> solution(int n, int m) {
    vector<int> answer;
    int gcd_result = n > m ? gcd(n,m) : gcd(m,n);
    answer.push_back(gcd_result);
    answer.push_back((n*m)/gcd_result);
    return answer;
}
```

(코드 2) 이런 방식으로 할 수도 있지만, 최대공약수는 유클리드 호제법을 사용하면 더욱 간결하게 코드를 작성할 수 있다.

> 유클리드 호제법이란, 
2개의 자연수 또는 정식의 최대공약수(Greatest Common Divisor)를 구하는 알고리즘

→ 2개의 자연수 a, b(a>b)에 대해서 a를 b로 나눈 나머지를 r이라 하면, a와 b의 최대공약수는 b와 r의 최대공약수와 같다.
이 성질에 따라, b를 r로 나눈 나머지 r'를 구하고, 다시 r을 r'로 나눈 나머지를 구하는 과정을 반복하여 나머지가 0이 되면 그 나누는 수가 a와 b의 최대공약수이다

```cpp
int gcd(int a, int b) { // 단, a가 b보다 커야함.
    int r;
    while ((a % b) > 0)  { //나머지가 0이 아니라면 반복문 수행
        r = a % b; //나머지
        a = b;
        b = r;
    }
    return b;
}
```
이 알고리즘을 통해 최대공약수를 구하고, 그 값을 이용해 최소공배수를 구할 수 있다.

---

<br>