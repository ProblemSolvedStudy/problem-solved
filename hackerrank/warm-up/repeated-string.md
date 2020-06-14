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
```

### 설명

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
