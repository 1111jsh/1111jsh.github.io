---
layout: single
title: "재귀"
categories:
  - Algorithm
tags:
  - recursion
published: true
toc: true
toc_sticky: true
---
----

## 재귀 (recursion)
- 재귀(recursion)는 **어떠한 것을 정의할 때 자기 자신을 참조하는 것을 뜻**한다

### 장점
- 변수를 여러 개 사용할 필요가 없다
- 불필요한 여러 반복문을 사용하지 않기에 코드가 간결해진다

### 단점
- 재귀 함수 사용에는 스택 오버플로우(stack overflow)를 주의해야 한다
- 메서드를 호출하고 매서드가 종료된 이후에 복귀를 위한 컨텍스트 스위칭 비용이 발생
	- 컨텍스트 스위칭  -> 하나의 프로세스가 CPU를 사용 중인 상태에서 다른 프로세스가 CPU를 사용하도록 하기 위해, 이전의 프로세스의 상태(context)를 보관하고 새로운 프로세스의 상태를 적재하는 작업을 말한다
- 매서드를 반복 호출하면서 지역변수, 매개변수, 반환값을 모두 process stack에 저장 한다
	- ->이런 과정이 반복문에 비해서 더 많은 메모리를 사용 하게 된다

### 재귀함수의 조건
- 문제의 크기를 점점 작은 단위로 쪼갤 수 있어야 한다 -> recursive case
- 재귀 호출이 종료되는 시점이 존재해야 한다 -> base case

```java
public int Factorial(int number) {
  if(number <= 1) { // base case
    return 1;
  }
  return number * Factorial(number - 1); // recursive case
}
```
