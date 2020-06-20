# [First Unique Character in a String](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/881/)

> 2020.05.17(일)

## Hoo

### 풀이

```js
const firstUniqChar = (s) => {
  let duplicateMap = new Map();
  let uniqueMap = new Map();

  s.split("").forEach((char, index) => {
    if (uniqueMap.has(char)) {
      duplicateMap.set(char, index);
      uniqueMap.delete(char);
    } else if (duplicateMap.has(char)) {
      uniqueMap.delete(char);
    } else uniqueMap.set(char, index);
  });

  if (!uniqueMap.size) return -1;
  return uniqueMap.values().next().value;
};
```

### 설명

> 주어진 문자열에서 첫 번째로 유일한 문자의 index를 찾아 반환하는 문제

1. 중복되는 값을 저장하는 `duplicateMap`과 유일한 값을 저장하는 `uniqueMap`을 생성한다.
2. 문자열을 배열로 변환해 반복문을 돌면서 `uniqueMap 또는 duplicateMap`에 해당 문자가 존재하는지 확인한다.
3. 두 Map 중에 하나에 들어가 있다면 중복 문자라는 뜻이므로 `uniqueMap`에서 삭제해 준다.
4. 두 Map 어디에도 들어있지 않다면 처음 나온 글자이거나 유일한 문자이므로 `uniqueMap`에 담는다.
5. 반복문이 끝나고 `uniqueMap`의 첫 번째 글자를 리턴한다.
6. 만약 `uniqueMap`에 어떤 값도 없다면 문제의 조건대로 -1을 반환한다.

- 사실 duplicateMap은 문제에 직접적으로 쓰이지 않는 Map이다.
- Map을 하나로 쓰려면 각 글자마다 `count` 를 value로 가지고 있게 하면 된다. 문제를 풀고 보니 이 방법이 더 좋아 보인다.

## Hoi

### 풀이

```js
var firstUniqChar = function (s) {
  for (i = 0; i < s.length; i++) {
    const first = s.indexOf(s[i]);
    const last = s.lastIndexOf(s[i]);
    if (first === last) {
      return i;
    }
  }
  return -1;
};
```

### 설명

주어진 인자 s에 대해서 첫번째 index의 값과 마지막 인덱스의 값을 for문만큼 계산해서 만약에 first와 last가 일치한다면 순환중인 i 값을 return 하도록 하고
for문을 다 돌아도 중복이 없다면 -1을 return 하도록 문제를 풀었다.

## Reese

### 문제이해

문자열을 인자로 받아서 딱 한 번만 등장하는 유니크한 **최초의** 문자가 무엇인지 반환하는 문제이다.

### 풀이

```js
var firstUniqChar = function (s) {
  const table = new Map();
  const arr = s.split("");

  for (let i = 0, len = arr.length; i < len; i++) {
    table.has(arr[i])
      ? table.set(arr[i], table.get(arr[i]) + 1)
      : table.set(arr[i], 1);
  }

  for (let [key, value] of table.entries()) {
    if (value === 1) {
      return arr.indexOf(key);
    }
  }

  return -1;
};
```

### 설명

1. 임의의 Map을 하나 생성해두고, 문자열을 배열로 변환하여 순회하면서 문자별로 등장하는 횟수를 Map에 기록한다. (key: 해당 문자열, value: 등장 횟수)
2. `entries` 메소드로 Map을 순회하면서 value가 1인 (1번만 등장할 경우) key값을 즉시 반환하고 순회를 종료한다.

시간복잡도는 `O(n)`이다.

> - 배열 순회 : O(n)
> - Map 순회 : O(n)

<br />

**Note**

- Map은 key-value pair를 추가된 순서대로 저장하기 때문에 유니크한 '최초'의 문자를 반환할 수 있다.
- Map에도 객체처럼 `entries` 메소드가 있어서 `[key, value]` 쌍을 통째로 참조하면서 순회할 수 있다. 사용법을 익혀두자!

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
