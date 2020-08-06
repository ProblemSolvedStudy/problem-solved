# [Bubble Sort](https://www.hackerrank.com/challenges/ctci-bubble-sort/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=sorting)

> 2020.08.06 (목)

## Sally

### 풀이

```js
```

### 설명

## Zello

### 풀이

```js
```

### 설명

## Huey

### 풀이

```js
```

### 설명

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
function swap(arr, i, j) {
  const tmp = arr[i];
  arr[i] = arr[j];
  arr[j] = tmp;
}

function countSwaps(a) {
  const len = a.length;

  let swaps = 0;
  for (let i = 0; i < len; i++) {
    for (let j = 0; j <= i; j++) {
      if (a[j] > a[i]) {
        swap(a, i, j);
        swaps++;
      }
    }
  }

  console.log(
    `Array is sorted in ${swaps} swaps.\nFirst Element: ${a[0]}\nLast Element: ${a[len - 1]}`
  );
}

// 시간복잡도 : O(n^2)
// 공간복잡도 : O(1)
```

### 설명

일반적인 방법으로 버블정렬을 구현했다.

- swap을 위한 별도의 함수를 생성하여 사용했다.
- 인덱스를 제어할 때 내부 for문에 `j <= i`라는 조건을 줌으로써 `i`가 바뀔 때마다 인덱스 0부터 다시 비교할 수 있도록 했다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
