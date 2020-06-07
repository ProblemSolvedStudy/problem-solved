# [Counting Valleys](https://www.hackerrank.com/challenges/counting-valleys/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup)

> 2020.06.07.(일요일)

## Hoo

### 풀이

```js
function countingValleys(n, s) {
  const stringList = s.split("");
  let seaLevel = 0;
  let result = 0;

  stringList.forEach((value) => {
    if (value === "U") {
      seaLevel++;
      if (seaLevel === 0) result++;
    } else {
      seaLevel--;
    }
  });

  return result;
}
```

### 설명

> 골짜기에 내려갔다가 도로 원래 위치로 올라오는 횟수를 구하는 문제

#### 문제 조건

- 입력되는 문자열에서 `U`는 1씩 올라가는 것, `D`는 1씩 내려가는 것을 표현한다.
- 그림에 있는 평행선은 시작하는 지점, 즉 **0**을 의미한다.
- 시작 지점(0)에서 올라갔다가 내려와서 0이 되는 것은 count에 포함되지 않는다.

![IMG_7D6847127D74-1](https://user-images.githubusercontent.com/30427711/83962561-5a9f9980-a8d9-11ea-99e2-aab9ad0d4a4c.jpeg)

1. 문제 조건을 따라 처음에는 `U와 D`를 조건문으로 나눠 1씩 더하거나 빼 주었다.
2. count(풀이에서는 result)가 적용되기 위해서는 시작 지점에서 내려갔다가 올라와서 다시 0이 되어야 한다.
3. 그러므로 `U`이면서 시작 지점일 때 count를 1씩 늘려 주면 답이 나온다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
function upOrDown(value) {
  return value === "U" ? false : true;
}

function countingValleys(n, s) {
  let isValley = upOrDown(s[0]);
  let numOfVallies = 0;
  let currLevel = 0;

  const steps = s.split("");

  for (let i = 0; i <= n; i++) {
    if (i !== 0 && currLevel === 0) {
      if (isValley) numOfVallies++;
      isValley = upOrDown(steps[i]);
    }
    steps[i] === "U" ? currLevel++ : currLevel--;
  }

  return numOfVallies;
}
```

### 설명

현재 높이(`currLevel`)가 0일때마다 valley인지 아닌지의 여부를 판단하여(`isValley`) valley 갯수(`numOfVallies`)를 업데이트 해나가는 식으로 접근했다.

`currLevel`는 해수면을 기준으로 한 현재 높이를 나타내는 변수이다. 시작지점의 높이는 해수면과 동일하기 때문에 초기값은 0이 된다.

그리고 인자로 받은 문자열 s를 배열로 변환한 후 순회를 돌면서 아래 2가지 과정을 반복한다.

1. 요소가 "U"일 경우 `currLevel`을 1씩 증가시키고 "D"일 경우 `currLevel`을 1씩 감소시킨다.
2. `currLevel`이 0일 때마다 `isValley`값을 확인하여 valley인지 아닌지를 판별한다. 이때 valley일경우 `numOfVallies`를 1 증가시키고 값("U" or "D")을 확인하여 `isValley`의 값을 재할당한다.
   > `currLevel`의 값이 0일때를 기점으로 다음 값이 "U"일 경우 mountain이 되고 "D"일 경우 valley가 된다. 이러한 판별은 upOrDown이라는 별도의 유틸함수를 사용했다.

### 다른 풀이

```js
function countingValleys(n, s) {
  let valley = 0;
  let counter = 0;

  for (let step of s) {
    counter = step === "U" ? counter - 1 : counter + 1;
    if (step === "U" && counter === 0) {
      valley++;
    }
  }

  return valley;
}
```

discussions에서 찾은 javascript 풀이이다.

풀이방식도 코드도 참 간단하다.<br />"U"이후에 현재높이 (`counter`)가 0일 경우에만 valley 갯수를 1 더해준다!

문자열을 배열로 변환하지 않고 [for...of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)로 순회한 점도 좋다. 공간복잡도 측면에서 효율적인 방법인듯.

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
