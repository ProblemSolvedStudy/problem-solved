# [2 x n 타일링](https://programmers.co.kr/learn/courses/30/lessons/12900)

> 2020.05.30(토)

## Hoo

### 풀이

```js
const solution = (n) => {
  return recursive(n);
};

const recursive = (n) => {
  let nums = [];

  for (let i = 1; i <= n; i++) {
    nums[i] = i < 3 ? i : nums[i - 1] + nums[i - 2];
    nums[i] %= 1000000007;
  }

  return nums[n];
};
```

### 설명

n의 증가로 타일 개수를 세어 봤을 때의 표이다.

<table style="border-collapse: collapse; width: 34.7674%; height: 528px;" border="1"><tbody><tr><td>* n = 1</td><td>1</td></tr><tr><td>* n = 2</td><td>2</td></tr><tr><td>* n = 3</td><td>3</td></tr><tr><td>* n = 4</td><td>5</td></tr><tr><td>* n = 5</td><td>8</td></tr><tr><td>* n = 6</td><td>13</td></tr><tr><td>* n = 7</td><td>21</td></tr><tr><td>* n = 8</td><td>34</td></tr><tr><td>* n = 9</td><td>55</td></tr><tr><td>* n = 10</td><td>89</td></tr><tr><td>* n = 11</td><td>144</td></tr><tr><td>* n = 12</td><td>233</td></tr><tr><td>* n = 13</td><td>377</td></tr><tr><td>* n = 14</td><td>610</td></tr></tbody></table>

- `n = n-1 + n-2` 구조를 띠고 있다.
- 앞에서 풀었던 피보나치 수와 비슷하게 풀면 된다.
- 단, 주의할 것은 `1000000007`을 나눈 나머지 값으로 저장하면서 for문을 돌아야 한다는 것이다.

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
