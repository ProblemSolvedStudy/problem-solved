# [Sock Merchant](https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup)

> 2020.06.07.(일요일)

## Hoo

### 풀이

```js
function sockMerchant(n, ar) {
  let map = new Map();

  for (let i = 0; i < n; i++) {
    // 분기처리 - if 문 사용
    if (!map.has(ar[i])) {
      map.set(ar[i], 1);
    } else {
      map.set(ar[i], map.get(ar[i]) + 1);
    }

    // 분기처리 - 삼항 연산자 사용
    map.has(ar[i]) ? map.set(ar[i], map.get(ar[i]) + 1) : map.set(ar[i], 1);
  }

  const reducer = (result, currentValue) => result + Math.floor(currentValue / 2);
  return [...map.values()].reduce(reducer, 0);
}
```

### 설명

> 짝이 맞는 양말의 개수를 구하는 문제

- 처음에 문제를 반대로 이해해서 짝이 안 되는 나머지 숫자를 구하는 것으로 이해해 헤맸다.

1. `map`으로 숫자마다 양말의 개수를 저장해 2로 나눠 몫만 더하면 답이 나온다.
2. for문을 돌면서 map에 개수를 차곡차곡 더한다.
3. 그리고 `reduce`를 사용해 양말이 짝지어지는 개수를 구해서 계속 더한 값을 구한다.

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
