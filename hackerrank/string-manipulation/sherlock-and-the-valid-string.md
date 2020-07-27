# [Sherlock and the Valid String](https://www.hackerrank.com/challenges/sherlock-and-valid-string/problem?h_l=interview&playlist_slugs%5B%5D%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D%5B%5D=strings&isFullScreen=true)

> 2020.07.23 (목요일)

## Zello

### 풀이

```js
function isValid(s) {
    const dict = new Map();
    const countDict = {};

    for ( let i = 0 ; i < s.length ; i++ ) {
        if ( !dict.get(s[i])) {
            dict.set(s[i], 1);
        }
        else {
            dict.set(s[i], dict.get(s[i]) + 1);    
        }
    }

    dict.forEach(function(value, key) {
        console.log(value, key);

        if ( !countDict[value] ) {
            countDict[value] = 1;
        }
        else {
            countDict[value] += 1;
        }
    });

    if ( Object.keys(countDict).length > 2) return "NO";
    else if ( Object.keys(countDict).length == 1) return "YES";
    else {
        if ( Object.keys(countDict)[1] - Object.keys(countDict)[0] == 1 && countDict[Object.keys(countDict)[1]] == 1 ) return "YES";
        else if ( Object.keys(countDict)[0] == 1 && countDict[Object.keys(countDict)[0]] == 1 ) return "YES";
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
    for ( let i = 0 ; i < s.length ; i++ ) {
        if ( !dict.get(s[i])) {
            dict.set(s[i], 1);
        }
        else {
            dict.set(s[i], dict.get(s[i]) + 1);    
        }
    }

    /*  
        설명: Map (dict) 을 { 'a' => 4, 'b' => 2, 'c' => 2 } 로 가정했을때
        { '2': 2, '4': 1 } 로 변환.
    */
    dict.forEach(function(value, key) {
        console.log(value, key);

        if ( !countDict[value] ) {
            countDict[value] = 1;
        }
        else {
            countDict[value] += 1;
        }
    });

    if ( Object.keys(countDict).length > 2) {
        /* 
            입력 s 가 'aaabbc' 라면 Object.keys(countDict) 가 3이 되는데,
            이때 한글자를 지우는것으로 모든 알파벳의 포함 횟수를 똑같이 되도록
            할 수 없으므로 'NO' 를 반환.
        */
        
        return "NO";
    }
    else if ( Object.keys(countDict).length == 1) {
        /*
            이미 조건이 충족되어있으므로 'YES' 를 반환.
        */
    
        return "YES";
    }
    else {
        if ( Object.keys(countDict)[1] - Object.keys(countDict)[0] == 1 && 
             countDict[Object.keys(countDict)[1]] == 1 ) {
              
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
        }
        else if ( Object.keys(countDict)[0] == 1 && countDict[Object.keys(countDict)[0]] == 1 ) {
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
        }
        else {
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