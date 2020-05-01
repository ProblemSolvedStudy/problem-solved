# [Remove Duplicates from Sorted Array](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/727/)

> 2020.04.25.(토)

## Hoo

### 풀이

```js
const removeDuplicates = (nums) => {
  for (let i = nums.length - 2; i >= 0; i--) {
    if (nums[i] === nums[i + 1]) nums.splice(i, 1);
  }
  console.log(nums);
  return nums.length;
};
```

### 설명

고차함수는 사용할 수 없는 문제라고 생각하면 될 것 같다.  
처음에 Set과 filter를 사용해 보았지만 틀린 답이라고 나왔다.  
그래서 for문에 splice를 사용했다.  
splice는 값을 삭제만 하는 기능도 있기 때문이다.  
근데 인덱스를 0번부터 1씩 커가는 식으로 돌리면 3개 이상 중복인 값은 제대로 지워지지 않는다.  
사실 이전에 다른 문제를 풀면서도 겪었던 문제인데, 간단하게 뒤에서부터 돌려주면 된다.  
나처럼 하지 않고 새로운 length 변수를 만들어 거기에 length를 세어줘도 된다.  

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

> 1st

```js
var removeDuplicates = function (nums) {
	const mySet = new Set(nums);
	return mySet.size;
};
```

### 설명

리스트 내에서 하나의 값이 한 번만 등장하는 Set의 특징을 이용한 풀이이다.<br />
인자로 받은 `nums`배열을 Set으로 변환하여 중복된 값을 삭제한뒤 `size` 메소드를 사용하여 Set내에 존재하는 (유일한)값들의 갯수를 반환했다.

콘솔에서는 잘 동작하지만 문제가 요구하는 조건(`modifying the input array **in-place** with O(1) extra memory.`)을 충족하지 못해서 fail이 떴다.

<br />

> 2nd

```js
var removeDuplicates = function (nums) {
	const numbers = {};
	nums.forEach((num) => {
		if (!numbers[num]) {
			numbers[num] = true;
		}
	});
	return Object.keys(numbers).length;
};
```

### 설명

임의의 빈 객체 `numbers`를 생성하고 `nums`배열을 순회하면서 특정 값이 등장할때마다 `numbers`의 프로퍼티로 추가해준다. 중복된 값이 있는지 여부를 확인할때 객체의 프로퍼티를 참조하는 방식.

1번 풀이와 마찬가지로 in-place한 방법이 아니어서 fail이었다.

<br />

> 3rd

```js
var removeDuplicates = function (nums) {
	for (let i = nums.length - 1; i > 0; i--) {
		if (nums[i] === nums[i - 1]) {
			nums.splice(i - 1, 1);
		}
	}
	return nums.length;
};
```

### 설명

3번째 풀이에서는 배열을 순회하면서 바로 직전값과 비교하여 중복된 값인 경우 `splice` 메서드를 사용하여 원본배열을 직접 수정했다.

<br />

#### 다른 풀이

```js
var removeDuplicates = function (nums) {
	let unique = 0;
	for (let i = 1, len = nums.length; i < len; i++) {
		if (nums[unique] !== nums[i]) {
			unique++;
			nums[unique] = nums[i];
		}
	}
	return unique + 1;
};
```

`unique`, `i` 총 2개의 포인터를 사용한 풀이이다.

`unique`는 유일한 값이 위치할 인덱스를 나타내고, `i`는 배열을 순회할때 사용할 인덱스를 나타낸다.

두 포인터가 각각 배열의 첫번째 값과 두번째 값을 가리키고 있는 상태에서 시작하여 배열을 순회하면서 새로운 유일한 값이 등장할 때마다 `unique`를 1 증가시키고 해당 값을 배열상의 `unique`가 가리키는 인덱스에 재할당하는 식이다.<br />

인자로 받은 배열이 `[0,0,1,1,1,2,2,3,3,4]`일 경우, 순회가 끝났을 때 `nums`는 아래와 같이 될텐데,

```
[0,0,1,1,1,2,2,3,3,4] -> [0, 1, 2, 3, 4, 2, 2, 3, 3, 4]
```

예시에 나온대로 반환할 길이를 넘어서는 `[2, 2, 3, 3, 4]`는 신경쓰지 않아도 된다.

> - It doesn't matter what you leave beyond the returned length.
> - It doesn't matter what values are set beyond the returned length.

반환할 값은 유니크한 값들의 갯수이자 유니크한 값들이 담긴 배열의 '길이'이므로, `unique + 1`을 반환해주면 된다. `unique` 자체는 **인덱스**를 나타낸다!

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료

- [In-Place Algorithm](https://www.geeksforgeeks.org/in-place-algorithm/)

`in-place`의 사전적 의미 : '그 자리에서', '제 자리에서'

In-Place 알고리즘은 추가적인 메모리 공간을 사용하지 않고 원본 데이터를 직접적으로 수정하는 알고리즘을 말한다.<br />
하지만 변수를 담기위한 '작은' 추가 메모리를 사용하는 것은 가능!

### Which Sorting Algorithms are In-Place and which are not?

- In Place : Bubble sort, Selection Sort, Insertion Sort, Heapsort.
- Not In-Place : Merge Sort. Note that merge sort requires O(n) extra space.

### What about QuickSort? Why is it called In-Place?

QuickSort uses extra space for recursive function calls. It is called in-place according to broad definition as extra space required is not used to manipulate input, but only for recursive calls.
