
__행렬(Matrix)__ 은 2차원 배열의 형태를 가진 자료구조이다.

행렬은 행(row)과 열(column)로 구성된 사각형의 배열로,
다양한 데이터와 연산을 효율적으로 관리할 수 있다.

---

|     | 0   | 1   | 2   |
| --- | --- | --- | --- |
| 0   | 1   | 2   | 3   |
| 1   | 4   | 5   | 6   |
| 2   | 7   | 8   | 9   |

_3 x 3 크기의 행렬에 1~9까지의 숫자를 저장한 예시_

---
#### 특징

1. __차원__: 행렬은 2차원 배열로, 행과 열의 조합으로 이루어져 있다.
2. __동일한 데이터 타입__: 행렬의 모든 요소는 동일한 데이터 타입을 가져야 한다.
3. __목차 접근__: 행렬 요소는 행과 열의 목차(Index) 를 통해 접근할 수 있다.

---
#### 예시

```TypeScript
const matrix: number[][] = [
	[1, 2, 3],
	[4, 5, 6]
];
```

`number[][]` 과 같이 행렬을 선언할 수 있다.

```TypeScript
matrix[1][1];
```

변수의 옆에 행과 열을 위와 같은 형태로 적어 변수의 특정 행과 열에 있는 값에 접근할 수 있다.

---
#### 주요 연산

1. __덧셈과 뺄셈__: 두 행렬의 요소를 각각 더하거나 뺀다. ( _m행 n열 행렬 기준_ ) <br />
$$O(m * n)$$

2. __곱셈__: 행렬을 서로 곱한다. ( _m행 n열 행렬 & n행 p열 행렬 기준_ ) <br />
$$O(m * n * p)$$

4. __전치 행렬__: 행렬의 행과 열을 바꾼다. ( _m행 n열 행렬 기준_ ) <br />
$$O(m * n)$$

---
#### 사용 예시

- __컴퓨터 그래픽스__: 변환 행렬을 사용하여 3D 객체의 이동, 회전 등을 수행한다.
- __데이터 분석__: 데이터를 행렬 형태로 나타내어 연산을 효율적으로 수행한다.
- __물리 시뮬레이션__: 연립 방정식의 해를 구하는데 사용된다.

---
#### 주요 연산 구현

##### 1. 덧셈과 뺄셈

```TypeScript
function addMatrices(A: number[][], B: number[][]): number[][] {
	const result = A.map((row, i) => row.map((v, j) => v + B[i][j]));
	return result;
}

function subtractMatrices(A: number[][], B: number[][]): number[][] {
	const result = A.map((row, i) => row.map((v, j) => v - B[i][j]));
	return result;
}
```

##### 2. 곱셈

```TypeScript
function multiplyMatrices(A: number[][], B: number[][]): number[][] {
	const m = A.length;
	const n = A[0].length;
	const p = B[0].length;
	const result = Array.from({ length: m }, () => Array(p).fill(0));

	for (let i = 0; i < m; i++) {
		for (let j = 0; j < p; j++) {
			for (let k = 0; k < n; k++) {
				result[i][j] += A[i][k] * B[k][j];
			}
		}
	}
	return result;
}
```

##### 3. 전치 행렬

```TypeScript
function transposeMatrix(A: number[][]): number[][] {
	const m = A.length;
	const n = A[0].length;
	const result = Array.from({ length: n }, () => Array(m).fill(0));

	for (let i = 0; i < m; i++) {
		for (let j = 0; j < n; j++) {
			result[j][i] = A[i][j];
		}
	}
	return result;
}
```


---
