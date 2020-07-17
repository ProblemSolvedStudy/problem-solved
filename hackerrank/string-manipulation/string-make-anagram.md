# [Strings: Making Anagrams](https://www.hackerrank.com/challenges/ctci-making-anagrams/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

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
function makeAnagram(a, b) {
  const arrA = a.split(""); // 1
  const arrB = b.split("");

  for (let i = a.length - 1; i >= 0; i--) {
    // 2
    for (let j = b.length - 1; j >= 0; j--) {
      if (arrA[i] === arrB[j]) {
        // 3
        arrA.splice(i, 1);
        arrB.splice(j, 1);
      }
    }
  }

  return arrA.length + arrB.length; // 4
}
```

### 설명

> 문자열 a와 b에서 최소 몇 개의 글자를 삭제해야 애나그램이 완성되는지 구하는 문제

- 처음에 문자열 a, b의 길이가 같다고 생각했는데, 같지 않아서 다르게 풀었었다.

1. `문자열 a, b`를 split하여 배열로 만들어 각각 저장한다.
2. 이중 반복문을 a, b의 길이만큼 역순으로 돈다.
   - 여기서 역순으로 반복문을 돌린 이유는 배열의 요소를 삭제하면서 반복시킬 것이기 때문이다.
   - 이중 반복문을 도는 이유는 a와 b의 길이가 다르고, 같다고 하여도 같은 인덱스에 같은 문자열이 있을지 알 수 없기 때문이다.
3. 배열 a, b에서 같은 요소가 있으면 각각 배열에서 `splice`를 통해 삭제한다.
   - 여기서 다른 것이 아닌 같은 것을 삭제하는 이유는 앞에서는 다른 것이라 판단했는데 뒤에서 같은 문자열이 나오면 판별하기가 어려워지기 때문이다.
4. 위에서 같은 문자열들을 삭제했으므로 배열 a, b에는 일치하지 않는 문자열들만 남아 있다. 이들을 더해서 반환하면 답이 나온다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
function makeAnagram(strA, strB) {
  const table = new Map();
  const a = "a",
    b = "b",
    both = "both";

  for (const letter of strA) {
    const value = table.get(letter);
    table.set(letter, value ? [a, value[1] + 1] : [a, 1]);
  }

  for (const letter of strB) {
    const value = table.get(letter);
    value
      ? value[0] === b
        ? table.set(letter, [b, value[1] + 1])
        : table.set(letter, [both, value[1] - 1])
      : table.set(letter, [b, 1]);
  }

  return [...table.values()].reduce((result, curr) => {
    result += curr[0] === both ? Math.abs(curr[1]) : curr[1];
    return result;
  }, 0);
}
```

### 설명

첫번째 인자로 받은 `strA`를 이루는 각 문자의 frequency를 맵핑한 후, 두번째 인자인 `strB`를 순회하면서 출처와 frequency를 업데이트 해나갔다.

여기서 출처란 '해당 문자가 어떤 문자열에서 등장하는가'를 의미한다. 예를들어 `"k": ["a", 2]`는 문자 k가 strA에서 2번 등장했다는 뜻이다.

strB를 순회하면서 strA에서 등장했던 문자의 경우 출처를 `both`로 변경한 후 frequency를 하나 차감해주고, strA에 등장하지 않았던 문자의 경우 출처를 `b`로 표기하여 맵에 추가해준다.

마지막으로 모든 frequency를 누적 합산 해주면 되는데, 이때 출처가 `both`인 경우는 절대값으로 처리해준다. 문자가 `strA`보다 `strB`에서 더 자주 등장했을 경우 해당 frequency가 마이너스 값을 가지기 때문.

시간복잡도는 **O(n + m)** 이다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
