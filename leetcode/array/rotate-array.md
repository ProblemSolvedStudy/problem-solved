# [Rotate Array](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/646/)

> 2020.04.25.(토)

## Hoo

### 풀이

```js
const rotate = (nums, k) => {
  if (nums.length < k) k %= nums.length;
  const spliceArray = nums.splice(0, nums.length - k);
  spliceArray.forEach((el) => nums.push(el));
};
```

### 설명

> 1차원 배열이 전해진 숫자만큼 오른쪽으로 회전하도록 만드는 문제.

이 문제의 풀이에는 크게 두 가지가 있는 것 같다.

1. 오른쪽에 주어진 개수만큼 분리해서 왼쪽에 붙여 회전된 결과를 만들기
2. 하나씩 오른쪽에서 떼고 왼쪽에 붙여서 회전하기

이 중 나는 1번으로 풀었다. (2번은 생각을 못 했다)

일단, 오른쪽으로 도는 횟수인 `k`는 nums의 총 길이를 넘지 않도록 제어해 주어야 한다.  
nums의 길이를 넘어가면 undefined로 계산하게 될 것이다.  
(2번 방법으로 풀더라도 반복 계산을 줄이기 위해 길이에 관한 계산을 먼저 해 주는 게 좋을 것이다.)  
나머지 값을 계산해 k에 다시 저장하고, 0번부터 k를 뺀 개수만큼 `splice`를 해 따로 배열에 저장한다.  
배열에 저장한 값은 반복문으로 남은 원래 배열에 추가한다.

## Hoi

### 풀이

```js
const rotate = function (nums, k) {
  debugger;
  for (i = nums.length - 1; i >= nums.length - k; i--) {
    nums.unshift(nums.pop());
  }
  return nums;
};

rotate([1, 2, 3, 4, 5, 6, 7], 3);
```

### 설명

이 문제를 해결결한 기준은 k 값을 기준으로 해당 값에 도달할 때 까지 오른쪽으로 회전한다.
라고 생각하고 계산했다.
k는 몇 번 rotate를 회전 할 지의 기준이 된다고 생각했으며 마지막 값을 pop으로 추출하고 바로 unshift로 넣어줌으로써 배열의 길이에 변화가 없도록 신경써서 문제를 해결했다.

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
var rotate = function(nums, k) {
    if (nums.length < k) k = k % nums.length;
    let num = nums.splice(-k, k);
    for (let i = num.length - 1; i >= 0; i--) {
        nums.unshift(num[i]);
    }
    return nums;
};
```

### 설명

문제에서는 `k`의 step만큼 순서대로 회전이 이루어진 예시를 보여줬는데, 나의 경우 한번에 회전하는 식으로 문제를 해결하려고 했다.

`k`의 수만큼 우선 `nums` 에서 자르고, `num`이라는 배열로 별도로 분리한다.
`num` 배열의 수만큼 `nums` 에서 `num` 의 맨 끝에서부터 `unshift` 해서 회전된 형태로 만든다.

앞의 조건문은 `k` 값이 `nums.length` 보다 커지는 케이스를 방지하기 위해 넣었다.

---

## 참고자료
