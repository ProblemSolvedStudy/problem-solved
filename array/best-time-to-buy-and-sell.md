# [Best Time to Buy and Sell Stock](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/564/)

> 2020.04.25.(토)

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
```

### 설명

---

## 참고자료
