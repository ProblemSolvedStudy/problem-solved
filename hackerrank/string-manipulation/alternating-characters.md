# [Alternating Characters](https://www.hackerrank.com/challenges/alternating-characters/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

> 2020.07.23 (목요일)

## Zello

### 풀이

```js
```

## Huey

### 풀이

```js
```

## Hoo

### 풀이

```js
function alternatingCharacters(s) {
  let result = 0;

  for (let i = 0; i < s.length - 1; i++) {
    if (s[i] === s[i + 1]) result++;
  }

  return result;
}
```

### 설명

> 한 문자가 연속으로 등장하게 하지 않기 위해 삭제해야 하는 문자의 개수를 구하는 문제

- 반복문을 돌면서 `현재 문자`와 `다음 문자`가 같으면 결과값에 1을 더해 주고 결과값을 반환하면 된다.
- 참고: 자바스크립트에서는 문자열도 일종의 `배열`이기 때문에 length나 값 참조는 배열과 똑같이 할 수 있다. charAt같은 메소드를 추가로 사용하지 않아도 되서 편하다.

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
