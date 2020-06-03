# [Reverse String](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/879/)

> 2020.05.17(일)

## Hoo

### 풀이

```js
const reverseString = (s) => s.reverse();
```

### 설명

> 배열로 들어온 문자열을 뒤집어 반환하는 문제

자바스크립트의 내장되어 있는 메소드를 사용해 배열의 순서를 뒤집어 문제를 해결했다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

#### Solution 1

```js
var reverseString = function (s) {
  return s.reverse();
};
```

### 설명

`reverse` 메소드를 사용해서 배열 내 원소의 순서를 뒤집었다.<br />
`reverse` 메소드는 원본 배열을 직접적으로 수정하여 그 참조를 리턴해준다.

<br />

#### Solution 2

```js
const reverseString = function (s) {
  const size = s.length;
  let temp;

  for (let i = 0, middle = size / 2; i < middle; i++) {
    temp = s[i];
    s[i] = s[size - 1 - i];
    s[size - 1 - i] = temp;
  }
};
```

### 설명

배열의 가운데의 위치한 원소를 기준으로 양 옆에 위치한 원소들을 swap하였다.<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
