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

1차

```js
var twoSum = function (nums, target) {
	for (let i = 0, len = nums.length; i < len; i++) {
		for (let j = i + 1; j < len; j++) {
			if (nums[i] + nums[j] === target) {
				return [i, j];
			}
		}
	}
};
```

### 설명

`nums` 배열을 순회하면서 하나의 요소와 그 다음에 위치한 요소들을 차례대로 더해보고 `target`값인지 아닌지를 판별했다.<br />이 풀이는 추가적인 메모리가 필요 없지만(공간복잡도 : **O(1)**) 시간복잡도가 **O(n^2)** 이라는 점에서 비효율적인 방법이다.

<br />

### 풀이

2차

```js
var twoSum = function (nums, target) {
	const table = {};

	for (let i = 0, len = nums.length; i < len; i++) {
		const currNumber = nums[i];
		const diff = target - currNumber;

		if (table[currNumber]) {
			return [table[currNumber], i];
		} else {
			table[diff] = i;
		}
	}
};
```

### 설명

`nums` 배열을 순회하면서 임의의 객체 `table`에 target과의 차이(diff)를 키값으로 하여 인덱스를 저장한다.<br />`table`에 diff에 해당하는 키값이 존재할 경우 즉시 index 묶음을 반환할 수 있다.

```
var nums = [1, 2, 3, 4, 5];
var target = 9;
```

3번째 인덱스에 위치하는 4까지 순회했을 때 `table`은 다음과 같다.

```
const table = {
  8: 0,
  7: 1,
  6: 2,
  5: 3
}
```

4번째 인덱스에 위치하는 5를 마주치면 `table[5]`를 찾아서 바로 **[3, 4]** 을 반환하게 된다.

이 풀이의 시간복잡도는 **O(n)**, 공간복잡도는 **O(n)** 이다. (공간복잡도는 `table`에 인덱스를 저장하는데서 발생)<br />
참고로 `table`과 같은 객체에 값을 저장하고 찾는데 소요되는 시간복잡도는 **O(1)**이다.

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
