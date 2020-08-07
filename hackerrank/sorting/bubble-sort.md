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
function countSwaps(a) {
  let count = 0;

  for (let i = 0; i < a.length; i++) {  
    for (let j = i + 1; j < a.length; j++) {
        if (a[i] > a[j]) {
            let temp  = a[i];
            a[i] = a[j];
            a[j] = temp;
            count++;
        }
    }  
  }
  
  let result = `Array is sorted in ${count} swaps.\nFirst Element: ${a[0]}\nLast Element: ${a[a.length - 1]}`;

  console.log(result);
}
```

### 설명

> 버블 소트를 한 결과를 문장으로 출력하는 문제.

- **버블 소트**는 정렬 알고리즘 중에 가장 쉬우면서 시간복잡도가 큰 알고리즘이다.
- 이중 반복문 안에서 값의 크기 비교를 통해 `swap`하면서 개수를 센다.
- 반복문 결과를 `template literal`로 저장해 콘솔로 출력하면 된다.

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
function countSwaps(a) {
    let numSwaps = 0;
    for (let i = 0; i < a.length; i++) {
        for (let j = 0; j < a.length - 1; j++) {
            if (a[j] > a[j + 1]) {
                const temp = a[j]
                a[j] = a[j + 1];
                a[j + 1] = temp;
                numSwaps++;
            }
        }
    }
    console.log(`Array is sorted in ${numSwaps} swaps.
First Element: ${a[0]}
Last Element: ${a[a.length - 1]}`);
}

```

### 설명

- 버블 정렬 코드가 문제 내에 주어져 있어서 쉽게 풀 수 있었다.

---

## 참고자료
