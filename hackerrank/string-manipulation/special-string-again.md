# [Special String Again](https://www.hackerrank.com/challenges/special-palindrome-again/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

> 2020.07.30 (목요일)

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
function substrCount(n, s) {
  let count = 0;
  let consecutiveLetters = "";

  for (let i = 0; i < n; ++i) {
    if (!consecutiveLetters || consecutiveLetters[0] === s[i]) {
      // 1
      consecutiveLetters += s[i];
    } else {
      let j = 1;
      while (j <= consecutiveLetters.length && s[i + j] === consecutiveLetters[0]) {
        // 2
        ++j;
        ++count;
      }
      consecutiveLetters = s[i];
    }

    count += consecutiveLetters.length;
  }

  return count;
}
```

### 설명

> 문자열에서 대칭되는 문자열 개수를 찾는 문제

- `time limit`으로 계속 풀지 못해 솔루션을 보고 이해하는 방식을 택했다.

1. 문자열을 반복문을 돌면서 나타나는 빈도수가 `consecutiveLetters`에 저장된다.
   - `consecutiveLetters`는 index가 0일 때이거나 연속 문자가 등장할 경우 추가시면서 저장한다.
2. consecutiveLetters를 기준으로 `s[i + j]` 값을 비교하며 조건에 만족하면 count가 1씩 추가되게 한다.
   - 여기서 **aaaa**와 같이 같은 문자열이 반복되면 `else문`에 들어오지 않아서 while문에 들어오지 않고 length를 저장해 개수를 구하게 된다.
3. while문이 끝나게 되면 `현재의 문자 값`으로 consecutiveLetters를 변경한다.
4. 현재의 길이를 count에 저장함으로써 `하나의 문자의 개수`와 `반복 문자열의 개수`를 저장하게 된다.
5. 반복문이 끝나고 나오게 되는 `count` 값을 반환한다.

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

- [string manipulation 문제 푸는 짧은 팁](https://ally10.tistory.com/6)
-
