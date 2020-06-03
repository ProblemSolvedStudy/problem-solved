# [Valid Palindrome](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/883/)

> 2020.05.23(토)

## Hoo

### 풀이


```js
const isPalindrome = (s) => {
    const regex = /(\w)/g;
    const onlyAlphanumeric = s.toLowerCase().match(regex);
   
    if (!onlyAlphanumeric) return true;
    
    const halfSize = Math.floor(onlyAlphanumeric.length / 2);
    let result = true;
    
    for (let i = 0; i < halfSize; i++) {
        let last = onlyAlphanumeric.length - 1 - i;
        
        if (onlyAlphanumeric[i] !== onlyAlphanumeric[last]) {
            result = false;
        }
    }
    
    return result;
};
```

### 설명

> 문자열의 영숫자가 회문인지 판별하는 문제

1. 정규식을 활용해 `영숫자`만 배열로 저장한다.
2. 이제 저장된 배열이 회문인지 확인하면 되는데, 들어온 문자열이 `".,"`와 같은 경우 길이가 없다고 나오므로 if문을 통해 예외처리를 해준다.
- 이 때, 꼭 배열 자체를 비교할 필요는 없다. `join`을 활용해 문자열로 만들고, 그것을 뒤집은 값과 비교해도 된다. 여기서 나는 배열인 채로 비교했다. 
3. 그리고 전체 배열 크기의 반을 구한 다음에 그만큼만 반복문을 돌면서 값이 같은지 확인한다. 
4. 하나라도 다르면 false가 되어 결과로 반환하게 된다. 

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

### 문제이해

문자열s를 인자로 받아서 유효한 palindrome인지를 판별하여 boolean 값으로 반환하는 문제이다.<br />
`only alphanumeric characters and ignoring cases` -> a-z, A-Z, 0-9만 고려해서 문제를 풀면 된다.

> palindrome이란, 거꾸로 읽어도 제대로 읽는 것과 같은 문장이나 낱말, 숫자, 문자열(sequence of characters) 등을 말한다.

### 풀이

```js
const isPalindrome = function (s) {
  const onlyAlphanumeric = s
    .toLowerCase()
    .split("")
    .filter((char) => {
      const code = char.charCodeAt(0);
      const isNumber = code >= 48 && code <= 57;
      const isAlphabet = 97 <= code && code <= 122;
      return isNumber || isAlphabet;
    });

  return onlyAlphanumeric.join("") === onlyAlphanumeric.reverse().join("");
};
```

### 설명

`charCodeAt` 메소드를 사용해서 문자의 utf-16 코드값을 구하고 alphanumeric character에 해당하는지의 여부를 판별했다.

## Ed

### 풀이

#### 절반 나누기

```js
var isPalindrome = function (s) {
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
var isPalindrome = function (s) {
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
