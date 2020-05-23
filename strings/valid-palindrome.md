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
```

### 설명

## Reese

### 풀이

```js
```

### 설명

## Ed

### 풀이

#### 절반 나누기

```js
var isPalindrome = function(s) {
    const specialChar = /[\{\}\[\]\/?.,;:|\)*~`!^\-+<>@\#$%&\\\=\(\'\"\s]/gi; 
    const alpha = s.split(specialChar).join("").toLowerCase();
    const centerIndex = Math.floor(alpha.length / 2);
    const halfPrev = alpha.substring(0, centerIndex);
    let halfAfter;
    if (alpha.length % 2 === 0) halfAfter = alpha.substring(centerIndex);
    else halfAfter = alpha.substring(centerIndex + 1);
    return halfPrev.split("").join("") === halfAfter.split("").reverse().join("");
};
```

#### 그대로 뒤집기

```js
var isPalindrome = function(s) {
    const specialChar = /[\{\}\[\]\/?.,;:|\)*~`!^\-+<>@\#$%&\\\=\(\'\"\s]/gi; 
    const alpha = s.split(specialChar).join("").toLowerCase();
    return alpha.split("").join("") === alpha.split("").reverse().join("");
};
```

### 설명

거꾸로 해도 똑같은 단어인 펠린드롬을 판별하는 문제. 두 가지 방법으로 풀었는데 후자가 훨씬 효율적이고 맞는 접근 방식이라고 생각한다. 두 가지 모두 특수문자를 정규표현식으로 지우고, 남은 알파벳을 소문자로 변경하는 부분은 동일하다. 첫번째 방식의 경우 예를 들어, "토마토" 에서 "마" 를 찾고, 해당 단어의 앞 뒤를 비교해서 참 거짓을 반환하도록 한다. 절반을 나누는 과정에서, 전체 문자열의 길이가 짝수면 한 단어가 증발하는 에러가 발생하기 때문에 별도로 조건문을 걸어줘야 한다. 

두번째 방식은 절반을 나눌 것도 없이 그냥 그대로 단어 전체를 `reverse()` 하고 비교하면 된다. "토마토"는 거꾸로 해도 "토마토"니까 굳이 "마"를 기준으로 자를 필요가 없다. 쉽게 생각하자...

---

## 참고자료
