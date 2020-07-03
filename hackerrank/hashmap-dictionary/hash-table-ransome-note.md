# [Hash Tables: Ransom Note](https://www.hackerrank.com/challenges/ctci-ransom-note/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

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

### 풀이

```js
function checkMagazine(magazine, note) {
  let mapOfMagazine = new Map();

  magazine.forEach((value) => {
    if (!mapOfMagazine.has(value)) mapOfMagazine.set(value, 1);
    else mapOfMagazine.set(value, mapOfMagazine.get(value) + 1);
  });

  return note.every((value) => {
    if (!mapOfMagazine.get(value)) return false;

    mapOfMagazine.set(value, mapOfMagazine.get(value) - 1);
    return true;
  })
    ? "Yes"
    : "No";
}
```

### 설명

> magazine에 note의 모든 단어가 포함되어 있는지 확인하는 문제

- `Map`과 `every`를 사용해 풀 수 있었다.

`Map`에는 magazine을 반복문을 돌면서 단어의 개수를 저장한다.  
그리고 note를 `every` 반복문을 돌면서 Map의 value가 `undefined 또는 0`이 아닐 경우에 false를 반환하게 만든다.  
이 문제에서는 1개만 false여도 false이기 때문에 every를 사용하면 추가적인 변수를 사용하지 않고 풀 수 있다.

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
