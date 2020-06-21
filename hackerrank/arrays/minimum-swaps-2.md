# [Minimum Swaps 2](https://www.hackerrank.com/challenges/minimum-swaps-2/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays)

> 2020.06.20 (토)

## Hoo

### 실패한 풀이 1

```js
function swaploop(arr, result) {
  if (arr === Array.from(Array(arr.length), (_, i) => i + 1)) return result;

  for (let i = 0; i < arr.length - 1; i++) {
    const originNum = i + 1;
    const swapNum = arr[i];

    const isSwap = () => originNum !== swapNum;
    const findIndex = () => arr.indexOf(originNum);
    const swapNums = (a, b) => {
      const temp = arr[a];
      arr[a] = arr[b];
      arr[b] = temp;
    };

    if (isSwap()) {
      swapNums(i, findIndex());
      result++;
    }
  }
  return swaploop(arr, result);
}

function minimumSwaps(arr) {
  let result = 0;

  return swaploop(arr, result);
}
```

### 실패한 풀이 2

```js
function minimumSwaps(arr) {
  let result = 0;

  for (let i = 0; i < arr.length; i++) {
    const originNum = i + 1;
    const currnetNum = arr[i];

    const isSwap = () => originNum !== currnetNum;

    const findIndex = () => arr.indexOf(originNum);

    const swapNums = (a, b) => {
      const temp = arr[a];
      arr[a] = arr[b];
      arr[b] = temp;
    };

    if (isSwap()) {
      swapNums(i, findIndex());
      result++;
      console.log(arr, result);
    }
  }

  return result;
}
```

### 실패한 풀이 설명

> 원래의 배열에서 가장 작은 횟수로 바꾼 수를 찾는 문제.

아주 골치아픈 문제다. 재귀로는 절대 풀 수 없다. 그렇다고 재귀가 아닌 반복문을 쓴다고 풀리는 것도 아니다.  
위의 실패한 풀이 두 개 모두 `시간초과`로 실패했다.  
swap을 하지 않고 풀어야 풀리는 문제인 것 같다.  
심지어 이전에 솔루션이라고 올라온 풀이들도 현재는 통과하지 않았다.  
문제가 더 엄격해 진 것 같다.  
실패 2번 풀이는 왜 실패인지 아직도 잘 모르겠다. 반복문을 한 번만 도는데도 swap해 주는 곳에서 시간을 더 많이 쓰게 되는 것일까?  
밑에 성공한 다른 풀이를 분석하여 이해해 보도록 하겠다.

### 성공한 풀이

```js
function minimumSwaps(arr) {
  let count = 0;
  let visited = [];

  for (let i = 0; i < arr.length; i++) {
    let j = i;
    let cycle = 0;

    while (!visited[j]) {
      visited[j] = true;
      j = arr[j] - 1;
      cycle++;
    }

    if (cycle) count += cycle - 1;
  }

  return count;
}
```

### 성공한 풀이 설명

이 풀이가 통과하는 결정적인 이유는 `visited`라는 방문한 `index`를 저장하는 배열을 만들어 반복문을 돌더라도 반복 횟수를 줄인다는 점인 것 같다.  
`visited`는 처음에 빈 배열이므로 무조건 `while문`에 들어간다.  
`while문`에 들어간 수는 `true`가 되어 while문 재진입을 막는다.  
`arr[j] - 1`는 현재 숫자보다 1보다 작은 수인데, 이 수가 다시 j로 저장되면서 while문이 순환되게끔 한다.  
이렇게 반복되면서 돌다가 visited가 `true`인 수가 또 들어오게 되면 반복문을 중지하고 count에 `cycle - 1`을 더해 준다.  
cycle에 1을 빼고 더해 주는 이유는 처음에 while문으로 들어갔을 때 1이 올라가는 것을 빼주는 것 같다.

설명을 대충 적었지만 정확히 왜 이렇게 돌아야 하는지 이해가 가지 않아서 나중에 다시 풀어 봐야겠다.

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

- [실패 참고코드](https://stoilsky.com/js-array-performance/)
- [정답 참고코드](https://medium.com/@aman.sharma163/minimum-swaps-2-ea7083cbee77)
- [정답 참조코드 2](https://stackoverflow.com/questions/55210162/minimum-number-of-swaps-to-sort-an-array)
