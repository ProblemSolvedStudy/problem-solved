# [Single Number](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/549/)

> 2020.05.02.(토)

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
```

### 설명

## Ed

### 풀이

```js
var singleNumber = function(nums) {
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
