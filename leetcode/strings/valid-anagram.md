# [Valid Anagram.md](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/883/)

> 2020.05.23(토)

## Hoo

### 풀이

```js
const isAnagram = (s, t) => {
  const listS = s.split("").sort();
  const listT = t.split("").sort();

  return JSON.stringify(listS) === JSON.stringify(listT);
};
```

### 설명

> 주어진 문자열이 유효한 anagram인지 아닌지 판별하는 문제

문자열의 길이와 알파벳 구성(개수)가 동일하면 `true`, 아니면 `false`를 반환하게끔 해야 한다.

처음에는 반복문을 돌게 해 값을 하나하나 비교해 참거짓을 반환했는데, 그냥 비교할 수 있는 방법이 있어서 그렇게 바꿔서 사용했다.

자바스크립트의 경우 배열 자체를 비교할 수 있는 메소드는 없지만 값을 **json 문자열로 만들어 주는** `*JSON.stringify` 를 이용해 두 배열을 비교했다.

아니면 아예 `join("")` 을 사용해 문자열을 만들어 문자열끼리 비교해 줄 수도 있다.

## Hoi

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

## Reese

### 문제이해

2개의 문자열을 인자로 받아서 둘이 서로 anagram 관계인지 판별하여 boolean 값을 반환하는 문제이다.

> anagram이란, 한 단어를 구성하는 글자의 개수를 그대로 유지하면서 순서만 바꾼 단어를 일컫는 말

### 풀이

#### 방법 1

```js
var isAnagram = function (s, t) {
  const sortedS = s.split("").sort().join("");
  const sortedT = t.split("").sort().join("");
  return sortedS === sortedT;
};
```

### 설명

hoi와 동일한 풀이이다. 두 문자열을 배열로 변환하고 정렬하여 다시 문자열로 바꾼 뒤, 동일한지 비교하는 것이다.

<br />

### 방법 2

```js
const isAnagram = function (s, t) {
  if (s.length !== t.length) return false;

  const map = {};

  for (let i = 0; i < s.length; i++) {
    map[s[i]] ? map[s[i]]++ : (map[s[i]] = 1);
  }

  for (let i = 0; i < t.length; i++) {
    if (map[t[i]]) {
      map[t[i]]--;
    } else {
      return false;
    }
  }

  return true;
};
```

### 설명

- 두 문자열의 길이를 비교해서 길이가 다를 경우 early return을 해준다.
- 문자열 s를 순회하면서 해당 문자가 객체의 키값으로 존재하는지 확인하면서 문자가 등장하는 횟수를 업데이트 한다. (방법 1과 동일)
- 문자열s 순회가 끝나면 t를 순회하면서 객체를 탐색한다. 문자가 객체의 키값으로 존재하면 갯수(value)를 하나씩 차감해 나가고, 키값으로 존재하지 않으면 즉시 false를 리턴한다.

## Ed

### 풀이

```js
var isAnagram = function (...words) {
  const sortedWord = (word) => word.split("").sort().join("");
  return new Set(words.map(sortedWord)).size === 1 ? true : false;
};
```

### 설명

애너그램을 판별하는 문제. 입력된 문자열들(이 문제에선 2개가 입력된다)을 순회하면서 한 글자씩 자르고, 순서를 정렬한 뒤에 다시 붙인다. 문자열들을 Set에 담고, Set의 크기가 1이 아니라면(=중복이 있다면) 거짓을 반환하고 아니면 참을 반환한다. 이 문제의 경우, 2개의 문자열만 주어지기 때문에 굳이 Set에 담지 않고 2개를 별개로 비교하는게 더 효율적이다.

---

## 참고자료
