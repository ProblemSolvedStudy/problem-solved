# [Alternating Characters](https://www.hackerrank.com/challenges/alternating-characters/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

> 2020.07.23 (목요일)

## Zello

### 풀이

```js
function alternatingCharacters(s) {
  let answer = 0;
  let char = "";

  for (let i = 0; i < s.length; i++) {
    if (char == s[i]) {
      ++answer;
    } else {
      char = s[i];
    }
  }

  return answer;
}
```

### 설명

#### 문제 해석

> a 와 b 만 포함된 문자열이 주어지는데, 일치하는 인접 문자가 없는 문자열로 변화시키기 위해서 삭제해야 할 최소 문자 갯수를 반환하는 함수를 작성.

#### 코드

- 사전 작업

1. 기준 문자로 다루기 위한 char 변수를 설정.
2. 기준 문자가 유지될때 일치하는 인접 문자로 판단하여 지워져야 할 문자 갯수 카운트를 위한 answer 변수를 설정.

- 코드 설명

1. 0번째 인덱스부터 검사를 한다.
   1-1. 만약 기준 문자가 i 번째 인덱스의 문자와 일치한다면
   -> 지워야할 문자 갯수를 카운트하는 변수의 크기를 1 증가
   1-2. 그렇지 않다면
   -> 기준 문자를 i 번째 인덱스의 문자로 변경 (인접한 글자가 다른 글자이기 때문)

#### 시간 복잡도

> O(N)

문자열 s 의 처음부터 마지막까지 순회를 하므로 **O(N)** 의 시간 복잡도를 갖는다.

#### 기타

String 을 Array 처럼 Handling 할 수 있다.

```js
const testString = "testString";

console.log(testString[0]); // t
console.log(testString.length); //10
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
function alternatingCharacters(s) {
  return s.split("").reduce((deletions, char, i, arr) => {
    if (char === arr[i - 1]) deletions++; // O(1)
    return deletions;
  }, 0);
  // O(n)
}
```

### 설명

인자로 받은 문자열을 배열로 강제변환한 뒤 reduce를 사용하여 모든 요소를 순회하면서 인접한 문자(`arr[i]`)와 현재 처리하고 있는 문자(`char`)를 비교하고, 두 값이 같을 경우 지워야 하는 문자의 갯수(`deletions`)를 1 더해주었다.  
reduce 메소드는 배열의 모든 요소에 대해 reducer를 실행하기 때문에 O(n)의 시간복잡도를 가지고, reducer 내부에서 값을 비교하고 업데이트하는 로직은 O(1)의 시간복잡도를 가지기 때문에 전체적인 시간복잡도는 O(n) 이다.

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
