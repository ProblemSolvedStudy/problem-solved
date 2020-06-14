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
* 단, 문제의 입력값 중에 d가 a의 길이보다 크다면 나머지 값으로 계산하는 등의 예외 처리는 해 주면 더 좋을 것 같다. 일단 나는 통과과 되어서 따로 해 주지는 않았다.

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
