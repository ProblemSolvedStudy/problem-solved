# [Frequency Queries](https://www.hackerrank.com/challenges/frequency-queries/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

> 2020.07.16 (목요일)

## Zello

### 풀이

```js
```

## Huey

### 풀이

```js
```

## Hoo

### 풀이

```js
function freqQuery(queries) {
  let map = new Map(); // 1
  let result = [];

  queries.forEach(([type, val]) => {
    // 2
    const mVal = map.get(val);
    switch (type) {
      case 1: // 3
        mVal ? map.set(val, mVal + 1) : map.set(val, 1);
        break;
      case 2: // 4
        if (mVal) map.set(val, mVal - 1);
        break;
      case 3: // 5
        result.push([...map.values()].some((v) => v === val) ? 1 : 0);
        break;
      default:
        break;
    }
  });

  return result;
}
```

### 설명

> 타입과 값이 넘어오는 이중 배열에서 type 3일 때의 빈도수 TF 값을 구하는 문제

- 처음에 문제를 이해하지 못하고 설명을 듣고 이해했다. 문제를 더 꼼꼼하게 읽어야겠다.
- 풀이 설명을 듣고 기억에 남아서 그대로 풀었다.

1. value의 개수를 저장하기 위한 map과 최종적으로 반환하기 위한 빈 배열을 생성한다.
2. `queries`로 반복문을 돌며 타입을 체크하고 switch문을 돈다.
3. 타입이 1이면 map에 값을 저장한다.
4. 타입이 2이면 map에서 1을 빼 주어 삭제한다.
5. 타입이 3이면 value들 중에 일치하는 것이 있는지 확인해 값을 배열에 담는다.
6. 반복문이 끝나고 나온 result를 반환한다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
function freqQuery(queries) {
  const ds = new Map();
  const result = [];

  const ops = {
    1: (data) => {
      const value = ds.get(data); // O(n) (worst)
      ds.set(data, value ? value + 1 : 1);
    },
    2: (data) => {
      const value = ds.get(data); // O(n) (worst)
      if (value) {
        ds.set(data, value - 1);
      }
    },
    3: (freq) => result.push([...ds.values()].some((data) => data === freq) ? 1 : 0), // O(n^2) (worst)
  };

  queries.forEach(([op, data]) => ops[op](data)); // O(n)

  return result;
}
```

### 설명

1, 2, 3 operation 처리 로직을 `ops` 객체에 명시해두고 `queries` 인자를 순회하면서 요청을 처리해주었다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
