# [Move Zeroes](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/567/)

> 2020.05.09.(토요일)

## Hoo

### 풀이

```js
const moveZeroes = (nums) => {
	for (let i = nums.length - 1; i >= 0; i--) {
		if (nums[i] === 0) {
			nums.push(nums.splice(i, 1));
		}
	}

	return nums;
};
```

### 설명

> 배열에서 0인 값을 오른쪽으로 이동시키는 문제

반복문을 뒤에서부터 돌아 0인 숫자는 `splice`하면서 `push`했다.  
여기서 주의할 점은 **반복문을 뒤에서 돌았다**는 것이다.  
반복문을 앞에서 돌면서 splice를 쓰게 되면 0이 연속해서 나온다면 0이 다 이동되지 않는 문제가 있다.  
그래서 splice를 중복된 배열에서 사용할 때는 역순 반복을 해야 한다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
var moveZeroes = function (nums) {
	let numOfZeros = 0;
	for (let i = nums.length - 1; i >= 0; i--) {
		if (nums[i] === 0) {
			nums.splice(i, 1);
			numOfZeros++;
		}
	}
	for (let j = numOfZeros; j > 0; j--) {
		nums.push(0);
	}
};
```

### 설명

1차적으로 `nums`를 순회하면서 0이 등장할 때마다 splice 하여 0을 제거하고 `numOfZeros` 값을 1씩 더해서 0이 등장하는 횟수를 업데이트 해나갔다.<br />순회가 끝나면 `numOfZeros`의 값 만큼 0을 추가해준다.

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
