# [Best Time to Buy and Sell Stock](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/564/)

> 2020.04.25.(토)

## Hoo

### 풀이

```js
const maxProfit = (prices) => {
  let result = 0;

  for (let i = 0; i < prices.length; i++) {
    if (prices[i] < prices[i + 1]) {
      result += prices[i + 1] - prices[i];
    }
  }

  return result;
};
```

### 설명

> 가장 이익이 크게 거래 누적값을 계산하는 문제이다.

내가 이해한 제약조건은 크게 두 가지이다.

1. 사기 전에는 팔 수 없고, 팔기 전에는 살 수 없다.
2. 사는 값이 바로 이후에 팔 값보다 작으면 산다.

하지만 문제의 예시와 풀이가 살짝 맞지 않는 것 같다.  
내가 푼 풀이가 나중에 보니 솔루션 중 하나였지만, Example 2번은 `(2-1) + (3-2) + (4-3) + (5-4)` 방식으로 계산되어 답이 나온다.  
어쨌든 위의 두 조건에 맞춰 반복문을 돌며 누적값을 계산해 나가도록 풀었다.

## Hoi

### 풀이

```js
var maxProfit = function (prices) {
  if (prices.length <= 1) return 0;
  var profits = 0;
  for (var i = 1, l = prices.length; i <= l - 1; ++i) {
    if (prices[i] > prices[i - 1]) {
      profits += prices[i] - prices[i - 1];
    }
  }
  return profits;
};
```

### 설명

이 문제는 오늘 풀었던 문제중에 가장 난이도가 높다고 생각한 문제다.
일단 문제 이해 자체를 잘 못하고 풀어서 그런지 더욱이 어려웠다.
나는 prices로 주어지는 배열의 첫번째는 무조건 구입하고 시작하는줄 알았지만
그게 아니라 다음 값과 비교한 후 최고의 이득을 도출하는 식이였다.
문제의 요구사항을 다 이해하니 비교적 처음보다는 쉽다고 느껴졌다.
이 문제는 다시 풀어볼만한 문제라고 생각된다.

## Reese

### 풀이

```js
var maxProfit = function (prices) {
  const numOfPrices = prices.length;
  let i = 0;
  let valley = prices[0];
  let peak = prices[0];
  let maxProfit = 0;

  while (i < numOfPrices - 1) {
    while (i < numOfPrices - 1 && prices[i] >= prices[i + 1]) {
      i++;
    }
    valley = prices[i];
    while (i < numOfPrices - 1 && prices[i] <= prices[i + 1]) {
      i++;
    }
    peak = prices[i];
    maxProfit += peak - valley;
  }
  return maxProfit;
};
```

### 설명

> 이날 풀었던 문제들 중 가장 어렵게 느껴졌던 문제다. 1시간정도 고민하다가 solution #2 Peak Valley Approach를 Javascript로 구현하면서 공부하는쪽으로 방향을 잡았다.

예시 `[7,1,5,3,6,4]`의 가격들을 그래프로 나타내면 다음과 같이 나타낼 수 있는데,

![solution #2 Peak Valley Approach](https://leetcode.com/media/original_images/122_maxprofit_1.PNG)

여기서 핵심은 **valley(골짜기) 다음에 등장하는 모든 peak(정상)을 고려해야 한다**는 점이다.

단순히 최저가에 사고 최고가에 팔기위해 day2에 1원에 산 뒤 day5까지 기다렸다가 6원에 팔면 최대 수익을 얻을 수 없다는 뜻이다. day4에 3원에 샀다가 day5에 6원에 팔아서 얻을 수 있는 수익을 놓치기 때문. 위 그래프에서 알 수 있듯이 `C`는 언제나 `A + B` 보다 작다.

때문에 valley '다음에' 등장하는 peak을 전부 고려하여 모든 gap을 수익에 포함시켜야 한다.

```js
while (i < numOfPrices - 1) {
  // valley 찾기
  while (i < numOfPrices - 1 && prices[i] >= prices[i + 1]) {
    i++;
  }
  valley = prices[i];

  // valley 바로 다음에 등장하는 peak 찾기
  while (i < numOfPrices - 1 && prices[i] <= prices[i + 1]) {
    i++;
  }
  peak = prices[i];

  // valley 와 peak의 차이를 최대 수익에 더해주기
  maxProfit += peak - valley;
}
```

이 문제는 나중에 다시 풀어볼만한 문제인 것 같다.

## Ed

### 풀이

```js
var maxProfit = function(prices) {
    return prices.reduce((profit, stock, i, arr) => {
        if (stock < arr[i + 1]) profit += (arr[i + 1] - stock);
        return profit;
    }, 0)
};
```

### 설명

배열을 순회하며 현재 값이 다음 값보다 작을 경우, profit이 있다는 뜻이다.
그 경우 다음 값에서 현재 값을 뺀 수만큼 profit에 더한 후, 총합을 리턴한다.

---

## 참고자료
