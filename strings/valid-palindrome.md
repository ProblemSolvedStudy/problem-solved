# [Valid Palindrome](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/883/)

> 2020.05.23(토)

## Hoo

### 풀이

```js
```

### 설명

## Hoi

### 풀이

```js
var isPalindrome = function (s) {
  var regExp_1 = /[\{\}\[\]\/?.,;:|\)*~`!^\-_+<>@\#$%&\\\=\(\'\"]/gi;
  var regExp_2 = /[^A-Za-z0-9]/g;

  // const _s =  s.toLowerCase().replace(regExp , "").split("").filter(el => el !== " ");

  const str = s.toLowerCase().replace(regExp_2, "");
  const reverseStr = str.split("").reverse().join("");

  return str === reverseStr;
};
```

### 설명

1. parameter로 주어진 s 문자열이 reverse를 해도 원본 s와 같은지 판별하는 문제
2. 첫번째로 대문자를 소문자로 변경하기 위해서 toLowerCase method를 사용했다.
3. 이후에 대문자 소문자 숫자를 제외한 나머지 특수문자등은 Filtering 해주기 위해서 정규표현식을 사용
4. reverse 변수를 하나 더 만들어서 비교 연산자를 통해서 결과를 return

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
