
__배열(Array)__ 은 데이터를 일정한 순서로 나열한 자료구조이다.


동일한 데이터 타입의 값들을 __연속된 메모리 공간__ 에 저장하여
효율적인 접근과 관리가 가능하다.

---

| Index | 0   | 1   | 2   | 3   | 4   |
| ----- | --- | --- | --- | --- | --- |
| Value | 1   | 2   | 3   | 4   | 5   |

_1~5까지의 숫자를 저장한 배열의 예시_

---
#### 특징

1. __고정 크기__: 배열의 크기는 처음 생성할 때 정의된다.
2. __연속된 메모리__: 메모리의 연속된 공간에 할당되므로, 목차 (Index) 를 통해 빠르게 접근할 수 있다.
3. __동일한 데이터 타입__: 배열의 모든 요소는 동일한 데이터 타입을 가진다.
4. __목차(Index)__: 0 부터 시작하는 목차(Index) 를 통해 접근할 수 있다.

---
#### 예시

```typescript
let numbers: number[] = [1, 2, 3, 4, 5];

let strings: string[] = ["apple", "banana", "cherry"];

let genericNum: Array<number> = [1, 2, 3, 4, 5];

let genericStr: Array<string> = ["apple", "banana", "cherry"];
```

`number[]` 와 같이 배열을 선언하거나, 제네릭(Generic) 으로 `Array<number>` 와 같이 배열을 선언할 수 있다.

```TypeScript
numbers[1];
numbers[2];
```

변수의 옆에 위와 같은 형태로 목차(Index) 를 적어 변수에 있는 해당 목차의 값에 접근할 수 있다.

___
#### 주요 연산

1. __검색__: 특정 목차(Index) 에 있는 요소를 빠르게 검색한다. <br />
$$O(1)$$ 
2. __삽입 및 삭제__: 다른 요소를 이동하며 특정 위치에 요소를 삽입하거나 삭제한다. <br />
$$O(n)$$
3. __정렬__: 알고리즘마다 각각의 시간 복잡도에 차이가 있다. <br />
$$?$$
---
#### 사용 예시

1. __리스트 관리__: 리스트(List), 스택(Stack), 큐(Queue)...
2. __데이터 구조 구현__: 해시 테이블(Hash Table), 트라이(Trie)...
3. __수학적 계산__: 행렬 연산...

---

#### 주요 연산 구현

##### 1. 검색

```TypeScript
function findElement(arr: number[], value: number): number {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === value) return i;
  }

  return -1;
}
```

##### 2. 삽입

```TypeScript
function insertEnd(arr: number[], key: number, value: number): number[] {
  for (let i = 0; i >= key; i--) {
    arr[i + 1] = arr[i];
  }
  arr[key] = value;
  
  return arr;
}
```

##### 3. 제거

```TypeScript
function deleteElement(arr: number[], value: number): number[] {
  const index = findElement(arr, value);
  if (index === -1) throw Error("Element not found");
  
  for (let i = index; i < arr.length - 1; i++) {
    arr[i] = arr[i + 1];
  }
  arr.pop();

  return arr;
}
```

---
