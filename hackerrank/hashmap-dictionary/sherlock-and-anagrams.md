# [Sherlock and Anagrams](https://www.hackerrank.com/challenges/sherlock-and-anagrams/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

> 2020.07.09 (목)

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
```

### 설명

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제 이해

문자열 하나 안에 서로 Anagram 관계인 substring이 몇 쌍 나오는지 구하는 문제이다.  
`abba` 의 경우 `[a, a]`, `[ab, ba]`, `[b, b]`, `[abb, bba]` 총 4쌍의 anagram pair가 나온다.

### 풀이

```js
function updateMap(map, key) {
  map.has(key) ? map.set(key, map.get(key) + 1) : map.set(key, 1);
}

function sherlockAndAnagrams(s) {
  const subStrings = new Map();

  for (let i = 0, len = s.length; i < len; i++) {
    updateMap(subStrings, s[i]);
    for (let j = i + 1; j < len; j++) {
      const key = s.slice(i, j + 1);
      updateMap(subStrings, key.split("").sort().join(""));
    }
  }

  let numOfAnaPairs = 0;
  subStrings.forEach((value) => {
    if (value > 1) {
      for (let i = 1; i <= value - 1; i++) {
        numOfAnaPairs += i;
      }
    }
  });

  return numOfAnaPairs;
}
```

### 설명

1. 인자로 받은 문자열 `s`를 순회하면서 여기서 나올 수 있는 모든 substring의 갯수를 맵핑한다.  
   (key: substring, value: substring의 갯수)  
   여기서 포인트는 **anagram 관계임을 알기 위해서 `ab`와 `ba`의 갯수가 동일한 key값의 value로 간주되어야 한다**는 점이다. 예를들면 substring `ab`에 대해 맵에서 ab의 value를 1 더해주고, `ba`가 등장했을 때에도 역시 ab의 value를 1 더해주는 것이다. 이렇게 anagram 관계인 substring을 하나의 key값으로 간주하기 위해 `sort`를 사용하여 substring을 정렬해주었다.

   1번 과정을 거쳐 `abba`의 모든 substring을 맵핑하면 다음과 같은 Map이 완성된다.

   `Map { 'a' => 2, 'ab' => 2, 'abb' => 2, 'aabb' => 1, 'b' => 2, 'bb' => 1 }`

2. 이제 anagram 관계인 substring pair가 몇 개인지 계산한다.  
   value가 1인 substring의 경우 pair를 이룰 수 없기 때문에 고려하지 않는다.  
   anagram pair를 구할때는 1부터 value보다 1작은 수 까지 모든 정수의 합을 구해주면 된다.  
   만약 value가 `4`라면 여기서 나올 수 있는 pair의 갯수는 `1 + 2 + 3 = 6`이 된다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
