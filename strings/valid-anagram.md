# [Valid Anagram.md](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/883/)

> 2020.05.23(토)

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
var isAnagram = function (s, t) {
  const _t = t.split("").sort().join("");
  const _s = s.split("").sort().join("");
  // _t.shift()
  // _s.shift()

  return _t === _s;
};
```

### 설명

> t 문자열과 s 문자열의 아나그램을 확인하는 문제

1. 아나그램이 뭔지 확인해 보니 같은 문자를 포함하고 있지만 다른 의미를 지니는 말장난 같은 의미라는걸 파악
2. 문자열의 정렬을 위해서 split을 사용해서 배열로 만듬
3. 각각의 문자열을 sort하면 이 문지열의 구성이 같은지를 확인할 수 있으니 sort를 통해서 문자를 정렬
4. join으로 다시 문자열로 만들어 준 후 비교 연산자를 통해서 결과를 return

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
