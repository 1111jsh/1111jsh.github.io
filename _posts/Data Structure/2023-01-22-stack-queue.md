---
layout: single
title: "Stack, Queue, Deque"
categories:
  - DataStructure
tags:
  - Stack
  - Queue
  - Deque
published: true
toc: true
toc_sticky: true
---
----

## Stack
- Stack은 후입선출(Last In First Out, LIFO) 원칙을 따르는 선형 데이터 구조다
- 후입선출은 Stack에 추가된 마지막 요소가 제거되는 첫 번째 요소를 의미 한다
- Stack은 배열 또는 LinkedList를 사용하여 구현할 수 있다
- Stack은 깊이우선탐색(DFS)과 같은 다양한 알고리즘에 유용하며 프로그래밍 언어의 호출 스택 및 많은 소프트웨어 애플리케이션의 실행 취소/다시 실행(undo/redo) 기능과 같은 다른 데이터 구조의 구현에도 사용 된다

```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();

        // Adding elements to the stack
        stack.push(1);
        stack.push(2);
        stack.push(3);
        stack.push(4);

        // Removing elements from the stack
        System.out.println(stack.pop());  // 4
        System.out.println(stack.pop());  // 3
        System.out.println(stack.pop());  // 2

        // Peeking at the top element
        System.out.println(stack.peek());  // 1

        // Checking if the stack is empty
        System.out.println(stack.empty());  // false
    }
}
```

## Queue
- Queue는 선입선출(First In First Out, FIFO) 원칙을 따르는 선형 데이터 구조다
- 선입선출은 Queue에 추가된 첫 번째 요소가 제거되는 첫 번째 요소 이다
- Queue는 배열 또는 LinkedList를 사용하여 구현할 수 있다
- Queue는 너비우선탐색(BFS)과 같은 다양한 알고리즘에 유용하며 운영 체제의 작업 스케줄러 및 프린터의 인쇄 스풀러와 같은 데이터 구조에도 사용 된다

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();

        // Adding elements to the queue
        queue.add("John");
        queue.add("Mike");
        queue.add("Sara");

        // Removing elements from the queue
        System.out.println(queue.remove());  // John
        System.out.println(queue.remove());  // Mike

        // Peeking at the front element
        System.out.println(queue.peek());  // Sara

        // Checking if the queue is empty
        System.out.println(queue.isEmpty());  // false
    }
}
```

## Deque
- Double-Ended Queue (Duque)는 Queue의 앞과 뒤 모두에서 요소를 추가하고 제거할 수 있는 선형 데이터 구조다. Stack과 Queue의 조합으로 두 데이터 구조의 특성을 모두 활용할 수 있다

```java
import java.util.Deque;
import java.util.LinkedList;

public class DequeExample {
    public static void main(String[] args) {
        Deque<String> deque = new LinkedList<>();

        // Adding elements to the deque
        deque.addFirst("John");
        deque.addLast("Mike");
        deque.offerFirst("Sara");
        deque.offerLast("Tom");

        // Removing elements from the deque
        System.out.println(deque.removeFirst());  // Sara
        System.out.println(deque.removeLast());  // Tom

        // Peeking at the front and back element
        System.out.println(deque.peekFirst());  // John
        System.out.println(deque.peekLast());  // Mike

        // Checking if the deque is empty
        System.out.println(deque.isEmpty());  // false
    }
}
```
