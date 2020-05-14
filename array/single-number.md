# [Single Number](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/549/)

> 2020.05.02.(토)

## Hoo

### 풀이

```js
const singleNumber = (nums) => {
	return nums.reduce((accu, curr) => accu ^ curr);
};
```

### 설명

> 배열에서 중복되지 않는 하나의 수를 찾는 문제

문제에서 중복되는 숫자가 있으면 2번 들어있으니 XOR로 배열의 모든 숫자를 계산한다.  
XOR은 숫자를 2진수로 변환해 각 숫자가 같으면 0, 다르면 1로 나타내어지는 연산자이다.  
즉, 같은 숫자를 비트 연산자로 계산하면 0이 된다는 것이다.  
`[4, 1, 2, 1, 2]`와 같이 숫자가 정렬되어 있지 않아도 `1+5+2-1-2`와 `1-1+2-2+5`의 값이 같은 것처럼 결과는 언제나 4가 나올 것이다.  
결국 마지막에는 중복되지 않은 값 하나만 나와서 답을 구하게 된다.

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
var singleNumber = function (nums) {
	const unique = new Set();
	for (let i = 0; i < nums.length; i++) {
		if (unique.has(nums[i])) unique.delete(nums[i]);
		else unique.add(nums[i]);
	}
	return [...unique];
};
```

### 설명

배열에서 반복되지 않는 1가지의 수를 찾으면 된다. 별도의 `Set`을 만든 뒤, 없으면 추가하고, 있으면 삭제하도록 했다. 1가지의 수를 제외한 다른 수는 무조건 2번씩 반복되므로, 마지막엔 유일한 1가지의 수만 남게 된다.

---

## 참고자료
