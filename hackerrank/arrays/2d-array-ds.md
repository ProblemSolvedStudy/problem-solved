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

> 2차원 6 * 6 배열에서 나올 수 있는 모래시계 중에서 가장 큰 합을 구하는 문제

1. 6 * 6 배열에서 모래시계는 `4 * 4 = 16`개가 나온다.
2. 모든 모래시계의 합을 구하기 위해 이중 반복문을 이중 배열보다 2보다 작은 길이만큼 돌 수 있게 한다.
3. 이중 반복문 안에서 모래시계의 합을 구해 result보다 크면 result에 저장시키고 반복문이 끝나면 반환한다.

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
