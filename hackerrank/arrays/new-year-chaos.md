# [New Year Chaos](https://www.hackerrank.com/challenges/new-year-chaos/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays)

> 2020.06.20 (토)

## Hoo

### 풀이

```js
function minimumBribes(q) {
  let counter = 0;

  for (let i = q.length - 1; i >= 0; i--) {
    if (q[i] - (i + 1) >= 3) return "Too chaotic";

    for (let j = Math.max(0, q[i] - 2); j < i; j++) if (q[j] > q[i]) counter++;
  }

  return counter;
}
```

### 설명

> 놀이기구를 기다리는 줄에서 뇌물이 최소 몇 번 오갔는지 구하는 문제. \
> (단, 한 사람이 뇌물을 3번 이상 준 경우는 Too chaotic을 결과로 해야 한다.)

- 문제 이해가 어려워 솔루션을 찾아보고 이해하는 방식을 택했다.
- 입력값은 뇌물로 인해 순서가 뒤섞인 배열이고, 출력값은 숫자 또는 문자열이다.

1. 우선 뇌물을 주고받았는지를 찾기 위해 `q`의 길이만큼 반복문을 돈다.
2. 한 사람이 뇌물을 3번 이상 줬다면 자신의 원래 위치보다 3 이상 앞에 있을 것이다.
   - 이것을 바탕으로 `q[i]`는 현재 위치, `i + 1`은 원래 위치로 두고 3 이상이면 `Too chaotic`을 반환하도록 한다.
3. 카오식하지 않다면 현재 위치보다 `1 또는 2 작은 위치`에서 뇌물을 주고받은 사람이 있는지 확인한다.
   - 현재 위치의 수보다 크다면 뇌물을 주고받은 것이다.
4. 뇌물을 주고받은 사람이 있으면 `counter`를 1씩 증가시켜 준다.
5. 최종 결과값인 `counter`를 반환한다.

- 솔루션을 보면서 이해해 보니 그렇게까지 어려운 문제는 아니었다. 문제가 길어도 진득하게 읽고 풀려고 해야겠다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제이해

`규칙 : '바로 앞 사람'에게 뇌물을 주고 자리를 swap할 수 있다. 단, 한 사람당 최대 2명까지 가능하다.`<br />
위와 같은 규칙을 가지고 무작위로 서있는 사람들을 초기상태(오름차순) 정렬하기 위해 최소한 몇 번의 swap이 필요한지 구하는 문제이다.

### 풀이 1 (fail)

```js
function minimumBribes(q) {
  const finalPosition = new Map();

  q.forEach((person, position) => finalPosition.set(person, position + 1));

  let numOfBribes = 0;
  for (let [person, position] of finalPosition) {
    if (person <= position) continue;

    const diff = person - position;
    if (diff > 2) {
      return "Too chaotic";
    } else {
      numOfBribes += diff;
    }
  }

  return numOfBribes;
}
```

### 설명

1. `finalPosition`이라는 Map을 생성한 후, 인자로 받은 배열을 순회하면서 swap하기 전 초기 상태의 위치를 맵핑했다.
2. `finalPosition`을 순회하면서 특정 사람의 위치(`position`)가 오름차순으로 정렬됐을때 자신의 위치(`person`)보다 앞일 경우, 그 차이가 2를 초과하는지 여부를 체크했다.
   > 최대 2명까지만 swap이 가능하기 때문.

이 풀이는 `[1, 2, 5, 3, 7, 8, 6, 4]` 인자가 주어졌을 때 크롬 개발자 도구에서는 정답인 `6`이 잘 반환됐는데 HackerRank 플랫폼에서는 7이 출력되면서 테스트 fail이 떴다. 이유를 못찾아서 일단 다른 풀이로 재시도.

<br />

### 풀이 2 (fail)

```js
function minimumBribes(q) {
  for (let i = 0, len = q.length; i < len; i++) {
    // O(n)
    if (q[i] - (i + 1) > 2) {
      return console.log("Too chaotic");
    }
  }

  let numOfBribes = 0;
  for (let j = 0, length = q.length; j < length; j++) {
    // O(n^2)
    for (let k = 0; k <= j; k++) {
      if (q[k] > q[j]) {
        const temp = q[j];
        q[j] = q[k];
        q[k] = temp;
        numOfBribes++;
      }
    }
  }
  console.log(numOfBribes);
}
```

### 설명

- 최초 1회 순회를 하면서 초기위치와 현재위치 사이의 갭이 2를 초과할 경우 "Too chaotic"을 early return 해준다.
- 이후 2번째로 순회를 하면서 bubble sort를 구현과 동시에 swap된 횟수(= 뇌물을 준 횟수이므로 `numOfBribes`로 표기)를 업데이트 해준 후 최종적으로 `numOfBribes`를 반환한다.

시간초과로 일부 테스트 케이스에서 fail이 떴다.  
loop를 2번 도는 것 + 좋지 않은 성능을 가진 bubble sort의 영향이 컸던 것 같다.

<br />

### 풀이 3 (success, 풀이 학습)

```js
function minimumBribes(q) {
  const TOO_CHAOTIC = "Too chaotic";
  let numOfBribes = 0;

  for (let current_pos = 0; current_pos < q.length; current_pos++) {
    // O(n)
    const original_pos = q[current_pos] - 1;
    const diff = original_pos - current_pos;
    if (diff > 2) return console.log(TOO_CHAOTIC);

    for (let i = Math.max(0, original_pos - 1); i < current_pos; i++) {
      // O(logn)
      const start_pos_of_forward_person = q[i] - 1;
      if (start_pos_of_forward_person > original_pos) {
        numOfBribes++;
      }
    }
  }
  console.log(numOfBribes); // Time Complexity = O(n) * O(logn) = O(nlogn)
}
```

### 설명

초기위치와 현재위치를 비교해서 갭이 2를 초과할 경우 early return을 해주는 것 까지는 동일한데, 중요한건 그 외의 경우(`diff <= 0`)를 핸들링하는 부분이다.  
즉, 최종적으로 **본인의 위치를 그대로 유지하더라도 뇌물을 받은 경우**가 있기 때문에 이 경우를 처리해주는 것이다.

예를들면,

```
1 2 3 4 5 --- 4번이 뇌물을 주고 앞으로 1칸 이동 (3번은 뇌물을 1번 받은 상태)
　　　↓
1 2 4 3 5 --- 4번이 한 번 더 뇌물을 주고 앞으로 1칸 이동 (2번도 뇌물을 1번 받은 상태)
　　　↓
1 4 2 3 5 --- 3번이 뇌물을 주고 앞으로 1칸 이동 (2번은 뇌물을 2번 받은 상태)
　　　↓
1 4 3 2 5 --- 최종적으로 3번은 원래 자기 위치에 그대로 있지만 뇌물을 1번 받은 상태!
```

위와 같은 경우 때문에 **뇌물을 받은 사람 기준(3)으로** 자기 앞에 자신보다 큰 숫자의 사람(4)이 있을 경우 3번 자신은 위치가 그대로더라도 뇌물을 1번 받은 것과 동일하다. 따라서 `numOfBribes`를 1 더해줘야 한다.  
이때는 loop를 도는 시작점은 index 0이 아닌, 뇌물을 받은 사람 기준으로 바로 앞에 있는 사람부터(`original_pos - 1`) 고려하면 된다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
