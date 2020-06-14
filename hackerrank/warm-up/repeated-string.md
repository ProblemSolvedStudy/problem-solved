# [Repeated String](https://www.hackerrank.com/challenges/repeated-string/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup)

> 2020.06.13.(토요일)

## Hoo

### 풀이

```js
function repeatedString(s, n) {
  const aCount = (s.match(/a/g) || []).length;
  const quotient = Math.floor(n / s.length);
  const remainder = n % s.length;

  let result = aCount * quotient;

  for (let i = 0; i < remainder; i++) {
    if (s[i] === "a") result++;
  }

  return result;
}
```

### 설명

> a라는 문자가 반복되는 횟수를 구하는 문제

- 처음에 문제를 제대로 읽지 못해 a가 아닌 가장 많은 횟수를 구하는 문제로 착각하고 풀어 헤맸다.

1. 정규식을 활용해 기본 문자열에서의 `a의 개수`를 구한다.
2. 몫과 나머지를 구하고, 몫을 위에서 구한 a의 개수와 더해준다.
3. 나머지만큼 반복문을 돌면서 나머지에서 a이면 result를 1씩 더해 준다.
4. 최종적인 result 값을 반환하면 정답이 나온다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
// 문자열 안에 들어있는 "a"의 갯수를 구하는 함수
function getNumOfAs(string) {
  let numOfAs = 0;
  for (const char of string) {
    numOfAs += char === "a" ? 1 : 0;
  }
  return numOfAs;
}

function repeatedString(s, n) {
  const length = s.length;

  //n개의 문자 안에 문자열 s가 잘리지 않고 온전히 들어가는 횟수
  const quotient = Math.floor(n / length);

  // 잘린 문자열 s의 길이
  const remainder = n % length;

  return getNumOfAs(s) * quotient + getNumOfAs(s.slice(0, remainder));
}
```

### 설명

`n`을 `s`의 길이로 나눈 몫과 나머지를 구한 다음<br />
(`s`안에 들어있는 "a"의 갯수) \* 몫 + (잘린 문자열에 들어있는 "a"의 갯수)를 반환했다.

<br />

### 다른 풀이

```js
// number of times string can be repeated within limit n
const numOfRepeats = Math.floor(n / s.length);

// additional number of strings to get to the limit n
const remainderString = n % s.length;

// find number of matches in a string
let matches = (s.match(/a/g) || []).length;

// multiply number of matches in a string with number of repeatations
matches = matches * numOfRepeats;

// find number of matches in remainder string
const remainderMatches = (s.substring(0, remainderString).match(/a/g) || []).length;

// add it up
return matches + remainderMatches;
```

### 배운 점

1. 문자열에 들어있는 "a"의 갯수를 구할 때 `String.prototype.match(regexp)` 메서드를 사용했다. 이 메서드의 반환값은 정규표현식에 매치되는 모든 문자열을 담은 **배열**이다.
2. `quotient` -> `numOfRepeats` / `remainder` -> `remainderString`이라고 네이밍했더니 같은 내용이더라도 가독성이 훨씬 좋다. 네이밍에 좀 더 신경쓰자!

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
