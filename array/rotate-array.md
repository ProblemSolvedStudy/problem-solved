# [Rotate Array](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/646/)

> 2020.04.25.(토)

## Hoo

### 풀이

```js
```

### 설명

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
var rotate = function (nums, k) {
	for (let len = nums.length, i = len - 1; i >= len - k; i--) {
		nums.unshift(nums.pop());
	}
};
```

### 설명

배열의 맨 끝에서부터 요소를 하나씩 제거(`pop`)한 후 `pop`이 반환한 요소를 배열의 맨 앞에 append(`unshift`)했다.

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
