# [Common Child](https://www.hackerrank.com/challenges/common-child/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

> 2020.07.30 (목요일)

## Sally

### 풀이

```js
```

### 설명

## Zello

### 풀이

```js
```

### 설명

## Huey

### 풀이

```js
```

### 설명

## Hoo

### 풀이

```js
function commonChild(s1, s2) {
  let arr2d = []; // 1

  for (let i = 0; i <= s1.length; i++) {
    // 2
    arr2d[i] = new Array(); // 3

    for (let j = 0; j <= s2.length; j++) {
      if (i === 0 || j === 0) arr2d[i][j] = 0;
      // 4
      else if (s1[i - 1] === s2[j - 1]) {
        arr2d[i][j] = arr2d[i - 1][j - 1] + 1; // 5
      } else {
        arr2d[i][j] = Math.max(arr2d[i - 1][j], arr2d[i][j - 1]); // 6
      }
    }
  }

  return arr2d[s1.length][s2.length]; // 7
}
```

### 설명

> Dynamic Programming를 사용해 LCS(Longest Common Substring)를 구하는 문제

- 문제 풀이법 접근부터 어렵고 예외 처리가 힘들어서 풀이 설명 및 DP, LCS에 대해 공부하고 풀이를 진행했다.
- LCS를 알고 있었다면 응용 문제는 아니라서 그렇게 어려운 문제는 아닌 것 같다.

1. 빈 배열을 선언한다. 자바스크립트에서 동적 2차원 배열을 사용하기 위해서는 배열 안에 배열을 선언해야 하기 때문에 일단 1차원 배열로 선언한다.
2. LCS를 구하기 위해 `0부터 입력 문자열의 길이`까지 이중 반복문을 돈다. 초기값을 0으로 지정해 사용하기 위해 `s1.length - 1`까지가 아닌 `s1.length`까지 반복문을 돈다.
3. 1번에서 말한 2차원 배열 선언하는 부분이다. 이렇게 하지 않고 `[[]]`나 `Array.from` 등을 통해 2차원 배열을 사용하면 참조하려고 할 때 아래와 같은 오류가 발생하게 된다.

```plain
TypeError: Cannot set property '0' of undefined
```

4. `i 또는 j`가 0인 경우 해당 이중 배열값은 아래와 같이 초기값인 0으로 저장된다.

- 참고: 예제는 HARRY, SALLY일 경우로 진행된다.

```
      0  H  A  R  R  Y
0 [ [ 0, 0, 0, 0, 0, 0 ],
S   [ 0, -, -, -, -, - ],
A   [ 0, -, -, -, -, - ],
L   [ 0, -, -, -, -, - ],
L   [ 0, -, -, -, -, - ],
Y   [ 0, -, -, -, -, - ] ]
```

5. 현재 index보다 1씩 작은 이중 배열의 값이 `같을 경우` 기존 수에 1을 추가하여 저장한다.

- 예제에서는 A가 처음 같은 문자이므로 A일 때 처음 1이 더해진다.

```
      0  H  A  R  R  Y
0 [ [ 0, 0, 0, 0, 0, 0 ],
S   [ 0, 0, 0, 0, 0, 0 ],
A   [ 0, 0, 1, 1, 1, 1 ],
```

6. 현재 index보다 1씩 작은 이중 배열의 값이 `같지 않을 경우` 이전 index 중 큰 수를 저장하게 된다.

- 예제에서는 SALLY의 `L`이 HARRY와 같지 않아서 기존 값인 1로 유지되는 것을 볼 수 있다.

```
      0  H  A  R  R  Y
0 [ [ 0, 0, 0, 0, 0, 0 ],
S   [ 0, 0, 0, 0, 0, 0 ],
A   [ 0, 0, 1, 1, 1, 1 ],
L   [ 0, 0, 1, 1, 1, 1 ],
L   [ 0, 0, 1, 1, 1, 1 ],
```

7. 반복문을 돌고 나면 이중 배열의 가장 마지막 값이 LCS의 최대값이 되게 된다. 해당 값을 반환하면 답이 된다.

```
      0  H  A  R  R  Y
0 [ [ 0, 0, 0, 0, 0, 0 ],
S   [ 0, 0, 0, 0, 0, 0 ],
A   [ 0, 0, 1, 1, 1, 1 ],
L   [ 0, 0, 1, 1, 1, 1 ],
L   [ 0, 0, 1, 1, 1, 1 ],
Y   [ 0, 0, 1, 1, 1, 2 ] ]
```

## Hoi

### 풀이

```js
```

### 설명

## Reese

> 재귀를 사용한 방식
> ![LCS - recursion](https://i.postimg.cc/xTfcLZXK/image.png)

> for loop을 사용한 방식
> ![LCS - for loop](https://i.postimg.cc/Hsg0NMzT/image.png)

### 풀이

```js
function commonChild(s1, s2) {
  const length1 = s1.length; // O(1)
  const length2 = s2.length; // O(1)
  if (length1 === 0 || length2 === 0) return 0;

  const memo = [];

  for (let i = 0; i <= length2; i++) {
    //O(m)
    memo.push(Array(length1 + 1).fill(0));
  }

  for (let i = 0; i < length1; i++) {
    // O(n * m)
    for (let j = 0; j < length2; j++) {
      if (s1[i] === s2[j]) {
        memo[i + 1][j + 1] = memo[i][j] + 1;
      } else {
        memo[i + 1][j + 1] = Math.max(memo[i + 1][j], memo[i][j + 1]);
      }
    }
  }

  return memo[length1][length2];
}

// 시간복잡도 : O(n * m)
// 공간복잡도 : O(n * m)
```

- 다이나믹 프로그래밍에 대해 학습하고 푼 첫 문제이다.  
  다이나믹 프로그래밍을 구현하는 여러가지 방법이 있었는데 이중 for문을 사용하는 방식이 가장 직관적이고 이해가 잘 가서 그 방식으로 풀었다.

### 설명

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료

- [LCS 설명](https://twinw.tistory.com/126)
- [백준 LCS 문제](https://www.acmicpc.net/problem/9251)
- [Longest Common Subsequence(LCS) Dynamic Programming In O(N) Space](https://www.youtube.com/watch?v=DuikFLPt8WQ)
- [Common Child HackerRank Solution](https://www.youtube.com/watch?v=ItRZRx8kvwY)
