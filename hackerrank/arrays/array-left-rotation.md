# [Arrays: Left Rotation](https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays)

> 2020.06.13.(토요일)

## Hoo

### 풀이

```js
const rotLeft = (a, d) => a.concat(a.splice(0, d));
```

### 설명

> 1차원 배열이 전해진 숫자만큼 오른쪽으로 회전하도록 만드는 문제.

leetcode의 rotate array 문제보다 덜 까다로운 문제이다.  
leetcode에서는 추가 메모리를 사용하면 안됐기 때문에 하나씩 떼어서 붙여주는 방식을 택했다.  
이번 문제는 splice를 시켜 바로 concat으로 붙여 주어 간단하게 해결했다.

- 단, 문제의 입력값 중에 d가 a의 길이보다 크다면 나머지 값으로 계산하는 등의 예외 처리는 해 주면 더 좋을 것 같다. 일단 나는 통과과 되어서 따로 해 주지는 않았다.

## Hoi

### 풀이

```js
function rotLeft(a, d) {
  const arr = Array.from({ length: a }, (v, i) => i + 1);

  for (let i = 0; i < d; i++) {
    arr.push(arr.shift());
  }
  return arr;
}
```

### 설명

left-rotation 문제는 일단 저번에 풀었던 문제 형식이지만 이번에는 문제 접근을 좀 잘못했다.

a가 array의 length가 전달되는줄 알았고 d가 left rotation의 count로 생각했는데 알고보니까 a는 그냥 array그 자체로 전달되는 거였다 ....

const arr = Array.from({ length: a }, (v, i) => i + 1); 전달된 Number 인자를 Array Type으로 변환해 주는 식만 제거하면 문제 통과를 잘 한다.

## Reese

### 풀이

```js
function rotLeft(a, d) {
  for (let i = 0; i < d; i++) {
    a.push(a.shift());
  }
  return a;
}
```

### 설명

예전에 leetcode에서 한 번 풀었던 문제이다. 차이점이라면 hackerrank에서는 in-place로 풀어야 한다는 제약사항이 없다는 것 정도?

`shift()`의 반환값(제거된 요소)를 다시 a에 push하는 식으로 접근했다.

## Ed

### 풀이

```js
function rotLeft(a, d) {
    const arr = a;
    for(let i = 0; i < d; i++) {
        const element = arr.shift();
        arr.push(element);
    }
    return arr;
}
```

### 설명

배열을 왼쪽으로 돌리는 문제. d가 1이라면, 0번째 요소를 배열 맨 마지막 요소에 붙이면 된다. 숫자 d만큼 순회를 돌며, `shift()`한 요소를 `push()`로 뒤에 붙이면 된다.

---

## 참고자료
