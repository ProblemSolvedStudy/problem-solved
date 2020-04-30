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
