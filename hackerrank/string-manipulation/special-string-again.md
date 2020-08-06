# [Special String Again](https://www.hackerrank.com/challenges/special-palindrome-again/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)

> 2020.07.30 (목요일)

## Sally

### 풀이

```js
```

### 설명

## Zello

### 풀이

```js
```

### 설명

## Huey

### 풀이

```js
```

### 설명

## Hoo

### 풀이

```js
function substrCount(n, s) {
  let count = 0;
  let consecutiveLetters = "";

  for (let i = 0; i < n; ++i) {
    if (!consecutiveLetters || consecutiveLetters[0] === s[i]) {
      // 1
      consecutiveLetters += s[i];
    } else {
      let j = 1;
      while (j <= consecutiveLetters.length && s[i + j] === consecutiveLetters[0]) {
        // 2
        ++j;
        ++count;
      }
      consecutiveLetters = s[i];
    }

    count += consecutiveLetters.length;
  }

  return count;
}
```

### 설명

> 문자열에서 대칭되는 문자열 개수를 찾는 문제

- `time limit`으로 계속 풀지 못해 솔루션을 보고 이해하는 방식을 택했다.

1. 문자열을 반복문을 돌면서 나타나는 빈도수가 `consecutiveLetters`에 저장된다.
   - `consecutiveLetters`는 index가 0일 때이거나 연속 문자가 등장할 경우 추가시면서 저장한다.
2. consecutiveLetters를 기준으로 `s[i + j]` 값을 비교하며 조건에 만족하면 count가 1씩 추가되게 한다.
   - 여기서 **aaaa**와 같이 같은 문자열이 반복되면 `else문`에 들어오지 않아서 while문에 들어오지 않고 length를 저장해 개수를 구하게 된다.
3. while문이 끝나게 되면 `현재의 문자 값`으로 consecutiveLetters를 변경한다.
4. 현재의 길이를 count에 저장함으로써 `하나의 문자의 개수`와 `반복 문자열의 개수`를 저장하게 된다.
5. 반복문이 끝나고 나오게 되는 `count` 값을 반환한다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

string이 아래의 두 경우 중 하나일 경우 special string이라고 한다.

1. 모든 문자가 같은 경우 (e.g. "aaa")
2. 가운데에 위치한 문자를 제외한 나머지가 같을 경우 (e.g. "aadaa")

문자열 하나를 인자로 받고 그 안에서 **special string에 해당하는 substring의 갯수**가 몇 개인지 반환하는 문제이다.

### 풀이

```js
function updateMap(map, key) {
  const value = map.get(key);
  map.set(key, value ? value + 1 : 1);
}

function substrCount(n, s) {
  const subStr = new Map();
  for (let i = 0; i < n; i++) {
    updateMap(subStr, s[i]);
    for (let j = i + 1; j < n; j++) {
      updateMap(subStr, s.slice(i, j + 1));
    }
  }

  let result = 0;
  for (const [key, value] of subStr) {
    const length = key.length;
    if (length === 1) {
      result += value;
      continue;
    }

    const unique = new Set(key);
    if (unique.size === 1) {
      result += value;
      continue;
    }

    if (length % 2 && unique.size === 2) {
      const mid = Math.floor(length / 2);
      if (key[0] === key[mid + 1] && key[mid] !== key[mid + 1]) {
        result += value;
      }
    }
  }

  return result;
}
```

문자열을 순회하면서 문자열에서 나올 수 있는 모든 substring을 구한 후 Map에 그 빈도수를 맵핑했다.

> 예를 들어 "aaaa"의 모든 substring을 구하고 그 빈도수를 맵핑하면 다음과 같다.
>
> ```js
> Map { 'a' => 4, 'aa' => 3, 'aaa' => 2, 'aaaa' => 1 }
> ```

이렇게 만들어진 Map을 순회하면서 key값(substring)의 길이를 기준으로

- 길이가 1인 경우 무조건 special string이기 때문에 value(빈도수)를 `result`에 더해주고,
- 길이가 1이 아닌 경우 special string인 2가지 경우를 각각 분기처리하여 조건을 충족할 경우 value를 `result`에 더해주었다.
  1. substring이 하나의 문자로 이루어진 경우(= Set의 길이가 1)
  2. 길이가 홀수이면서 2가지 종류의 문자로 이루어져있으며(= Set의 길이가 2) 가운데 문자만 다른 경우

위 코드를 제출해보니 시간초과로 인해 대부분의 테스트를 통과하지 못했다.

<br />

풀이 학습

