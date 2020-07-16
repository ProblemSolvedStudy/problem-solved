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
function sherlockAndAnagrams(s) {
  const sList = s.split(""); // 1
  let mapOfSub = new Map(); // 2

  const makeSubList = (len) => {
    // 3
    mapOfSub.clear();
    sList.forEach((ss, i) => {
      const splitStr = s.substring(i, i + len);
      const sortStr = splitStr.split("").sort().join("");
      if (sortStr.length === len) {
        mapOfSub.has(sortStr)
          ? mapOfSub.set(sortStr, mapOfSub.get(sortStr) + 1)
          : mapOfSub.set(sortStr, 1);
      }
    });
  };

  const isAnagram = (len) => {
    // 4
    makeSubList(len);
    return [...mapOfSub.values()].reduce((prev, curr) => prev + (curr * (curr - 1)) / 2, 0);
  };

  return sList.reduce((prev, curr, currIndex) => {
    if (!currIndex) return prev + 0;
    return prev + isAnagram(currIndex);
  }, 0);
}
```

### 설명

> 입력된 문자열에서 발생하는 모든 Anagram의 수를 반환하는 문제

- 이 문제는 Map을 쓰지 않고 풀었다가 한참을 고생한 문제이다. `Map의 성능`을 체감하게 된 문제이다.
- 일반 배열로 풀게 되면 `time limit`이 더 많이 걸리게 되는 것 같다.

1. 우선 반복문을 돌리기 위해 입력된 문자열을 배열로 만든다.
2. 자른 문자열의 개수를 저장하기 위해 `Map`을 새로 선언한다.
3. `makeSubList`는 len이라는 인자를 받아 해당 숫자만큼 자르고 정렬해 개수를 `앞서 만든 Map`에 저장한다.
   이 때, `makeSubList`가 reduce 안에서 불려서 바로 계산되기 때문에 함수 시작 부분에서 `.clear()`를 통해 Map을 비워준다.
4. `isAnagram`에서는 `makeSubList` 함수에서 만들어진 Map을 바탕으로 Anagram의 개수를 센다.

- Anagram의 개수를 세는 방법인 `(curr * (curr - 1)) / 2`은 규칙을 바탕으로 만들어진 것이다.

s가 `kkkk`일 때 잘린 문자열, 중복 개수, 애나그램 개수는 아래 표와 같다.  
애나그램 개수는 위의 식과 같은 규칙을 가지고 있어 계산식으로 간단하게 풀 수 있다.

| 잘린 문자열 | 중복 개수 |      애나그램 개수       |
| ----------- | --------- | :----------------------: |
| k           | 4         | ( 4 \* (4 - 1) ) / 2 = 6 |
| kk          | 3         | ( 3 \* (3 - 1) ) / 2 = 3 |
| kkk         | 2         | ( 2 \* (2 - 1) ) / 2 = 1 |

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

- [How to solve the Sherlock and Anagrams coding challenge in JavaScript](https://www.freecodecamp.org/news/how-to-solve-the-sherlock-and-anagrams-coding-challenge-in-javascript-a80baa908637/)
