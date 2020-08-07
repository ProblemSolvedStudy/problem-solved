# [Mark and Toys](https://www.hackerrank.com/challenges/mark-and-toys/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=sorting)

> 2020.08.06 (목)

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
function maximumToys(prices, k) {
  prices.sort((a, b) => a - b);

  const calcMax = (result, v) => {
    if (k - v < 0) return result;
    k -= v;
    return result + 1;
  };

  return prices.reduce(calcMax, 0);
}
```

### 설명

> 주어진 금액으로 가장 많이 살 수 있는 장난감의 개수를 구하는 문제

1. 가장 많은 개수를 구하기 위해서는 `작은 금액으로 여러 개`를 구매해야 한다. 따라서 `prices 배열`을 오름차순으로 정렬한다.
2. 주어진 금액인 `k`가 prices를 뺐을 때 0보다 작으면 원래 값을 리턴하고, 그게 아니면 price를 빼고 개수를 1 늘려 준다.
3. `reduce`를 사용해 값을 계산하고 리턴한다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
function swap(arr, i, j) {
  const tmp = arr[i];
  arr[i] = arr[j];
  arr[j] = tmp;
}

function maximumToys(prices, k) {
  const len = prices.length;
  let sum = 0;
  let minIdx;

  for (let i = 0; i < len; i++) {
    minIdx = i;
    for (let j = i + 1; j < len; j++) {
      if (prices[minIdx] > prices[j]) minIdx = j;
    }
    const tmp = sum + prices[minIdx];
    if (tmp > k) return i;
    if (tmp === k) return i + 1;
    if (i !== minIdx) swap(prices, i, minIdx);
    sum = tmp;
  }

  return len;
}

// 시간복잡도 : O(n^2)
// 공간복잡도 : O(1)
```

### 설명

모든 가격을 정렬하지 않고도 소지금액으로 살 수 있는 장난감의 갯수를 즉시 반환하고 싶어서 선택정렬을 사용하기로 했다.  
선택정렬을 사용하면 왼쪽부터 차례대로 오름차순 정렬을 하기 때문이다.

정렬과 동시에 정렬된 가격들의 합(`sum`)을 업데이트 하다가 `sum`이 소지금액인 `k`보다 작거나 같을 경우 구매 가능한 장난감의 갯수를 즉시 리턴하도록 했다.  
(장난감의 갯수는 `prices`의 인덱스로 알 수 있다.)

엄밀히 말하면 `sum`을 `k`와 직접 비교하지는 않고, `sum + prices[min]`을 `k`와 비교한다. 불필요하게 swap을 하지 않기 위해서이다.

- `sum + prices[min] > k` 인 경우 즉시 아이템의 갯수 `i`를 리턴하고 (-> swap할 필요가 없음)
- `sum + prices[min] === k` 인 경우 아이템의 갯수 `i + 1`를 리턴하고 (-> swap할 필요가 없음)
- `sum + prices[min] < k` 인 경우에는 **`i`가 `minIdx`와 다를 경우에만 swap**을 시켜준 뒤 `sum`을 `sum + prices[min]`로 대체한다. (즉, `sum`에 새로운 최소값을 더해서 업데이트 시켜준다.)

<br />

## Ed

### 풀이

```js
function maximumToys(prices, k) {
    let count = 0;
    let totalPrice = 0;
    prices.sort((a, b) => a - b);
    for (let i = 0; i < prices.length; i++) {
        totalPrice += prices[i];
        if (totalPrice > k) break;
        count++;
    }
    return count;
}
```

### 설명

> 가지고 있는 돈 (k) 안에서 가장 많은 장난감(장난감 가격 배열 prices)을 살 수 있는 경우를 구하는 문제

- 장난감 가격이 저렴하면 저렴할수록 많은 양을 구매할 수 있기 때문에, `prices`를 우선 오름차순으로 정렬했다.
- 순회를 돌면서 전체 장난감 가격 `totalPrice`에 계속해서 더해준다. 장난감 `count`를 1씩 계속 증가시킨다.
- `totalPrice`가 가지고 있는 돈`k`를 넘으면 반복문을 종료하고 `count`를 반환한다.

---

## 참고자료
