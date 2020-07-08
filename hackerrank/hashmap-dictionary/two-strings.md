# [Two Strings](https://www.hackerrank.com/challenges/two-strings/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

> 2020.07.02 (목요일)

## Zello

### 풀이

```js
```

## Huey

### 풀이

```js
function twoStrings(s1, s2) {
  const ss = [...s2];
  let rs = "YES";
  [...s1].forEach((i, index) => {
    if(i.indexOf(ss[index]) === 0 ){
      return console.log(rs);
    } else {
      rs ="NO"
    }
  })
  return console.log(rs)
}
```

### 설명
스트링으로 들어온 인자를 확장 연산자를 사용하여서 배열에 담아주었다. 이 경우 단점은 중복되는 키값이 존재하여서 좋지 않은 방법인것같다.
foreach를 돌면서 2번째 인자로 들어온 스트링과 비교하면서 indexOf로 체크해주었다, 
some을 사용하면 조금더 코드가 간결하게 

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
function twoStrings(s1, s2) {
  let set = new Set();
  const _s1 = s1.split("");

  _s1.forEach((el) => set.add(el));

  for (let i = 0; i < s2.length; i++) {
    if (set.has(s2[i])) {
      return "YES";
    }
  }
  return "NO";
}
```

### 설명

1. Set 구조에 String Type의 s1을 배열화 한 후 저장함.
2. s2의 길이 만큼 for문을 순회하면서 Set에서 일치하는 값이 있다면 "YES"를 return
3. 만약에 for문을 다 순회해도 일치하는 값이 없다면 함수는 "No"를 return 한다.

위에 함수 식에서 split을 써서 배열로 만든 후 forEach를 통해서 Set에 담아 줬지만 const set = new Set( ...s1 ); 이런 식으로 spread operator를 사용하면
좀 더 간결하게 식을 표현할 수 있다는 걸 다른 팀원들의 풀이를 통해서 알았다.

## Reese

### 풀이

```js
function twoStrings(s1, s2) {
  const onlyUniqueS1 = new Set(s1);
  for (let i = 0, len = s2.length; i < len; i++) {
    if (onlyUniqueS1.has(s2[i])) {
      return "YES";
    }
  }
  return "NO";
}
```

### 설명

`onlyUniqueS1`에 s1의 유일한 문자들만을 담은 Set을 할당하고, s2 문자열을 순회하면서 `onlyUniqueS1`에 특정 문자열이 포함되어 있는지를 확인했다. 만약 하나라도 포함되어있을 경우 즉시 "YES"를 리턴하고 순회가 종료되어 일치하는 문자가 하나도 없을 경우엔 "NO"를 리턴한다.  
이 문제의 경우 자바스크립트의 `Array.prototype.some` 메소드를 쓰기에 적절한 것 같아 (휴이's 아이디어!) `some` 메소드를 써서 구현해본다면 다음과 같이 리팩토링 해볼 수 있다.

> cf) `some`은 callback이 참(불린으로 변환했을 때 true가 되는 값)을 반환하는 요소를 찾을 때까지 배열에 있는 각 요소에 대해 한 번씩 callback 함수를 실행한다.

```js
function twoStrings(s1, s2) {
  const onlyUniqueS1 = new Set(s1);
  const hasCommonString = (currLetter) => onlyUniqueS1.has(currLetter);
  return s2.split("").some(hasCommonString) ? "YES" : "NO";
}
```

<br />

## Ed

### 풀이

```js
function twoStrings(s1, s2) {
    const wordSet = new Set(s1.split(""));
    for (let i = 0; i < s2.length; i++) {
        if (wordSet.has(s2[i])) return "YES";
    }
    return "NO";
}
```

```js
function twoStrings(s1, s2) {
    const wordSet = new Set(s1);
    return [...s2].some(word => wordSet.has(word)) ? "YES" : "NO";
}
```

> 두 개의 문자열(s1, s2)가 공통되는 문자를 가지고 있는지 판별하는 문제

### 설명

- 첫번째 풀이 : 첫번째 문자열을 split해서 `wordSet`에 담는다. 이 후 두번째 문자열을 for문으로 순회하면서, `Set.prototype.has`문을 거쳐 하나라도 겹치는 문자가 있을 경우 YES, 그 외 NO를 반환한다.
- 두번째 풀이 : 문자열 하나를 Set에 넣을 경우 알아서 split해서 들어간다고 한다! for문 대신 `Array.prototype.some`을 사용해서, for문을 훨씬 간결하고 선언적으로 나타냈다. some은 배열의 메서드이기 때문에, 문자열(s2)을 배열로 변경해야 한다. `split` 대신 spread 연산자를 사용해서 배열로 변경해봤다.

---

## 참고자료
