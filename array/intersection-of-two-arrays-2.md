# [Intersection of Two Arrays II](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/674/)

> 2020.05.02.(토)

## Hoo

### 풀이

```js
const intersect = (nums1, nums2) => {
	let result = [];

	for (let i = nums1.length - 1; i >= 0; i--) {
		for (let j = 0; j < nums2.length; j++) {
			if (nums1[i] === nums2[j]) {
				result.push(nums1[i]);
				nums1.splice(i, 1);
				nums2.splice(j, 1);
			}
		}
	}

	return result;
};
```

### 설명

> 두 배열에서 중복되게 들어있는 값만 배열로 반환하는 문제

마땅한 더 좋은 방법이 생각이 나지 않아서 이중 반복문을 사용했다.  
이중 반복문을 돌아 값을 하나씩 비교하면서 같으면 배열에 `push`하고 두 배열에서는 삭제하도록 했다.  
삭제하지 않으면 `[4,9,4,9]`와 같은 중복되는 값이 걸러지지 않고 추가로 배열에 들어가 버린다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제 이해

두 개의 배열이 인자로 주어졌을때, 겹치는 요소를 새로운 배열로 반환하는 문제이다.<br />
여러 번 겹치면 겹치는대로 모두 반환해줘야 하며, 요소의 순서는 상관 없다. <- 이부분이 문제에는 나와있는데 예제에는 명시되지 않아서 헷갈렸다.<br />
아래는 내가 좀 더 명확하게 다듬은 예제들이다.

> e.g.

```
Input: nums1 = [1, 2, 2, 1, 2, 2], nums2 = [2, 2]
Output: [2, 2, 2, 2]
```

→ 여러 번 겹치면 겹치는대로 다 반환해줘야 한다.

```
Input: nums1 = [4, 9, 5], nums2 = [9, 4, 9, 8, 4]
Output: [4, 9] or [9, 4]
```

→ 일부분이 겹치면 겹치는 부분만 반환한다.<br />
→ 반환되는 배열 내에서 요소의 순서는 상관없다.

### 풀이

처음엔 `Set`, `include`, `filter` 등을 사용해서 겹치는 요소를 찾으려고 했는데, 위에 명시된 조건을 충족시키지 못해서 번번이 실패했다. 30분 정도 고민하다가 답안을 보고 공부하기로 결정.

```js
var intersect = function (nums1, nums2) {
	const map = new Map();
	nums1.forEach((num) => (map.has(num) ? map.set(num, map.get(num) + 1) : map.set(num, 1)));

	const result = [];
	nums2.forEach((num) => {
		if (map.get(num) > 0) {
			result.push(num);
			map.set(num, map.get(num) - 1);
		}
	});

	return result;
};
```

### 설명

임의의 `Map`을 하나 만들고 `nums1`에 들어있는 모든 요소의 갯수를 map에 표기한다. 그리고 `nums2`를 순회하면서 `nums1`에 있던 요소의 갯수를 하나씩 차감해 나간다.<br />이때의 시간복잡도는 **O(n+m)**이 된다.

이 풀이를 보고 깨달은건, 문제의 조건을 명확하게 이해하지 못했다는 점이었다. 나는 중복된 요소가 연속으로 붙어있어야 하는 줄 알았는데, 사실은 위치에 관계없이 중복해서 등장하기만 하면 반환값에 포함시키면 되는 것이었다! 이런건 예제에서 좀 더 명확하게 보여줬어야 하지 않았나 싶다.<br /> 예를 들면 이런 식이다.

```
Input: nums1 = [4, 9, 5], nums2 = [4, 5]
Output: [4, 5] or [5, 4]
```

→ 두 배열에서 겹치는 요소는 4와 5이다. 이 둘 사이에 9가 있지만 어쨌든 두 배열에서 모두 등장하는 값이기 때문에 반환하는 배열에 포함시키면 된다.

## Ed

### 풀이

```js
```

### 설명

이 문제는 제대로 풀지 못했다. 추후 다시 풀어보려고 한다.

---

## 참고자료
