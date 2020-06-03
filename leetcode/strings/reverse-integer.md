# [Reverse Integer](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/880/)

> 2020.05.17(일)

## Hoo

### 풀이

```js
const reverse = (x) => {
  const MAX_NUMBER = Math.pow(2, 31);
  const abs_number = Math.abs(x);

  let reverseNumbers = Number(abs_number.toString().split("").reverse().join(""));
  if (reverseNumbers > MAX_NUMBER) return 0;
  let answer = x < 0 ? -reverseNumbers : reverseNumbers;

  return answer;
};
```

### 설명

> 숫자를 뒤집어서 출력하는 문제.
> ​

#### 주의할 점

1. 음수일 경우에는 음수는 유지한 채 숫자만 reverse되어야 한다.
2. reverse했을 때 제일 앞자리가 0이면 0은 생략되어 출력된다. 즉, 타입이 `number`여야 한다.
3. 결과값 양음수 모두 `2의 31승`을 넘어가면 0을 출력하게 해야 한다.

- reverse는 내장함수를 이용해 배열로 바꾸고 reverse한 뒤 다시 합쳐 숫자형으로 바꿔 주면 된다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제이해

숫자를 뒤집어서 반환해주는 문제다.<br />
음수일 경우 숫자만 뒤집고 `-`를 붙여서 반한해주면 된다.<br />

- 뒤집어진 숫자의 앞에 위치하는 0의 경우 표시하지 않는다.
- 인자가 −2<sup>31</sup>보다 작거나 2<sup>31</sup> − 1보다 클 경우 0을 반환한다.

### 풀이

```js
const reverse = function (x) {
  const limit = Math.pow(2, 31),
    min = limit * -1,
    max = limit - 1;

  const reversed = parseInt(Math.abs(x).toString().split("").reverse().join(""));

  return reversed < min || reversed > max ? 0 : Math.sign(x) * reversed;
};
```

### 설명

1. 숫자 `x`를 절대값으로 변환 (`Math.abs`)
2. 숫자 -> 문자열 변환 (`toString`)
3. 문자열 -> 배열 변환 (`split`)
4. 배열 내 요소 순서 역순으로 변환 (`reverse`)
5. 배열 -> 문자열 (`join`)
6. 문자열 -> 숫자 (`parseInt`)
7. 최소값, 최대값 범위에 속하는지 여부에 따라 `0` 또는 1 ~ 6에서 처리한 결과값에 양/음수에 따른 부호를 붙여서 반환 (`Math.sign`)

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
