# [Sherlock and the Valid String](https://www.hackerrank.com/challenges/sherlock-and-valid-string/problem?h_l=interview&playlist_slugs%5B%5D%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D%5B%5D=strings&isFullScreen=true)

> 2020.07.23 (목요일)

## Zello

### 풀이

```js
function isValid(s) {
  const dict = new Map();
  const countDict = {};

  for (let i = 0; i < s.length; i++) {
    if (!dict.get(s[i])) {
      dict.set(s[i], 1);
    } else {
      dict.set(s[i], dict.get(s[i]) + 1);
    }
  }

  dict.forEach(function (value, key) {
    console.log(value, key);

    if (!countDict[value]) {
      countDict[value] = 1;
    } else {
      countDict[value] += 1;
    }
  });

  if (Object.keys(countDict).length > 2) return "NO";
  else if (Object.keys(countDict).length == 1) return "YES";
  else {
    if (
      Object.keys(countDict)[1] - Object.keys(countDict)[0] == 1 &&
      countDict[Object.keys(countDict)[1]] == 1
    )
      return "YES";
    else if (Object.keys(countDict)[0] == 1 && countDict[Object.keys(countDict)[0]] == 1)
      return "YES";
    else return "NO";
  }
}
```

### 설명

#### 문제 해석

> 주어진 문자열에서 최대 1개의 문자를 제거하여 포함된 문자의 갯수가 모두 동일해지도록 만드는것.

#### 코드 설명

```js
function isValid(s) {
  /*  const dict
        형식: Map (ES6) 객체 레퍼런스.
        설명: 각 알파벳이 몇번 포함되어있는지 저장하기 위한 컨테이너.
        예시: s 가 'aaaabbcc' 라면 
        -> Map { 'a' => 4, 'b' => 2, 'c' => 2 } 로 변환.
    */
  const dict = new Map();

  /*  const countDict
        형식: 객체 레퍼런스.
        설명: 각 알파벳들의 반복된 수를 저장하기 위한 컨테이너.
        예시: 'aaaabbcc' 가 변환된 Map (dict) { 'a' => 4, 'b' => 2, 'c' => 2 } 를
        -> { '2': 2, '4': 1 } 로 변환.
    */
  const countDict = {};

  /*  
        설명: s 가 'aaaabbcc' 라고 가정했을때
        Map { 'a' => 4, 'b' => 2, 'c' => 2 } 으로 변환.
    */
  for (let i = 0; i < s.length; i++) {
    if (!dict.get(s[i])) {
      dict.set(s[i], 1);
    } else {
      dict.set(s[i], dict.get(s[i]) + 1);
    }
  }

  /*  
        설명: Map (dict) 을 { 'a' => 4, 'b' => 2, 'c' => 2 } 로 가정했을때
        { '2': 2, '4': 1 } 로 변환.
    */
  dict.forEach(function (value, key) {
    console.log(value, key);

    if (!countDict[value]) {
      countDict[value] = 1;
    } else {
      countDict[value] += 1;
    }
  });

  if (Object.keys(countDict).length > 2) {
    /* 
            입력 s 가 'aaabbc' 라면 Object.keys(countDict) 가 3이 되는데,
            이때 한글자를 지우는것으로 모든 알파벳의 포함 횟수를 똑같이 되도록
            할 수 없으므로 'NO' 를 반환.
        */

    return "NO";
  } else if (Object.keys(countDict).length == 1) {
    /*
            이미 조건이 충족되어있으므로 'YES' 를 반환.
        */

    return "YES";
  } else {
    if (
      Object.keys(countDict)[1] - Object.keys(countDict)[0] == 1 &&
      countDict[Object.keys(countDict)[1]] == 1
    ) {
      /* 조건문 설명
                -> 'aaabbccdd' 가 입력되었다고 가정 할 때,
                   Object.keys(countDict)[0] 는 2 가 되고 (bb,cc,dd) Object.keys(countDict)[1] 3 이 됨 (aaa).
                   (Object.keys(countDict)[1] - Object.keys(countDict)[0]) == 1 을 만족)
                   
                   반복 횟수가 1 차이 날 때 포함 횟수가 많은것이 1개이고 거기서 하나를 빼줘 1이 된다면 (aaa 에서 a 하나 제거)
                   모든 요소의 반복 횟수가 2가 되는것을 만족함.
                   (countDict[Object.keys(countDict)[1]] == 1 을 만족)
                   
                   
                   'aabbccdddeee' 가 입력되었다고 가정 할 때,
                   Object.keys(countDict)[0] 는 2 가 되고 Object.keys(countDict)[1] 3 이 되는것은 위와 동일하지만
                   countDict[Object.keys(countDict)[1]] 이 1 이 아닌 2 가 되므로 (ddd,eee 2개),
                   총 2개의 글자 (d,e ) 를 제거해야 만족하는 문자열이 되기 때문에 최대 1개만 제거 가능하다는 제약에 어긋난다.
            */

      return "YES";
    } else if (Object.keys(countDict)[0] == 1 && countDict[Object.keys(countDict)[0]] == 1) {
      /* 조건문 설명
               ->  'aaaabbbbccccdddde' 가 입력되었다고 가정 할 때,
                   Object.keys(countDict)[0] 는 1이 되고 Object.keys(countDict)[1] 는 4가 된다.
                   
                   countDict[Object.keys(countDict)[0]] 는 1 (e) 이고 
                   countDict[Object.keys(countDict)[1]] 는 4 (aaaa,bbbb,cccc,dddd) 가 되는데,
                   이때 주어진 문제를 만족하는것은 'e' 문자를 지우면 가능해진다.
                   
                   
                   하지만 'abcdefggg' 가 입력되었다고 가정 할 때에는
                   Object.keys(countDict)[0] 는 1, Object.keys(countDict)[1] 는 3이 된다.
                   
                   countDict[Object.keys(countDict)[0]] 는 6 (a,b,c,d,e,f) 이고 
                   countDict[Object.keys(countDict)[1]] 는 1 (ggg) 이지만
                   a,b,c,d,e,f 중 하나를 지운다고 모든 알파벳의 빈도를 맞출 수 없고,
                   3개가 있는 ggg 에서 하나를 지우더라도 나머지 알파벳처럼 1개가 되지 못하여 (ggg -> gg) 
                   해당 else if 조건식을 충족하지 못한다.
               
            */
      return "YES";
    } else {
      //그 외의 경우는 'NO' 를 반환.

      return "NO";
    }
  }
}
```

