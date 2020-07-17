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
```

### 설명

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
