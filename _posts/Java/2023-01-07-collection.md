---
layout: single
title: "Java 컬렉션"
categories:
  - Java
tags:
  - Collection
published: true
toc: true
toc_sticky: true
---
----

## 컬렉션 프레임워크(Collection Framework)
- Java에서 데이터를 저장하기 위해 자료 구조를 바탕으로 객체들을 효율적으로 추가, 삭제, 검색할 수 있도록 컬렉션을 만들고, 관련된 인터페이스와 클래스를 포함시켜 만들은 것

![image.png](https://raw.githubusercontent.com/1111jsh/image/upload/collection.png)



**List**
-   List는 **데이터의 순서가 유지되며, 중복 저장이 가능**한 컬렉션을 구현하는 데에 사용
-   ArrayList, Vector, Stack, LinkedList 등이 List 인터페이스를 구현 한다  

**Queue**
- Queue는 **FIFO(First Input First Output, 선입선출)** 구조로 먼저 입력된 자료를 먼저 출력

**Set**
-   Set은 **데이터의 순서가 유지되지 않으며, 중복 저장이 불가능**한 컬렉션을 구현하는 데에 사용    
-   HashSet, TreeSet 등이 Set 인터페이스를 구현 한다

**Map**
-   Map은 **키(key)와 값(value)의 쌍으로 데이터를 저장**하는 컬렉션을 구현하는 데에 사용    
-   **데이터의 순서가 유지되지 않으며, 키는 값을 식별하기 위해 사용되므로 중복 저장이 불가능하지만, 값은 중복 저장이 가능 하다**
-   HashMap, HashTable, TreeMap, Properties 등

### Collection 인터페이스

| 기능     | 리턴 타입 | 메소드                                        | 설명                                                                                         |
| -------- | --------- | --------------------------------------------- | -------------------------------------------------------------------------------------------- |
| 객체추가 | boolean   | add(Object o), addAll(Collection c)           | 주어진 객체 및 컬렉션의 객체들을 컬렉션에 추가                                               |
| 객체검색 | boolean   | contains(Object o), containsAll(Collection c) | 주어진 객체 및 컬렉션이 저장되어 있는지 여부를 리턴                                          |
|          | Iterator  | iterator()                                    | 컬렉션의 iterator를 리턴                                                                     |
|          | boolean   | equals(Object o)                              | 컬렉션이 동일한지 여부를 확인                                                                |
|          | boolean   | isEmpty()                                     | 컬렉션이 비어있는지 여부를 확인                                                              |
|          | int       | size()                                        | 저장되어 있는 전체 객체 수를 리턴                                                            |
| 객체삭제 | void      | clear()                                       | 컬렉션에 저장된 모든 객체를 삭제                                                             |
|          | boolean   | remove(Object o), removeAll(Collection c)     | 주어진 객체 및 컬렉션을 삭제하고 성공 여부를 리턴                                            |
|          | boolean   | retainAll(Collection c)                       | 주어진 컬렉션을 제외한 모든 객체를 컬렉션에서 삭제하고, 컬렉션에 변화가 있는지의 여부를 리턴 |
| 객체변환 | Object[]  | toArray()                                     | 컬렉션에 저장된 객체를 객체배열(Object [])로 반환                                            |
|          | Object[]  | toArray(Object[] a)                           | 주어진 배열에 컬렉션의 객체를 저장해서 반환                                                                                             |

## Iterator
- 컬렉션에 저장된 요소들을 순차적으로 읽어오는 역할
- Collection 인터페이스에 정의된 `iterator()`를 호출하면, Iterator 타입의 인스턴스가 반환 된다
	- Collection 인터페이스를 상속받는 List와 Set 인터페이스를 구현한 클래스들은 `iterator()` 메서드를 사용 가능 하다

**Iterator 인터페이스에 정의된 메서드**

| 메서드    | 설명                                                                                                            |
| --------- | --------------------------------------------------------------------------------------------------------------- |
| hasNext() | 읽어올 객체가 남아 잇으면 true를 리턴, 없으면 false를 리턴                                                      |
| next()    | 컬렉션에서 하나의 객체를 읽어온다 (next()를 호출하기 전에 hasNext()를 통해 읽어올 다음 요소가 있는지 먼저 확인) |
| remove()  | next()를 통해 읽어온 객체를 삭제 한다 (next()를 호출한 다음 remove()를 호출)                                                                                                                |

```java
ArrayList<String> list = ...;
Iterator<String> iterator = list.iterator();

while(iterator.hasNext()) {     // 읽어올 다음 객체가 있다면 
	String str = iterator.next(); // next()를 통해 다음 객체를 읽어옵니다. 
	if (str.equals("str과 같은 단어")) {
		iterator.remove();  // 해당 객체를 컬렉션에서 제
	}
}
// Iterator를 사용하지 않아도, for-each문 이용해 전체 객체를 반복 가능
ArrayList<String> list = ...;
for(String str : list) {
	...
}
```

## List\<E>
- List 인터페이스는 배열과 같이 객체를 일렬로 늘어놓은 구조를 가진다
- 객체를 인덱스로 관리하기 때문에 **객체를 저장하면 자동으로 인덱스가 부여되고, 인덱스로 객체를 검색, 추가, 삭제할 수 있는 등의 여러 기능을 제공한다**

| 기능     | 리턴타입     | 메서드                                  | 설명                                                                                             |
| -------- | ------------ | --------------------------------------- | ------------------------------------------------------------------------------------------------ |
| 객체추가 | void         | add(int index, Object element)          | 주어진 인덱스에 객체를 추가                                                                      |
|          | boolean      | addAll(int index, Collection c)         | 주어진 인덱스에 컬렉션을 추가                                                                    |
|          | Object       | set(int index, Object element)          | 주어진 위치에 객체를 저장                                                                        |
| 객체검색 | Object       | get(int index)                          | 주어진 인덱스에 저장된 객체를 반환                                                               |
|          | int          | indexOf(Object o), lastIndex(Object o)  | 순방향, 역방향으로 탐색하여 주어진 객체의 위치를 반환                                            |
|          | ListIterator | listIterator(), listIterator(int index) | List의 객체를 탐색할 수 있는 ListIerator 반환. 주어진 index부터 탐색할 수 있는 ListIterator 반환 |
|          | List         | subList(int fromIndex, int toIndex)     | fromIndex부터 toIndex에 있는 객체를 반환                                                         |
| 객체삭제 | Object       | remove(int index)                       | 주어진 인덱스에 저장된 객체를 삭제하고 삭제된 객체를 반환                                        |
|          | boolean      | remove(Object o)                        | 주어진 객체를 삭제                                                                               |
| 객체정렬 | void         | sort(Comparator c)                      | 주어진 비교자(comparator)로 List를 정렬                                                          |

### ArrayList
- ArrayList는 List 인터페이스를 구현한 클래스로, 컬렉션 프레임워크에서 가장 많이 사용
- 기능적으로는 Vector와 동일하지만 기존의 Vector를 개선한 것이므로, Vector보다는 주로 ArrayList를 사용
- 객체가 저장 용량을 초과하면 자동으로 저장 용량이 늘어난다
- List 자료구조 특성을 이어받아 데이터가 연속적으로 존재하여 데이터의 순서를 유지 한다

```java
ArrayList<타입 매개변수> 객체명 = new ArrayList<타입 매개변수>(초기 저장 용량);

ArrayList<String> container1 = new ArrayList<String>();
// String 타입의 객체를 저장하는 ArrayList 생성
// 초기 용량이 인자로 전달되지 않으면 기본적으로 10으로 지정됩니다. 

ArrayList<String> container2 = new ArrayList<String>(30);
// String 타입의 객체를 저장하는 ArrayList 생성
// 초기 용량을 30으로 지정하였습니다. 
```
- ArrayList에 객체를 추가하면 인덱스 0부터 차례대로 저장
- 특정 인덱스의 객체를 제거하면, 바로 뒤 인덱스부터 마지막 인덱스까지 모두 앞으로 1씩 당겨진다

```java
public class ArrayListExample {
	public static void main(String[] args) {

		// ArrayList를 생성하여 list에 할당
		ArrayList<String> list = new ArrayList<String>();

		// String 타입의 데이터를 ArrayList에 추가
		list.add("Java");
		list.add("egg");
		list.add("tree");

		// 저장된 총 객체 수 얻기
		int size = list.size(); 

		// 0번 인덱스의 객체 얻기
		String skill = list.get(0);

		// 저장된 총 객체 수 만큼 조회
		for(int i = 0; i < list.size(); i++){
			String str = list.get(i);
			System.out.println(i + ":" + str);
		}

		// for-each문으로 순회 
		for (String str: list) {
			System.out.println(str);
		}		

		// 0번 인덱스 객체 삭제
		list.remove(0);
	}
}
```

### LinkedList
- LinkedList 컬렉션은 데이터를 효율적으로 추가, 삭제, 변경하기 위해 사용
- 데이터가 불연속적으로 존재하며, 이 데이터를 서로 연결 되어 있다
- LinkedList의 각 요소(node)들은 자신과 연결된 이전 요소 및 다음 요소의 주소값과 데이터로 구성되어 있다
- LinkedList에서 데이터의 삭제는 링크를 끊어주는 방식. 처리 속도가 빠르다

```java
public class LinkedListExample {
	public static void main(String[] args) {
		
		// Linked List를 생성하여 list에 할당
		LinkedList<String> list = new LinkedList<>();

		// String 타입의 데이터를 LinkedList에 추가
		list.add("Java");
		list.add("egg");
		list.add("tree");

		// 저장된 총 객체 수 얻기
		int size = list.size(); 

		// 0번 인덱스의 객체 얻기
		String skill = list.get(0);

		// 저장된 총 객체 수 만큼 조회
		for(int i = 0; i < list.size(); i++){
			String str = list.get(i);
			System.out.println(i + ":" + str);
		}

		// for-each문으로 순회
		for (String str: list) {
			System.out.println(str);
		}		

		// 0번 인덱스 객체 삭제
		list.remove(0);
	}
}
```

### ArrayList와 LinkedList 차이

**ArrayList 강점**
-   **데이터를 순차적으로 추가하거나 삭제하는 경우**
    -   순차적으로 추가한다는 것은 0번 인덱스에서부터 데이터를 추가하는 것을 의미
    -   순차적으로 삭제한다는 것은 마지막 인덱스에서부터 데이터를 삭제하는 것을 의미
-   **데이터를 읽어 들이는 경우**
    -   인덱스를 통해 바로 데이터에 접근할 수 있으므로 검색이 빠르다

**ArrayList 단점**
-   **중간에 데이터를 추가하거나, 중간에 위치하는 데이터를 삭제하는 경우**    
    -   추가 또는 삭제 시, 해당 데이터의 뒤에 위치한 값들을 뒤로 밀어주거나 앞으로 당겨주어야 한다
- **데이터를 중간에 추가하거나 삭제하는 경우, LinkedList는 ArrayList보다 빠른 속도를 보인다**

**LinkedList 강점**
-   **중간에 위치하는 데이터를 추가하거나 삭제하는 경우**
    - 데이터를 중간에 추가하는 경우, Prev와 Next의 주소값만 변경하면 되므로, 다른 요소들을 이동시킬 필요가 없다

**데이터의 잦은 변경이 예상된다면 LinkedList를, 데이터의 개수가 변하지 않는다면 ArrayList를 사용**하는 것이 좋다

## Set\<E>
- Set은 요소의 중복을 허용하지 않고, 저장 순서를 유지하지 않는 컬렉션 이다

| 기능     | 리턴타입 | 메서드             | 설명                                                            |
| -------- | -------- | ------------------ | --------------------------------------------------------------- |
| 객체추가 | boolean  | add(Object o)      | 주어진 객체를 추가하고, 성공하면 true, 중복 객체면 false를 반환 |
| 객체검색 | boolean  | contains(Object o) | 주어진 객체가 Set에 존재하는지 확인한다                         |
|          | boolean  | isEmpty()          | Set이 비어있는지 확인                                           |
|          | Iterator | Iterator()         | 저장된 객체를 하나씩 읽어오는 반복자를 리턴                     |
|          | int      | size()             | 저장되어 있는 전체 객체의 수를 리턴                             |
| 객체삭제 | void     | clear()            | Set에 저장되어 있는 모든 객체를 삭제                            |
|          | boolean  | remove(Object o)   | 주어진 객체를 삭제                                              |

### HashSet
- Set 인터페이스를 구현한 가장 대표적인 컬렉션 클래스
- 중복된 값을 허용하지 않으며, 저장 순서를 유지하지 않는다
	1. `add(Object o)`를 통해 객체를 저장 할 때, 객체의 해시코드를 `hasCode()`메서드를 통해 얻어낸다
	2. Set이 가지고 있는 모든 객체의 해시코드를 `hasCode()`메서드를 통해 얻어낸다
	3. 1번과 2번의 해시코드를 비교 검사 한다, 중복이 존재하면 5번으로
	4. 중복이 없으면 Set에 객체가 추가되며 `add(Object o)`메서드가 `true`를 리턴 한다
	5. `equals()`메서드를 통해 객체를 비교
		-  `true`가 리턴되면 중복이므로 Set에 추가되지 않는며 `add(Object o)`가 `false`를 리턴
		-  `false`가 리턴되면 Set에 객체 추가되며, `add(Object o)`가 `true`를 리턴

### TreeSet
- TreeSet은 이진 탐색 트리 형태로 데이터를 저장
- 이진 탐색 트리(Binary Search Tree)란 하나의 부모 노드가 최대 두 개의 자식 노드와 연결되는 이진 트리의 일종, 정렬과 검색에 특화된 자료 구조
- 이진 탐색 트리는 모든 왼쪽 자식의 값이 루트나 부모보다 작고, 모든 오른쪽 자식의 값이 루트나 부모보다 큰 값을 가지는 특징이 있

## Map\<K, V>
- Map 인터페이스는 **키(key)와 값(value)으로 구성된 객체를 저장하는 구조**
- 이 객체를 **Entry객체** 라고 하는데, 이 **Entry 객체는 키와 값을 각각 Key 객체와 Value 객체로 저장**
- 키는 중복 저장이 불가능 하지만, 값은 중복 저장이 가능하다
	- 기본에 저장된 키와 동일한 키로 값을 저장하면, 기존의 값이 새로운 값으로 대치 된다
- Map 인터페이스를 구현한 클래스에는 HashMap, Hashtable, TreeMap, SortedMap 등이 있다

| 기능     | 리턴 타입  | 메서드                        | 설명                                                                                                                                      |
| -------- | ---------- | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 객체추가 | Object     | put(Object key, Object value) | 주어진 키로 값을 저장. 해당 키가 새로운 키일 경우 null을 리턴하지만, 동일한 키가 있을 경우 기존의 값을 대체하고 대체되기 이전의 값을 리턴 |
| 객체검색 | boolean    | containsKey(Object key)       | 주어진 키가 있으면 true, 없으면 false를 리턴                                                                                              |
|          | boolean    | containsValues(Object value)  | 주어진 값이 있으면 true, 없으면 false를 리턴                                                                                              |
|          | set        | entrySet()                    | 키와 값의 쌍으로 구성된 모든 Map.Entry객체를 Set에 담아 리턴                                                                              |
|          | Object     | get(Object key)               | 주어진 키에 해당하는 값을 리턴                                                                                                            |
|          | boolean    | isEmpty()                     | 컬렉션이 비어 있는지 확인 한다                                                                                                            |
|          | Set        | keySet()                      | 모든 키를 Set 객체에 담아서 리턴                                                                                                          |
|          | int        | size()                        | 저장된 Entry 객체의 총 개수를 리턴                                                                                                        |
|          | Collection | values()                      | 저장된 모든 값을 Collection에 담아서 리턴                                                                                                 |
| 객체삭제 | void       | clear()                       | 모든 Map.Entry를 삭제                                                                                                                     |
|          | Object     | remove(Object key)            | 주어진 키와 일치하는 Map.Entry를 삭제하고 값을 리턴                                                                                                                                          |

### HashMap
- HashMap은 해시 함수를 통해 '키'와 '값'이 저장되는 위치를 결정하므로, 사용자는 그 위치를 알 수 없고, **삽입되는 순서와 위치 또한 관계가 없다**
- HashMap은 이름 그대로 해싱(Hashing)을 사용하기 때문에 **많은 양의 데이터를 검색하는 데 있어서 뛰어난 성능**을 보인다

**Map.Entry 인터페이스 메서드**

| 리턴 타입 | 메서드                 | 설명                          |
| --------- | ---------------------- | ----------------------------- |
| boolean   | equals(Object o)       | 동일한 Entry 객체인지 비교    |
| Object    | getKey()               | Entry객체의 key객체를 반환    |
| Object    | getValue()             | Entry객체의 Value 객체를 반환 |
| int       | hashCode()             | Entry객체의 해시코드를 반환   |
| Object    | setValue(Object value) | Entry객체의 Value객체를 인자로 전달한 value객체로 바꾼다                              |

```java
HashMap<String, Integer> hashmap = new HashMap<>();
// HashMap을 생성할 때에는 키와 값의 타입을 따로 지정 해야 한다
```

```java
import java.util.*;

public class HashMapExample {
    public static void main(String[] args) {

	    // HashMap 생성
        HashMap<String, Integer> map = new HashMap<>();

        // Entry 객체 저장
        map.put("피카츄", 85);
        map.put("꼬부기", 95);
        map.put("야도란", 75);
        map.put("파이리", 65);
        map.put("피존투", 15);

        // 저장된 총 Entry 수 얻기
        System.out.println("총 entry 수: " + map.size());

        // 객체 찾기
        System.out.println("파이리 : " + map.get("파이리"));
				
        // key를 요소로 가지는 Set을 생성 -> 아래에서 순회하기 위해 필요 
        Set<String> keySet = map.keySet();

        // keySet을 순회하면서 value를 읽어온다 
        Iterator<String> keyIterator = keySet.iterator();
        while(keyIterator.hasNext()) {
            String key = keyIterator.next();
            Integer value = map.get(key);
            System.out.println(key + " : " + value);
        }

        // 객체 삭제
        map.remove("피존투");

        System.out.println("총 entry 수: " + map.size());

        // Entry 객체를 요소로 가지는 Set을 생성 -> 아래에서 순회하기 위해 필요 
        Set<Map.Entry<String, Integer>> entrySet = map.entrySet();

        // entrySet을 순회하면서 value를 읽어온다 
        Iterator<Map.Entry<String, Integer>> entryIterator = entrySet.iterator();
        while(entryIterator.hasNext()) {
            Map.Entry<String, Integer> entry = entryIterator.next();
            String key = entry.getKey(); // Map.Entry 인터페이스의 메서드
            Integer value = entry.getValue(); // Map.Entry 인터페이스의 메서드
            System.out.println(key + " : " + value);
        }

        // 객체 전체 삭제
        map.clear();
    }
}
```

- Map은 키와 값을 쌍으로 저장하기 때문에 `iterator()`를 직접 호출할 수 없다
- 그 대신 **`keySet()` 이나 `entrySet()` 메서드를 이용해 Set 형태로 반환된 컬렉션에 `iterator()`를 호출하여 반복자를 만든 후, 반복자를 통해 순회할 수 있**

>**Reference**
>>[https://www.geeksforgeeks.org/how-to-learn-java-collections-a-complete-guide/](https://www.geeksforgeeks.org/how-to-learn-java-collections-a-complete-guide/)  
>>[Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html)  
>>[ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)  