#### 시간 복잡도

> O(N)

문자열 s 의 처음부터 마지막까지 순회를 하므로 **O(N)** 의 시간 복잡도를 갖는다.

#### 기타

Dictionary 의 활용

```js
const dictionary = {};

dictionary[10] = 200;
dictionary[5] = 10;

//dictionary 의 첫번째 키의 값
Object.keys(dictionary)[0]; // '5'

// dictionary 의 첫번째 키에 해당되는 값
dictionary[Object.keys(dictionary)[0]]; // 10

//dictionary 의 마지막 키의 값
Object.keys(dictionary)[Object.keys(dictionary).length - 1]; // '10'

//dictionary 의 마지막 키에 해당되는 값: 200
dictionary[Object.keys(dictionary)[Object.keys(dictionary).length - 1]]; // 200
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

### 풀이

1차

```js
function isValid(s) {
  if (s.length === 1) return "YES";
  const table = new Map();

  for (let i = 0, len = s.length; i < len; i++) {
    const frequency = table.get(s[i]);
    table.set(s[i], frequency ? frequency + 1 : 1);
  }

  const values = [...table.values()].sort();
  let changed = false;
  let same = false;
  let sameAgain = false;

  for (let i = 0, len = values.length; i < len - 1; i++) {
    const diff = Math.abs(values[i] - values[i + 1]);
    if (diff > 1) return "NO";
    if (diff === 0) {
      if (!changed) {
        same = true;
      } else {
        if (same) {
          return "NO";
        } else {
          same = true;
        }
      }
    }
    if (diff === 1) {
      if (!changed) {
        changed = true;
      } else {
        return sameAgain ? "NO" : "YES";
      }
    }
  }
  return sameAgain ? "NO" : "YES";
}
```

문자열을 이루는 각각의 문자가 몇번씩 등장하는지를 `{"a" => 3, "b" => 2, ...}` 의 형태로 Map에 맵핑해두고 다시 빈도수만 배열로 추출해서 `[3, 2, ...]` 정렬한뒤 바로 다음 요소와의 차이(`diff`)를 절대값으로 비교해가면서 답을 도출하고자 했다.

위 코드로 "aabbccddeeffg"와 같이 하나의 문자가 딱 1번 차이나는 경우는 통과했지만 그 외에 3개의 test를 통과하지 못했는데, 다음과 같은 경우여서 파악이 어려웠다.

```
"ebhcgicceggecgdcibbeicigehhebabiehbdgaeaigihghbhigihfebgabicbgfhhedgbfehiahchcecedffhccebifcbdfcfaecicafahfiecceeaabbecfhgbfifabbffadcieeaiidddhfdeccaedbgcfdehbadihheieidgcfbdiiicgahebfbbdfeffegbdhgdagefhbgafaabfghdcbfdhabhfahbdhgifbghhafcieachcbeabccbiigdcfegcccfafehegbiecbdhabcffggiifaabfagbfdfbfacdcafabccgibiidgabiabigbgbbaideeagaaffcddhieicehhchfedfgbgbfhgedhacegaieeedggacbbgadeibbbcdhbabbieibcfbhgdbbiecdhbffaghh"...
```

풀이를 학습하고 정리하기로 결정.

<br />

2차 (풀이 학습)

```js
function isValid(s) {
  let fq = {};
  s.split("").map((v) => (fq[v] ? (fq[v] += 1) : (fq[v] = 1)));

  let c = 0;
  Object.keys(fq).map((v, i, a) => (fq[v] !== fq[a[0]] ? c++ : 1));

  return c > 1 ? "NO" : "YES";
}
```

`fq`라는 객체를 생성하고 문자열을 이루는 문자들의 등장 횟수를 맵핑했다. 여기까지는 나의 풀이와 접근 방식이 같은데, 그 다음이 중요하다. `fq`객체에서 key값들을 배열에 담은 뒤 map 메서드를 사용하여 순회하면서 **첫번째 문자(첫번째 key값)를 기준으로** 문자열을 이루는 모든 문자와 등장 횟수를 비교해나고 그 차이가 같은지 다른지만 판별해서 다르면 무조건 `c`를 1을 더해주는 것이다.

이 풀이의 핵심은 기준점을 첫번째 문자로 고정했다는 점인 것 같다. 굳이 배열을 정렬할 필요도 없었고 순회하면서 기준점을 계속해서 바꿔가면서 차이가 0인지 1인지 1보다 큰지 다양한 케이스를 고려할 필요가 없었다.

이 코드를 좀 더 개선해본다면 두번째 map 메서드 대신 for문을 사용해서 `c`값이 1을 초과하면 즉시 순회를 종료하고 값을 반환해줄 수 있을 것 같다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
