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
let singleNumber = function (nums) {
  let result = 0;
  for (let i = 0; i < nums.length; i++) {
    result = result ^ nums[i];
  }
  return result;
};
```

### 설명

주어지는 array를 기준으로 for문을 순회했고 중복되는 숫자를 XOR 연산자를 활용해서 result에 값에 담아줬다.

## Reese

### 풀이

```js
var singleNumber = function (nums) {
  const onlyUnique = new Set();
  nums.forEach((num) =>
    !onlyUnique.has(num) ? onlyUnique.add(num) : onlyUnique.delete(num)
  );
  return [...onlyUnique][0];
};
```

### 설명

`nums`는 하나의 요소만 딱 한번 등장하고 이를 제외한 모든 요소가 2번씩 등장하는 배열이다. 문제는 한 번만 등장하는 요소가 무엇인지 찾는거다.<br />
임의의 Set `onlyUnique`를 만들어 놓고 `nums`를 순회하면서 해당 인자가 `onlyUnique`에 존재하지 않을 경우 `onlyUnique`에 추가하고, 존재할 경우 `onlyUnique`에서 삭제하는 식으로 접근했다.<br />
두번 등장한 요소는 반드시 `onlyUnique`에서 삭제되기 때문에 순회가 끝난 시점에 `onlyUnique`에 남아 있는 요소가 바로 한 번만 등장하는 요소이다.<br />

<br />

> Set을 array로 변환하는 방법 (spread syntax)

```
[...Set] = arr
```

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
