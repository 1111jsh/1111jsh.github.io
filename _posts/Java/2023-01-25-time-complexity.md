---
layout: single
title: "시간 복잡도"
categories:
  - java
tags:
  - time complexity
published: true
toc: true
toc_sticky: true
---
----

## 시간복잡도
- 시간 복잡도는 입력 크기 측면에서 알고리즘이 실행되는 데 걸리는 시간을 설명하는 방법
- 시간 복잡도를 표현하는 가장 일반적인 방법은 알고리즘이 수행하는 작업 수의 상한을 설명하는 Big-O 표기법을 사용하는 것
	- 예를 들어 시간 복잡도가 O(n)인 알고리즘은 입력(n)의 크기에 비례하는 시간이 걸리고 시간 복잡도가 O(1)인 알고리즘은 입력 크기에 관계없이 일정한 시간이 걸린다

![image.png](https://raw.githubusercontent.com/1111jsh/image/upload/big-o.png)

![image.png](https://raw.githubusercontent.com/1111jsh/image/upload/timecomplexity.png)

![image.png](https://raw.githubusercontent.com/1111jsh/image/upload/timecomplexity2.png)

### O(1)
- O(1)은 일정한 시간 복잡도(constant complexity)이다
- 입력 값의 크기에 관계 없이 시간이 늘어나지 않는다

```java
public int O_1_algorithm(int[] arr, int index) {
  return arr[index];
}

int[] arr = new int[]{1,2,3,4,5};
int index = 1;
int results = O_1_algorithm(arr, index);
System.out.println(results); // 2
```

### O(log n)
- O(log n)은 대수적 시간 복잡도(logarithmic complexity)이다
- 입력 크기에 따라 연산 수가 대수적으로 증가함을 의미 한다

```java
public int binarySearch(int[] arr, int x) {
    int left = 0;
    int right = arr.length - 1;
    while (left <= right) {
        int mid = (left + right) / 2;
        if (arr[mid] == x) {
            return mid;
        } else if (arr[mid] < x) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}
// 이 알고리즘의 시간 복잡도는 O(log n)이며 여기서 n은 입력 배열의 크기이다
```


### O(n)
- O(n)은 선형 시간 복잡도(linear time complexity)이다
- 작업 수가 입력 크기에 정비례 한다

```java
public void O_n_algorithm(int n) {
	for(int i = 0; i < n; i++) {
	// do something for 1 second
	}
}

public void another_O_n_algorithm(int n) {
	for(int i = 0; i < n * 2; i++) {
	// do something for 1 second
	}
}
```

### O(n log n)
- O(n log n)은 로그 선형 시간 복잡도(log-linear time complexity) 이다
- 작업 수가 입력 크기에 입력 크기를 곱한 로그 함수임을 의미 한다

```java
public static void mergeSort(int[] arr) {
    if (arr.length > 1) {
        int mid = arr.length / 2;
        int[] left = Arrays.copyOfRange(arr, 0, mid);
        int[] right = Arrays.copyOfRange(arr, mid, arr.length);

        mergeSort(left);
        mergeSort(right);

        merge(arr, left, right);
    }
}

private static void merge(int[] arr, int[] left, int[] right) {
    int i = 0, j = 0, k = 0;
    while (i < left.length && j < right.length) {
        if (left[i] < right[j]) {
            arr[k++] = left[i++];
        } else {
            arr[k++] = right[j++];
        }
    }
    while (i < left.length) {
        arr[k++] = left[i++];
    }
    while (j < right.length) {
        arr[k++] = right[j++];
    }
}
// 병합 정렬 알고리즘의 시간 복잡도는 O(n log n) 이다 여기서 n은 입력 배열의 크기
// 입력 배열을 두 개의 작은 배열로 나누고 각 배열을 재귀적으로 정렬한 다음 선형 O(n) 작업에서 다시 병합 한다
// 입력 배열을 더 작은 배열로 나누는 과정은 대수적으로 수행되므로 알고리즘의 시간 복잡도는 O(n log n)
```

### O(n^2)
- O(n^2)는 2차 시간 복잡도(quadratic time complexity) 이다
- 작업 수가 입력 크기의 제곱에 비례한다

```java
public void O_quadratic_algorithm(int n) {
	for(int i = 0; i < n; i++) {
		for(int j = 0; j < n; j++) {
			// do something for 1 second
		}
	}
}
```

### O(2^n)
- O(2^n)은 기하급수적 시간 복잡도(exponential time complexity) 이다
- 입력 크기가 증가할 때마다 작업 수가 두 배가 된다

```java
public int fibonacci(int n) {
	if(n <= 1) {
		return 1;
	}
	return fibonacci(n - 1) + fibonacci (n - 2);
}
```

| Name     | constant | logarithmic | linear | log-linear  | quadratic | exponential |
| -------- | -------- | ----------- | ------ | ---------- | --------- | ---------- |
| Notation | O(1)     | O(log n)    | O(n)   | O(n log n) | O(n^2)    | O(c^n)     |



>**Reference**
>> [bigocheatsheet](https://www.bigocheatsheet.com/)