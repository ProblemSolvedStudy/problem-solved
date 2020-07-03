# [Two Strings](https://www.hackerrank.com/challenges/two-strings/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

> 2020.07.02 (목요일)

## Zello

### 풀이

```js
```

## Huey

### 풀이

```js
```

## Hoo

### 첫번째 풀이

```js
function twoStrings(s1, s2) {
  let mapOfPair = new Map();
  let mapOfResult = new Map();

  const s1List = s1.split("");
  const s2List = s2.split("");

  s1List.forEach((value) => {
    if (!mapOfPair.has(value)) mapOfPair.set(value, 1);
    else mapOfPair.set(value, mapOfPair.has(value) + 1);
  });

  s2List.forEach((value, index) => {
    if (!mapOfPair.has(value)) mapOfResult.set(value, false);
    else mapOfResult.set(value, true);
  });

  return [...mapOfResult.values()].some((value) => value) ? "YES" : "NO";
}
```

### 두번째 풀이

```js
function twoStrings(s1, s2) {
  let setOfs1 = new Set(s1);

  return s2.split("").some((value) => setOfs1.has(value)) ? "YES" : "NO";
}
```

### 설명

> 두 개의 문자 사이에 같은 문자열이 존재하는지 판별하는 문제

#### 첫번째 풀이

`Map`을 2개를 사용한다. 1개는 `s1`을 저장하기 위해 쓰이고, 1개는 `true, false` 값을 저장하기 위해 쓰인다.  
`s1` 리스트가 반복문을 돌면서 맵에 개수가 저장된다.  
`s2` 리스트로 s1 문자열 중에 같은 문자열이 존재하는지 판단해 Map에 저장하며 반복한다.  
마지막 반환할 때 `mapOfResult`에 `true`가 있는지를 some 메소드를 통해 판별한다.

- 하지만, Map을 두 개나 만들고 불필요하게 반복문을 돌게 되는 것 같아 스터디에서 알게 된 내용으로 다시 풀어 보았다.

#### 두번째 풀이

`Set`에 `s1`을 저장한다. 여기서 처음 알게 된 사실은 **Set에는 String이 들어가도 하나씩 배열로 바뀌면서 저장된다는 것이다.** 속도가 느리지 않을까 싶었는데 Stackoverflow를 보니 빠르기는 일반 배열보다 빠른 것 같다.  
그리고 `s2`가 반복문(some)을 돌면서 `Set`에 문자열이 있는지 확인한다.  
여기서 some이 forEach보다 좋은 점은 `true`가 하나라도 존재하면 바로 반환한다는 것이다. 첫번째 풀이에서 이 점 때문에 Map을 하나 더 만들었었는데 some을 사용하면 이런 불편함이 없어진다.

- 고차함수를 더 잘 활용해야겠다는 생각이 든다.

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
