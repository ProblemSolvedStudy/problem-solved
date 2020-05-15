# [Two Sum](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/546/)

> 2020.05.09(토)

## Hoo

### 풀이

```js
const twoSum = (nums, target) => {
	let map = new Map();
	for (let i = 0; i < nums.length; i++) {
		const complement = target - nums[i];
		if (map.has(complement)) {
			return [map.get(complement), i];
		}
		map.set(nums[i], i);
	}
};
```

### 설명

> 배열의 두 수를 더해 타겟의 수가 나오도록 하는 위치를 배열로 반환하는 문제

처음에는 이중 반복문을 사용해 두 수를 더한 값이 `타겟` 값이 나오면 해당 값의 인덱스를 배열로 묶어 반환하도록 풀었다. 더 간단한 풀이가 있을 것 같아서 솔루션을 참고해 `Map`을 사용했다.

1. 먼저 빈 `Map`을 만든다.
2. 반복문을 돌면서 `현재 배열의 값`을 `타겟 값`에 뺀 값이 Map에 있는지 확인한다.
3. 값이 Map에 있으면 해당 수의 index 값(value)과 현재 index를 배열로 반환한다.
4. 값이 Map에 없으면 현재 값과 인덱스를 Map에 추가한다.

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
