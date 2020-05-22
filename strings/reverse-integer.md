# [Reverse Integer](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/880/)

> 2020.05.17(일)

## Hoo

### 풀이

```js
const reverse = x => {
    const MAX_NUMBER = Math.pow(2, 31);
    const abs_number = Math.abs(x);

    let reverseNumbers = Number(abs_number.toString().split('').reverse().join(''));
    if (reverseNumbers > MAX_NUMBER) return 0;
    let answer = (x < 0) ? -reverseNumbers : reverseNumbers;

    return answer;
}
```

### 설명

> 숫자를 뒤집어서 출력하는 문제.
​
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
