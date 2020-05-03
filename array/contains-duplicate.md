# [Contains Duplicate](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/578/)

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
var containsDuplicate = function(nums) {
    return nums.length !== new Set(nums).size;
};
```

### 설명

중복이 포함돼있는지를 판별하는 문제이다. 다른 알고리즘을 사용하진 않고, 자바스크립트 `Set`을 사용했다. 같은 요소를 가진 새로운 `Set`을 만든다. `Set`은 중복을 허용하지 않기 때문에 `Set`과 원본 배열 `nums`의 길이가 같은지 다른지 체크하면 된다.

---

## 참고자료
