# [Jumping on the Clouds](https://www.hackerrank.com/challenges/jumping-on-the-clouds/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup)

> 2020.06.07.(일요일)

## Hoo

### 실패한 풀이

```js
// 완전 다 틀린 풀이
function jumpingOnClouds(c) {
  let result = 0;
  let jump = 0;

  c.forEach((value, index) => {
    if (value === 0) {
      if (c[index + 1] === 1 || (jump === 1 && index + 1 >= c.length)) result++;
      if (jump < 2) jump++;
      if (jump === 2) {
        jump = 0;
        result++;
      }
    } else {
      jump = 0;
      result++;
    }
  });

  return result;
}
```

### 성공한 풀이

```js
function jumpingOnClouds(c) {
  let result = 0;

  for (let i = 0; i < c.length - 1; i++) {
    if (c[i + 2] === 0) i++;

    result++;
  }

  return result;
}
```

### 설명

> 0만 건널 수 있는 구름이 가질 수 있는 최소 이동 횟수를 구하는 문제

#### 실패한 풀이 설명

- 문제에서 건널 수 있는 구름의 조건은 `한 번에 2개까지의 구름만 넘을 수 있다`는 것과 `1의 구름은 무조건 건너뛴다`는 것이다.
- 첫 풀이가 실패한 이유는 두 개의 조건에서 `건너뛴다`의 조건을 코드로 적지 못해서이다.
- 조건을 나름대로 적었지만 건너뛰지 않고 동떨어진 `jump`라는 변수만 0~2 사이를 왔다갔다 하게 된다.

#### 성공한 풀이 설명

- if문의 늪에 빠져서 팀원들과 stackoverflow의 도움으로 문제를 다시 풀고 이해하려고 노력했다.
- 가장 중요한 것은 현재 수의 `다다음 수`를 검사해야 한다는 것이다.
- `바로 다음 수`가 0인지 1인지 비교하고 0이어서 갔는데 거기서 그 다음 수가 1이 나오면 다시 1개만 건너뛸 수 있게 돼 비교가 복잡해 진다.
- 현재 숫자가 0이고 다다음 수가 1이면 1칸만 이동하고 count에는 1이 추가된다.
- 중간에 for문의 인덱스가 1 추가되면 for문에서 기본적으로 추가되는 인덱스 1과 합쳐져 2가 더해지게 되므로 2칸 뛰어넘기를 할 수 있게 된다.

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
