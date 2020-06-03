# [Valid Sudoku](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/769/)

> 2020.05.09.(토)

## Hoo

### 풀이

```js
const isValidSudoku = (board) => {
	return (
		board.every((column) => isValidColumn(column)) &&
		rotateMatrix(board).every((column) => isValidColumn(column)) &&
		extractMatrix(board).every((column) => isValidColumn(column))
	);
};

const isValidColumn = (column) => {
	const onlyNums = column.filter((num) => num !== ".");
	const set = new Set(onlyNums);
	return set.size === onlyNums.length;
};

const rotateMatrix = (matrix) => matrix[0].map((column, index) => matrix.map((row) => row[index]));

const extractMatrix = (matrix) => {
	const squares = [[], [], [], [], [], [], [], [], []];

	matrix.forEach((row, rowIndex) => {
		row.forEach((cell, columnIndex) => {
			const squareIndex = Math.floor(rowIndex / 3) * 3 + Math.floor(columnIndex / 3);

			squares[squareIndex].push(cell);
		});
	});

	return squares;
};
```

### 설명

> 수도쿠가 유효한지 확인하는 문제

수도쿠가 유효한지 확인하려면 `행, 열, 3*3 묶음`에 모두 중복되는 숫자가 없어야 한다.  
나는 이를 처리하기 위해 `.`을 제외한 숫자들을 `Set`에 넣어 개수를 비교하는 `isValidColumn` 함수를 만들었다.  
`isValidColumn` 는 9개의 한 묶음을 비교하기 위한 것이기 때문에 배열 9개 묶음이 있어야 한다.  
행은 원래 그대로 비교하면 되기 때문에 그대로 비교하고, 열과 3\*3은 배열 묶음으로 만들기 위해 `rotateMatrix`, `extractMatrix` 함수를 만들었다.
마지막으로 모든 결과가 true이면 true이도록 `every` 메소드를 사용했다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
```

### 설명

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
