# [Count Triplets](https://www.hackerrank.com/challenges/count-triplets-1/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=dictionaries-hashmaps)

> 2020.07.09 (목)

## Zello

### 풀이

```js
function countTriplets(arr, r) {
    let answer = 0;
    const countDictionary = {};

    for ( let i = 0 ; i < arr.length ; ++i ) {
        if ( !countDictionary[arr[i]] ) countDictionary[arr[i]] = 1;
        else countDictionary[arr[i]] += 1;
    }

    const currentDictionary = {};
    currentDictionary[arr[0]] = 1;
    
    const coefficient = r == 1 ? 1 : 0;

    for ( let i = 1 ; i < arr.length - 1 ; ++i ) {
        if ( Number.isInteger(arr[i] / r) && currentDictionary[arr[i] / r] ) {
            if ( !currentDictionary[arr[i] * r] && countDictionary[arr[i] * r] ) {
                answer += currentDictionary[arr[i] / r] * 
                          (countDictionary[arr[i] * r] - coefficient);
            }
            else if ( currentDictionary[arr[i] * r] && countDictionary[arr[i] * r] ) {
                answer += currentDictionary[arr[i] / r] * 
                          (countDictionary[arr[i] * r] - currentDictionary[arr[i] * r] - coefficient);
            }
        }

        if ( !currentDictionary[arr[i]] ) currentDictionary[arr[i]] = 1;
        else currentDictionary[arr[i]] += 1;
    }

    return answer;
}
```

### 설명


## Huey

### 풀이

```js
```

## Hoo

### 풀이

```js
function countTriplets(arr, r) {
  let m2 = new Map();
  let m3 = new Map();
  let total = 0;

  arr.forEach((val) => {
    if (m3.has(val)) total += m3.get(val);
    if (m2.has(val)) m3.set(val * r, m3.get(val) ? m3.get(val) + m2.get(val) : m2.get(val));
    m2.set(val, m2.get(val * r) ? m2.get(val * r) + 1 : 1);
  });

  return total;
}
```

### 설명

> 배열 안에서 연속해서 등장하는 r의 n제곱 3개의 숫자가 몇 쌍이 되는지 구하는 문제

- 문제 접근하기가 어려워서 파이썬으로 간단하게 푸신 분의 풀이를 참고했다.
- 풀이 설명은 아래 블로그를 참고하면 되고, 나는 그 풀이를 어떻게 이해했는지 작성해 보겠다.

아래는 `arr: 1 2 2 4, r: 2`일 때 풀이의 Map 변화 상황이다.

```plain
m2:  Map { 2 => 1 }                 m3:  Map {} // 0
m2:  Map { 2 => 1, 4 => 1 }         m3:  Map { 4 => 1 } // 1
m2:  Map { 2 => 1, 4 => 2 }         m3:  Map { 4 => 2 } // 3
m2:  Map { 2 => 1, 4 => 2, 8 => 1 } m3:  Map { 4 => 2, 8 => 2 } //4
```

1. 먼저 3개의 쌍 중 첫번째 값에 의해 m2에 값이 들어간다.
2. m2에 값이 생기게 되면서 m3에도 그에 의해 값이 들어간다.
3. m3에 있는 값이 total에 누적된다.

- m2와 m2 값을 보면 기존 배열에 있지 않은 8이 있는 것을 볼 수 있다. 이는 개수를 세기 위함이고, 실제로는 2를 나눠서 보면 원래의 개수가 나오게 된다.
- 설명을 보면 대충 이해가 가는데 이렇게 여러 Map을 사용해야 하는 문제는 접근방식이 잘 생각나지 않아 고민을 많이 해야겠다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제이해

정수로 이루어진 임의의 배열 하나(`arr`)와 정수 하나(`r`)가 주어졌을 때, 길이가 3인 부분집합 배열(triplet)의 갯수를 구하는 문제다.  
이 triplet은 길이가 3인 배열인데 첫번째 요소를 제외하고 나머지 두 요소는 각각 이전 요소에 `r`을 곱해서 나오는 값으로 이루어져 있다.  
triplet을 이루는 요소들의 인덱스는 차례대로 `i`, `j`, `k`로 표현할 수 있으며 `i < j < k` 조건을 만족한다.  
`arr = [1, 4, 16, 64]`이고 `r = 4`일 경우 나올 수 있는 triplet의 갯수는 `[1, 4, 16]`와 `[4, 16, 64]` 2개 이다.

#### 조건

- `i` < `j` < `k`
- 1 <= arr의 길이 <= 10^5
- 1 <= `r` <= 10^9
- 1 <= `arr[i]` <= 10^9

### 풀이

**1차**

```js
function countTriplets(arr, r) {
  const nums = new Map();
  arr.forEach((num) => (nums.has(num) ? nums.set(num, nums.get(num) + 1) : nums.set(num, 1)));

  let numOfTriplets = 0;
  let posI, posJ, posK;
  for (const [key, value] of nums) {
    if (value > 1) {
      posI = nums.has(key * r) && nums.has(key * Math.pow(r, 2)) ? 1 : 0;
      posJ = nums.has(key / r) && nums.has(key * r) ? 1 : 0;
      posK = nums.has(key / r) && nums.has(key / Math.pow(r, 2)) ? 1 : 0;
      numOfTriplets += (posI + posJ + posK) * value;
    }
  }

  return numOfTriplets;
}
```

