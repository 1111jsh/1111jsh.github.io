---
layout: single
title: "Java 예외 처리"
categories:
  - Java
tags:
  - Exception Handling
published: true
toc: true
toc_sticky: true
---
----

## 예외 처리(Exception Handling)
- 에러가 발생하는 원인
	- 사용자의 입력 오류
	- 네트워크 연결 끊김
	- 디스크 메모리 공간 부족 등 물리적 한계
	- 개발자의 코드 에러
	- 유효하지 않는 파일 불러오기 등등
- 자바에서는 에러 발생 시점에 따라 에러를 다시 **컴파일 에러(Compile Time Error)**와 **런타임 에러(Run Time Error)**로 구분하고 있다

### 컴파일 에러
- 주로 세미콜론 생략, 오탈자, 잘못된 자료형, 잘못된 포맷 등 문법적인 문제를 가리키는 신택스(syntax) 오류로부터 발생 한다 신택스 에러라고도 한다

### 런타임 에러
- 런타임(코드를 실행하는 과정) 시에 발생하는 에러
- 런타임 에러는 프로그램이 실행될 때에 자바 가상 머신(JVM)에 의해 감지

### 에러(error)와 예외(exception)
- 에러란 한번 발생하면 **복구하기 어려운 수준의 심각한 오류**를 의미하고, 대표적으로 메모리 부족(OutOfMemoryError)와 스택오버플로우(StackOverflowError) 등이 있다
- 예외는 잘못된 사용 또는 코딩으로 인한 상대적으로 미약한 수준의 오류로서 코드 수정 등을 통해 수습이 가능한 오류를 지칭

## 예외 클래스 상속 계층도
- 자바에서는 예외가 발생하면 예외 클래스로부터 객체를 생성하여 해당 인스턴스를 통해 예외처리를 한다
- 자바의 모든 에러와 예외 클래스는 `Throwable` 클래스로부터 확장되며, 모든 예외의 최고 상위클래스는 `Exception` 클래스다

![image.png](https://raw.githubusercontent.com/1111jsh/image/upload/exceptionclass.png)

### 일반 예외 클래스 (Exception)
- 런타임 시 발생하는 `RuntimeException` 클래스와 그 하위 클래스를 제외한 모든 `Exception` 클래스와 그 하위 클래스들을 가리킨다
- 컴파일러가 코드 실행 전에 예외 처리 코드 여부를 검사 한다고 하여 **checked 예외**라 부르기도 한다
- 주로 잘못된 클래스명(ClassNotFoundException)이나 데이터 형식(DataFormatException) 등 사용자편의 실수로 발생하는 경우가 많다

### 실행 예외 클래스(Runtime Exception)
- 런타임 시 발생하는 `RuntimeException` 클래스와 그 하위클래스를 지칭
- 컴파일러가 예외 처리 코드 여부를 검사하지 않는다는 의미에서 **unchecked 예외**라 한다
- 주로 개발자의 실수에 의해 발생하는 경우가 많고, 자바 문법 요소와 관련이 있다
	- 클래스간 형변환 오류(ClassCastException)
	- 벗어난 배열 범위 지정 (ArrayIndexOutOfBoundsException)
	- 값이 null인 참조변수 사용(NullPointerException) 등


### try - catch문
- 자바에서 예외 처리는 `try - catch` 블럭을 통해 구현이 가능

```java
try {
    // 예외가 발생할 가능성이 있는 코드를 삽입
} 
catch (ExceptionType1 e1) {
    // ExceptionType1 유형의 예외 발생 시 실행할 코드
} 
catch (ExceptionType2 e2) {
    // ExceptionType2 유형의 예외 발생 시 실행할 코드
} 
finally {
    // finally 블럭은 옵셔널
    // 예외 발생 여부와 상관없이 항상 실행
}
```

- `try` 블럭 안에는 **예외가 발생할 가능성이 있는 코드를 삽입**
	- 작성한 코드가 예외 없이 정상적으로 실행되면 아래 `catch` 블럭은 실행되지 않고 `finally` 블럭이 실행
- `catch` 블럭은 **예외가 발생하는 경우에 실행되는 코드로, 여러 종류의 예외를 처리**
	- 모든 예외를 받을 수 있는 `Exception` 클래스 하나로 처리도 가능하며, 각기 다른 종류의 예외를 하나 이상의 `catch` 블럭을 사용하여 처리할 수 있
- `finally` 블럭은 옵션으로 필수적으로 포함되지 않아도 되지만, 만약 포함되는 경우에는 예외 발생 여부와 상관없이 항상 실행


### 예외 전가
- `try-catch` 문 외에 예외를 호출한 곳으로 다시 예외를 떠넘기는 방법도 있다

```java
반환타입 메서드명(매개변수, ...) throws 예외클래스1, 예외클래스2, ... {
	...생략...
}
```
- 메서드의 선언부 끝에 아래와 같이 `throws` 키워드와 발생할 수 있는 예외들을 쉽표로 구분하여 나열해 해주면 된다
- `main()` 메서드에서도 `throws` 키워드를 사용해서 예외를 넘길 수 있는 데, 이 경우 자바 JVM이 최종적으로 예외의 내용을 콘솔에 출력하여 예외 처리를 수행 한다

```java
public class ThrowExceptionTest {

    public static void main(String[] args) {
        try {
            throwException();
        } catch (ClassNotFoundException e) {
            System.out.println(e.getMessage());
        }
    }

    static void throwException() throws ClassNotFoundException, NullPointerException {
        Class.forName("java.lang.StringX");
    }
}

//출력값
java.lang.StringX
````
1. `try-catch` 문 안에서 `throwException` 메서드가 호출되지만 잘못된 코드 작성으로 인한 런타임 에러가 발생
2. 이렇게 예외가 발생한 경우, 앞서 사용했던 예외 처리 방식은 잠재적으로 예외가 발생할 수 있는 곳에서 `try-catch` 문을 작성하여 예외 처리를 했지만
3. `throws` 키워드를 사용하여 해당 예외를 발생한 메서드 안에서 처리하지 않고 메서드를 호출한 곳으로 다시 떠넘기고 있다
4. 따라서 이제 예외 처리의 책임은 `throwException` 메서드가 아닌 `main` 메서드가 지게 되었다

### 예외를 의도적으로 발생

```java
public class ExceptionTest {

    public static void main(String[] args) {
        try {
            Exception intendedException = new Exception("의도된 예외 만들기");
            throw intendedException; // throw 키워드 사용
        } catch (Exception e) {
            System.out.println("고의로 예외 발생시키기 성공!");
        }
    }
    
}

//출력값
고의로 예외 발생시키기 성공!
```