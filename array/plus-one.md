# [Plus One](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/559/)

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
var plusOne = function(digits) {
    // return new String(parseInt(digits.join('')) + 1).split('').map(Number);

    let i = digits.length - 1;
    while (digits[i] === 9) digits[i--] = 0;
    if (i < 0) digits.unshift(1);
    else digits[i] += 1;
    return digits;
};
```

### 설명

이 문제는 처음에 주석의 코드로 시도했는데 잘 되지 않았다. 배열을 수로 변경한 뒤 +1 을 하고 다시 배열로 바꿔주는 식으로 해결하고자 했는데, 굉장히 큰 수가 있어 이 방식은 불가능하게 막아놨다.

제한 시간안에 문제를 다 풀지 못해 다른 답안을 참고했다.

1. 마지막 수가 9라면, 해당 수를 0으로 만들고 `i`를 -1 한다. 9에서 1을 더하면 10이 되는 과정이다. 이 부분에서 `--`에 대한 내 이해가 부족하다고 느꼈다. `--`와 `-= 1` 의 정확한 차이를 더 공부해봐야겠다. `-= 1` 에선 제대로 동작하지 않았다.
2. `i` 가 0 이하라면, 즉 자릿수가 첫번째라면 맨 앞에 1을 붙인다. 자리올림을 나타낸 식이다.
3. 아니라면 자리올림이 더 이상 일어나지 않는 마지막 수에 1을 더한다.

---

## 참고자료