### 설명

접근 방식은 이렇다. 배열에 들어있는 숫자들이 각각 몇 번씩 등장하는지 그 갯수를 맵핑한 후, 해당 맵을 순회하면서 각각의 숫자가 triplet의 일부가 될 수 있는지 확인하는 것이다.

triplet은 `[i, j, k]`로 구성되어 있으며 이때 `i`를 제외한 나머지가 바로 앞 요소에 `r`을 곱한 값이라는 규칙을 활용한다.  
해당 값이 `i`의 위치에 올 수 있는지는 posI의 값으로 판별하고, `j`의 위치에 올 수 있는지는 posJ의 값으로 판별하고, 'k'의 위치에 올 수 있는지는 posK의 값으로 판별한다.  
`i`, `j`, `k` 각각의 위치에 올 수 있으면 1, 없으면 0을 반환해서 이들을 더한 값에 value(해당 값이 등장한 횟수)를 곱해주면 triplet의 갯수를 구할 수 있다.

이 풀이의 경우 코드를 제출했을 때 13개 중 5개의 case를 통과하지 못했다.  
그 중 하나의 케이스를 확인해보니 다음과 같은 경우였다.

![failed test case](https://i.postimg.cc/0Qfsr5NC/2020-07-09-21-28-18.png)

문제에 주어진 예시들이 전부 오름차순으로 정렬되어 있어서 당연히 모든 케이스가 그럴거라고 생각했는데, 그게 아니었다ㅎ  
그러고보니 문제 어디에서도 오름차순으로 정렬되어 있다는 말은 없었다.  
_`i < j < k` 조건의 경우 `i`, `j`, `k` 각각이 triplet을 이루는 '값'이 아니라 '인덱스'를 의미하는 거였고, triplet에 대한 조건이지 `arr`에 대한 조건이 아니었다._

<br />

### 풀이

**2차 ([풀이](https://www.youtube.com/watch?v=tBFZMaWP0W8) 학습)**

```js
function countTriplets(arr, r) {
  const left = new Map();
  const right = new Map();

  arr.forEach((num) => right.set(num, right.has(num) ? right.get(num) + 1 : 1));

  let count = 0;
  arr.forEach((num) => {
    let c1 = 0,
      c3 = 0;
    right.set(num, right.get(num) - 1);
    if (left.has(num / r) && num % r === 0) {
      c1 = left.get(num / r);
    }
    if (right.has(num * r)) {
      c3 = right.get(num * r);
    }
    count += c1 * c3;
    left.set(num, left.has(num) ? left.get(num) + 1 : 1);
  });

  return count;
}
```

### 설명

**Points**

1. triplet을 구성하는 숫자들을 a, ar, ar^2이 아니라 a/r, a, ar로 놓고 문제를 푼다. 즉, a를 triplet의 가운데 값으로 두는 것이다.

   ```
   a  ar  ar^2  ->  a/r  a  ar
   ```

   a, ar, ar^2로 두고 풀때는 ar의 인덱스(`j`)가 ar^2의 인덱스(`k`)보다 작은지를 판별해야 하는데,  
   a를 가운데 값 즉, 인덱스 `j`를 가지를 값으로 두게 되면 이러한 판별 과정이 필요 없어진다.  
   a/r의 인덱스(`i`)는 무조건 a의 인덱스 `j`보다 작고, ar의 인덱스 `k`는 `j`보다 크다는 것을 보장할 수 있다.

2. `a`를 기준으로 왼쪽에 등장하는 숫자들의 frequency는 `left`라는 Map에 저장하고, 오른쪽에 위치한 숫자들의 frequency는 `right`라는 Map에 저장한다.  
   이렇게 되면 `left`에 있는 숫자들의 인덱스(`i`)는 반드시 `a`의 인덱스(`j`)보다 작고, `right`에 있는 숫자들의 인덱스(`k`)는 반드시 `j`보다 크기 때문에 `i < j < k`라는 조건을 충족하는지 확인하기 위한 별도의 로직이 필요하지 않게 된다. (1번에서 얻을 수 있는 효과와 같은 맥락이다.)

위의 2가지 포인트를 가지고 다음과 같이 처리해준다.

- 일단 arr를 순회하면서 등장하는 모든 숫자의 frequency를 `right` Map에 맵핑해둔다.
- 다시 한 번 arr를 순회하면서 `left` Map에 a/r이 있는지 확인하고 `right` Map에 ar이 있는지 확인하면서 있을 경우 각각의 frequency를 곱해서 나올 수 있는 triplet의 가짓수를 구하고 count에 업데이트 해준다.

<br />

---

<br />

아래는 loop 1회로 끝나는 풀이 이다.  
이해가 잘 안가서 나중에 다시 공부해봐야 할 듯..!

```js
function countTriplets(arr, r) {
  const left = new Map();
  const right = new Map();

  let count = 0;

  arr.forEach((num) => {
    if (right.get(num)) {
      count = count + right.get(num);
    }
    if (left.get(num)) {
      right.set(num * r, right.get(num * r) ? right.get(num * r) + left.get(num) : left.get(num));
    }
    left.set(num * r, left.get(num * r) ? left.get(num * r) + 1 : 1);
  });
  return count;
}
```

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료

- https://monthlywoongah.tistory.com/80
