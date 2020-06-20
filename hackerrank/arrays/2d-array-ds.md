# [2D Array - DS](https://www.hackerrank.com/challenges/2d-array/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays)

> 2020.06.13.(토요일)

## Hoo

### 풀이

```js
function hourglassSum(arr) {
  let result = -100;

  for (let i = 0; i < arr.length - 2; i++) {
    for (let j = 0; j < arr.length - 2; j++) {
      let sum = arr[i + 1][j + 1];
      for (let k = 0; k < 3; k++) {
        sum += arr[i][j + k];
        sum += arr[i + 2][j + k];
      }
      if (sum > result) result = sum;
    }
  }

  return result;
}
```

### 설명

> 2차원 6 \* 6 배열에서 나올 수 있는 모래시계 중에서 가장 큰 합을 구하는 문제

1. 6 _ 6 배열에서 모래시계는 `4 _ 4 = 16`개가 나온다.
2. 모든 모래시계의 합을 구하기 위해 이중 반복문을 이중 배열보다 2보다 작은 길이만큼 돌 수 있게 한다.
3. 이중 반복문 안에서 모래시계의 합을 구해 result보다 크면 result에 저장시키고 반복문이 끝나면 반환한다.

## Hoi

### 풀이

```js
function hourglassSum(arr) {
  const hourglassSumList = [];
  const count = arr.length - 2;

  for (let i = 1; i <= count; i++) {
    for (let j = 1; j <= count; j++) {
      let sum = 0;
      sum += arr[i - 1][j - 1] + arr[i - 1][j] + arr[i - 1][j + 1];
      sum += arr[i][j];
      sum += arr[i + 1][j - 1] + arr[i + 1][j] + arr[i + 1][j + 1];

      hourglassSumList.push(sum);
    }
  }

  return Math.max(...hourglassSumList);
}
```

### 설명

6 \* 6의 이챠원 배열이 주어지고 계산가능한 모든 모례시계들의 합을 구해서 가장 큰 값을 찾아내는 문제다.
일단 이 문제는 풀지 못했지만 Hoo와 Reese가 조언을 해준 덕분에 풀 수 있었다.
첫번째 오류는 이차원 배열의 모래시계 형태에 0이 아닌 정수나 음수의 형태로 들어가 있어야만 모래시계라고 판단하고 값을 구하는 줄 알았다.
하지만 문제의 조건은 만들어 질 수 있는 모든 모래시계의 형태를 계산하면 되는 문제였다 ....

1. 편의를 위해서 1번째 index부터 for문을 순회하도록 했다. 0번째 index는 이차원 배열에서 모래시계의 형태를 만들 수 없기 때문이다.
2. 이중 for문을 이용해서 모든 모래시계의 Sums을 구하도록 했고 위와 같이 마지막 index 역시 모래시계의 형태를 만들 수 없으니 arr.length - 2 만큼만 반복문을 순회하도록 했다.
3. 결과값들을 array에 계속해서 저장하고 Math.max를 활용해서 가장 큰 값을 return 하도록 했다.

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
