# [Hash Tables: Ransom Note](https://www.hackerrank.com/challenges/ctci-ransom-note/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

> 2020.07.02 (목요일)

## Zello

### 풀이

```js
function checkMagazine(magazine, note) {
    const dictionary = {};

    for ( let i = 0 ; i < magazine.length ; ++i ) {
        if ( !dictionary[magazine[i]] ) dictionary[magazine[i]] = 1;
        else dictionary[magazine[i]] += 1;
    }

    for ( let i = 0 ; i < note.length ; ++i ) {
        const word = note[i];

        if ( dictionary[word] > 1 ) {
            dictionary[word] -= 1;
        }
        else if ( dictionary[word] == 1 ) {
            dictionary[word] = undefined;
        }
        else {
            console.log("No");
            return;
        }
    }

    console.log("Yes");
    return;
}
```

### 설명

#### 문제 해석
> note 의 단어들이 전부 magazine 에 포함되는지 확인하는 문제.

#### 코드 설명
- 첫번째 for 문에서는 magazine 의 단어 출연 횟수를 dictionary 에 저장한다.
  - ex. ['give', 'me', 'one', 'grand', 'today', 'night'] -> { give: 1, me: 1, one: 1, grand: 1, today: 1, night: 1 }
- 두번째 for 문에서는 note 의 각 단어에 대해 dictionary 를 검사한다.
  - dictionary 에서 note 의 i 번째 인덱스에 해당하는 단어를 2개 이상 갖고 있다면 dictionary 에서 해당 문자열 카운트를 1 차감
  - dictionary 에서 note 의 i 번째 인덱스에 해당하는 단어를 1개 갖고 있다면 dictionary 의 해당 문자열에 대한 정보를 undefined 로 처리
  - dictionary 에서 note 의 i 번째 인덱스에 해당하는 단어를 갖고 있지 않다면 콘솔에 'No' 출력 후 종료
- 두번째 for 문에서 else 분기가 처리되지 않았다는것은 magazine 이 note 의 단어를 전부 포함하고 있다는 뜻이므로 'Yes' 출력 후 종료 


## Huey

### 풀이

```js
function checkMagazine(magazine, note) {
   const fs = magazine.split(" ")
   const ss = note.split(" ")
   console.log(fs, ss)
   let result = "yes"
   for(let i = 0; ss.length > i; i++) {
     index = fs.indexOf(ss[i])
     console.log(index)
     if(index === -1) {
       result = "no"
       break
     } else {
       result = "yes"
     }
   }
   return console.log(result);
 }
```
### 설명
한글자씩 잘라서 배열로 넣은다음에 반목문을 돌면서 indexOf로 단어가 포함되어있는지 확인하면서 있다면 바로 리턴을 해주도록 하였다.
배열로 넣을필요가 없었는데 해당 사이트에서 풀지 않고 js파일을 만들어서 불필요한 코드가 추가되었다.

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
function checkMagazine(magazine, note) {
  const memo = {};

  magazine.forEach((el) => {
    !memo[el] ? (memo[el] = 1) : (memo[el] = memo[el] + 1);
  });

  for (let i = 0; i < note.length; i++) {
    if (!memo[note[i]]) return console.log("No");
    else memo[note[i]] = memo[note[i]] - 1;
  }
  return console.log("Yes");
}
```

### 설명

1. memo 객체를 선언한 후 magazine.forEach를 통해서 값이 없다면 1을 할당해 주고 값이 있다면 해당 값에 count를 1 더해서 반복문을 순회한다.
2. for문을 통해서 만약에 memo[note[i]] 값이 false라면 NO를 return하고 true라면 객체에서 해당 key값에 count를 -1 해준다.
3. 반복문을 모두 통과한다면 note의 배열의 구성은 magazine에 전부 포함되 있다는 가정을 할 수 있으며 Yes를 return 한다.

## Reese

### 풀이

1.

```js
function checkMagazine(magazine, note) {
  const wordMapOfMagazine = new Map();
  magazine.forEach((word) =>
    wordMapOfMagazine.has(word)
      ? wordMapOfMagazine.set(word, wordMapOfMagazine.get(word) + 1)
      : wordMapOfMagazine.set(word, 1)
  );

  for (let i = 0, len = note.length; i < len; i++) {
    if (wordMapOfMagazine.has(note[i])) {
      if (wordMapOfMagazine.get(note[i]) === 0) return console.log("No");
      wordMapOfMagazine.set(note[i], wordMapOfMagazine.get(note[i]) - 1);
    } else {
      return console.log("No");
    }
  }

  return console.log("Yes");
}
```

### 설명

magazine에 들어있는 string들의 갯수를 임의의 Map `wordMapOfMagazine`에 맵핑한 후, note 배열을 순회하면서 (1) `wordMapOfMagazine`에 해당하는 string이 키값이 존재하는지를 확인하고, (2) 키값이 존재할 경우 그 갯수를 1 차감해서 0인지 아닌지를 판별했다.  
string 키값이 존재하지 않거나 string의 갯수가 0일 경우 경우 "No"를 early return 해주고, early return 없이 note 배열 순회를 완료했을 경우 magazine에 들어있는 string을 사용해서 note 내용을 전부 만들 수 있다는 의미이기 때문에 "Yes"를 return한다.

<br />

## Ed

### 풀이

```js
function checkMagazine(magazine, note) {
    let answer = "Yes";

    const magazineMap = new Map();
    magazine.forEach(word => {
        const wordValue = magazineMap.get(word);
        magazineMap.set(word, wordValue ? wordValue + 1 : 1);
    });

    for(let i = 0; i < note.length; i++) {
        const wordValue = magazineMap.get(note[i]);
        if (wordValue) magazineMap.set(note[i], wordValue - 1);
        else {
            answer = "No";
            break;
        }
    };

    console.log(answer);
}
```

> magazine에 있는 문자들로 note의 문자를 구성할 수 있는지 판별하는 문제. magazine의 문자는 갯수만큼만 사용할 수 있다.

### 설명

1. 빈 Map `magazineMap`을 만든다.
2. magazine을 forEach문으로 순회하며, magazineMap의 `get` 메서드로 해당 단어가 저장돼있는지 아닌지 확인한다.
3. 없을 경우 해당 value를 1로 새로 `set`하고, 있을 경우 value를 기존 값에서 1 증가시킨다.
4. note 배열을 순회하며, 인덱스에 해당하는 문자(`note[i]`)를 magazineMap에서 get 메서드를 통해 찾은 후 `wordValue`에 저장한다.
5. wordValue가 존재할 경우 해당 문자의 value를 1 감소시킨다.
6. 애초에 `note[i]`에 해당하는 wordValue 자체가 없거나, 혹은 wordValue의 값이 0인 경우 `No`를 리턴한다. `No`가 아닐경우 `Yes`를 리턴한다.

---

## 참고자료
