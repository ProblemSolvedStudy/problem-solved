# [문제 제목](링크)

> 연.월.일.(요일)

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
function hourglassSum(arr) {
  const sums = [];
  for (let i = 1, lastArrIdx = arr.length - 2; i <= lastArrIdx; i++) {
    for (let j = 1, lastElIdx = arr[0].length - 2; j <= lastElIdx; j++) {
      let sum = 0;
      // top
      sum += arr[i - 1][j - 1] + arr[i - 1][j] + arr[i - 1][j + 1];
      // middle
      sum += arr[i][j];
      // bottom
      sum += arr[i + 1][j - 1] + arr[i + 1][j] + arr[i + 1][j + 1];
      sums.push(sum);
    }
  }
  return Math.max(...sums);
}
```

### 설명

풀이 과정은 크게 3부분으로 나눌 수 있다.

1. 모래시계를 아래와 같이 크게 3부분으로 나누었다.

```
2 4 4  -> top
  2    -> middle
1 2 4  -> bottom
```

2. middle 부분을 기준으로 배열 arr를 순회하면서 합을 구하고 임의의 배열 `sums`에 보관한다.<br />이때 middle에 위치하는 요소가 가질 수 있는 인덱스 범위는 1이상, (배열의 길이 - 2)이하이다.

   > 문제에는 6x6 사이즈의 배열만 인자로 주어진다고 했지만, 확장성을 고려해서 배열 arr의 길이, 그리고 arr의 요소로 들어있는 배열의 길이를 고정된 값이 아닌 length를 통해 계산하도록 했다.

3. 순회가 종료되면 (각각의 모래시계의 합을 다 구하면) `sums` 배열 안에서 최대값을 찾아 반환한다.

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
