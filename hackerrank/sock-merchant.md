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
function sockMerchant(n, ar) {
  const tableOfSocks = new Map();

  ar.forEach((sock) => {
    tableOfSocks.has(sock)
      ? tableOfSocks.set(sock, tableOfSocks.get(sock) + 1)
      : tableOfSocks.set(sock, 1);
  });

  return [...tableOfSocks.values()].reduce((pairs, numOfSocks) => {
    pairs += Math.floor(numOfSocks / 2);
    return pairs;
  }, 0);
}
```

### 설명

임의의 Map (`tableOfSocks`)를 생성하고 인자로 받은 양말 리스트(ar)를 순회하면서 색상별 양말 갯수를 key(색상)-value(갯수) pair로 하여 테이블에 업데이트 해나간다.

```
Map {
  1: 3,
  3: 4,
  5: 1
}
```

색상이 같은 양말이 몇 쌍 나오는지 구하는 문제이기 때문에 `tableOfSocks`의 value를 배열로 변환한 뒤 reduce 메소드를 사용하여 2로 나눈 몫을 누적하여 리턴해주었다.

---

- 시간복잡도: **O(n)** (forEach로 배열을 순회할 때 O(n) + reduce로 배열 순회할 때 O(n))
- 공간복잡도: **O(m)** (n >= m, 인자로 받은 ar을 제외하고 Map을 생성할때 O(m) + Map의 value들을 담은 배열을 생성할때 O(m))

---

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