```js
function substrCount(n, s) {
  let counter = 0;

  for (let i = 0; i < n; i++) {
    counter++; // substring의 길이가 1인 경우 무조건 +1
    for (let j = i + 1; j < n; j++) {
      if (s[i] !== s[j]) {
        if (s.slice(i, j) === s.slice(j + 1, 2 * j - i + 1)) {
          counter++; // 가운데 문자(s[j])를 기준으로 양 옆이 같을 경우 +1
        }
        break;
      } else {
        counter++; // 같은 문자일 경우 +1
      }
    }
  }

  return counter;
}
```

이중 for문을 돌면서 substring의 조합을 구하면서 다음과 같이 special string의 조건을 충족하는 3가지 경우에 한해 `counter`를 1씩 더해준다.

- substring의 길이가 1인 경우 - e.g. `a`
- `s[i] !== s[j]`일때 가운데 문자 `s[j]`를 기준으로 양 옆이 같을 경우 - e.g. `aabaa`
- `s[i] === s[j]`인 경우 - e.g. `aaa`

순회를 하다가 다른 문자가 나왔을 때에만 양 옆을 비교해서 special string 여부를 판별하고 그 외에는 계속해서 `counter`를 1씩 더해준다.

`break` 문을 사용해야 `counter`를 중복해서 더하지 않을 수 있다.

<br />

## Ed

### 풀이

```js
function substrCount(n, s) {
  let count = n;
  for (let i = 0; i < s.length; i++) {
    let sameCount = 1;
    for (let j = i + 1; j < s.length; j++) {
      if (s[i] !== s[j]) {
        const left = s.substring(i, j);
        const right = s.substring(j + 1, j + 1 + sameCount);
        if (left === right) count++;
        break;
      }
      sameCount++;
      count++;
    }
  }
  return count;
}
```

### 설명

> 부분 문자열 중, 1. 모든 문자가 같거나 `예) aaaaa` 2. 가운데 문자만 다른 경우 `예) aaabaaa`의 합을 구하는 문제.

이 문제에서 핵심은 `2. 가운데 문자만 다른 경우`라고 생각한다.

1. 우선 문자열의 길이만큼 정답이 될 `count`에 우선 더해준다. 개별 알파벳들은 모두 `1.모든 문자가 같은 경우`에 속하기 때문이다.
2. 첫번째 인덱스인 `s[0]` 부터 이중 반복문으로 모든 부분 문자열을 찾아나간다. 개별 알파벳들의 경우의 수는 1번에서 모두 더했으므로 이중반복은 다음에 오는 알파벳인 `i + 1` 부터 시작한다.
3. 여기서 `sameCount`라는 변수를 사용했는데, `2. 가운데 문자만 다른 경우`를 판별하기 위해서이다. 예를 들어 설명해보자면,

```js
            aaaabaaaa
index:      012345678
sameCount:  1234

1. 우선 0번째 문자부터 순회를 시작한다. sameCount는 1로 시작한다.
2. 반복을 시작한 문자 s[i] 와 다음 문자 s[j] 가 같다면, 전체 경우의 수인 count와 sameCount 모두 1씩 증가시킨다.
3. 순회를 하다 j = 4번 인덱스에 이르게 되면, 반복을 시작한 문자 s[i] "a"와 다른 문자 s[j] "b"를 발견했을 때, 이 부분문자열이 경우의 수에 포함될 경우는 "이 b가 전체 문자열의 가운데에 있을 경우" 밖에 없다.
4. sameCount = 4 라는 값을 가지고 있으므로, 기존 시작점부터 현재 인덱스까지 (0 ~ 3)가 "왼쪽" 문자열이 되고, "4" 가 중앙, 왼쪽 문자열의 수만큼 중앙 이후의 문자들 (5 ~ 8)이 "오른쪽" 문자열이 된다.
5. 왼쪽과 오른쪽 문자열이 같을 경우, 전체 경우의 수를 1 증가시킨다.
6. 같거나 틀리거나, 이미 중앙에 한가지만 다른 경우의 수가 나왔으므로, 이 이후 더 이상 경우의 수는 존재하지 않는다. 순회를 종료한다.
```

4. 다음은 3번에서 설명한 부분을 코드로 풀어쓴 것과 동일하다.
5. `s[i] === s[j]` 의 경우, `1. 모든 문자가 같은 경우` 에 속하므로 `count`와 `sameCount` 둘 다 1씩 증가시킨다.
6. 다른 경우, `substring` 메서드를 사용해 왼쪽과 오른쪽의 부분 문자열을 추출하고 비교한다. 같을 경우 `count`를 1 증가시킨다.
7. 같거나 다르거나, 더 이상 순회를 도는 의미가 없으므로 반복을 종료하고 다음 `i`로 넘어간다.

---

## 참고자료

- [string manipulation 문제 푸는 짧은 팁](https://ally10.tistory.com/6)
