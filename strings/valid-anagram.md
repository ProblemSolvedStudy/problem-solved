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
```

### 설명

## Ed

### 풀이

```js
var isAnagram = function(...words) {
    const sortedWord = word => word.split("").sort().join("");
    return new Set(words.map(sortedWord)).size === 1 ? true : false;
};
```

### 설명

애너그램을 판별하는 문제. 입력된 문자열들(이 문제에선 2개가 입력된다)을 순회하면서 한 글자씩 자르고, 순서를 정렬한 뒤에 다시 붙인다. 문자열들을 Set에 담고, Set의 크기가 1이 아니라면(=중복이 있다면) 거짓을 반환하고 아니면 참을 반환한다. 이 문제의 경우, 2개의 문자열만 주어지기 때문에 굳이 Set에 담지 않고 2개를 별개로 비교하는게 더 효율적이다.

---

## 참고자료
