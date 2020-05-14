# [Contains Duplicate](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/578/)

> 2020.05.02.(토)

## Hoo

### 풀이

```js
const containsDuplicate = (nums) => {
	const set = new Set(nums);
	return set.size !== nums.length;
};
```

### 설명

> 배열 안에 중복되는 값이 있으면 true, 없으면 false를 반환하는 문제

중복을 허용하지 않는 `Set`에 배열을 넣으면 간단히 해결된다.<br />
만약 중복이 있다면 set의 크기와 원본 배열의 크기가 다를 것이다.<br />
이를 이용해 `boolean` 값을 반환하도록 하면 된다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
var containsDuplicate = function (nums) {
	const mySet = new Set(nums);
	return mySet.size !== nums.length;
};
```

### 설명

Hoo, Ed와 동일한 방법으로 풀었다😅<br />
중복을 허용하지 않는 `Set`의 성질을 활용해서 리스트의 길이를 비교!

<br />

### 다른 풀이

```js
var containsDuplicate = function (nums) {
	const table = {};
	for (let i = 0, len = num.length; i < len; i++) {
		table[nums[i]] = table[nums[i]] + 1 || 1;
		if (table[nums[i]]) return true;
	}
	return false;
};
```

`nums` 배열을 순회하면서 해당 값이 등장하는 횟수를 객체 `table`에 업데이트 해주는 방법이다. <br />
특정 값이 2번 이상 등장할 경우 순회를 종료함과 동시에 true를 리턴한다.

## Ed

### 풀이

```js
var containsDuplicate = function (nums) {
	return nums.length !== new Set(nums).size;
};
```

### 설명

중복이 포함돼있는지를 판별하는 문제이다. 다른 알고리즘을 사용하진 않고, 자바스크립트 `Set`을 사용했다. 같은 요소를 가진 새로운 `Set`을 만든다. `Set`은 중복을 허용하지 않기 때문에 `Set`과 원본 배열 `nums`의 길이가 같은지 다른지 체크하면 된다.

---

## 참고자료
