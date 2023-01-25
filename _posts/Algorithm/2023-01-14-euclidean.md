---
layout: single
title: "유클리드 호제법"
categories:
  - Algorithm
tags:
  - Euclidean
published: true
toc: true
toc_sticky: true
---
----

## 최대 공약수 (Greatest Common Divisor, GCD)
- 최대 공약수란 두 수 이상의 여러 수 의 공약수 중 최대인 수를 말한다
- 최대 공약수는 각 정수의 약수를 구하고, 공통되는 약수를 구하고, 가장 큰 하나를 구하면 얻을 수 있다
	- 그 밖에 소인수분해를 통한 방법과 유클리드 호제법을 통한 방법이 있다


```java
192, 72의 최대공약수 소인수분해
192 = 2^6 * 3
72 = 2^3 * 3^2
최대공약수 = 2^3 * 3 = 24
```

다만 소인수분해는 효율적으로 빠른 시간 내에 하는 방법은 알려지지 않았다

## 유클리드 호제법 (Euclidean algorithm)
- 2개의 자연수의 최대공약수를 구하는 알고리즘의 하나 이다
- 호제법이란 두 수가 서로 상대방 수를 나누어 결국 원하는 수를 얻는 알고리즘을 말한다

```java
유클리드 호제법
조건 : a % b = r, (a >= b, 0 <= r < b) 
a와 b의 최대공약수를 a,b라고 하면 다음이 성립
(a, b) = (b, r)
ex) 1071과 1029의 최대공약수
(1071, 1029) = (1029, 42) = (42, 21) = (21, 0) = 21
```

```java
public static int gcd(int a, int b) {
	if (a % b == 0) return b;
	return gcd(b, a % b);
}
// 재귀를 이용한 최대공약수 구하기
```

>**Reference**
>> [TCP스쿨](http://www.tcpschool.com/codingmath/common)  
>> [wikidepia](https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95)