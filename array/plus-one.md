# [Plus One](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/559/)

> 2020.05.02.(토)

## Hoo

### 실패한 풀이

```js
const plusOne = (digits) => {
	let lastTen =
		digits.length >= 11 ? digits.splice(-11, 11) : digits.splice(-digits.length, digits.length);

	const isFirstZero = lastTen[0] === 0 && digits.length > 0;
	const isSecondZero = lastTen[1] === 0 && digits.length > 1 && isFirstZero;

	const plusNumber = parseInt(lastTen.join("")) + 1;
	const resultLast = plusNumber.toString().split("");

	const resultLastNum = [];
	resultLast.forEach((el) => resultLastNum.push(parseInt(el)));

	if (isFirstZero) digits.push(0);
	if (isSecondZero) digits.push(0);

	resultLastNum.forEach((el) => digits.push(el));
	return digits;
};
```

### 성공한 풀이

```js
const plusOne = (digits) => {
	for (var i = digits.length - 1; i >= 0; i--) {
		if (++digits[i] > 9) digits[i] = 0;
		else return digits;
	}
	digits.unshift(1);
	return digits;
};
```

### 설명

> 배열을 하나의 숫자라고 생각하고, 숫자에 1이 더해졌을 때 결과배열을 반환하는 문제

처음에 9와 같이 경계선에 있는 값을 생각하고 무작정 배열을 숫자로 변환해 더했다.  
자바스크립트의 숫자형이 감당할 수 없는 크기의 숫자가 배열로 나오면 `Fail`이 발생했다.  
그것에 예외처리를 해 주기 위해 숫자를 중간부터 잘라서 더하는 일도 해 봤지만, `999999999999...`와 같은 값은 계산이 불가능하다.

이 문제는 주어진 값이 배열인 점을 이용해서 반복해서 올림이 있는지 찾아내서 값을 바꿔 준다.  
근데 `digits.unshift(1);`를 했을 때 아래 이미지처럼 자동으로 맨 앞자리가 0인 것과 아닌 것을 구분해 1을 붙여 줬다.  
이에 대한 이유를 찾지 못했다.

![image](https://user-images.githubusercontent.com/30427711/81428662-870bad00-9197-11ea-87cf-a0a5bcff1ee7.png)

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 풀이

```js
var plusOne = function (digits) {
	let up = true;

	const plus = (digit) => {
		const plused = digit + 1;
		if (plused === 10) {
			up = true;
			return 0;
		} else {
			up = false;
			return plused;
		}
	};

	for (let i = digits.length - 1; i >= 0; i--) {
		if (up) {
			digits[i] = plus(digits[i]);
			if (i === 0 && digits[i] === 0) {
				digits.unshift(1);
			}
		}
	}

	return digits;
};
```

### 설명

`parseInt`나 `Number`를 사용한 sting -> number 변환이 불가능한 문제여서 일의 자리에 1을 더한 결과에 따라 한자리씩 올림처리를 해줄지 말지 판별해줘야 했다.<br />
이러한 판별을 위해 `up`이라는 변수와 `plus`라는 함수를 사용했는데,<br />
`up`은 true/false boolean값을 가지고 있어서 true이면 올림처리가 필요하다는걸 의미하고, false이면 올림처리가 불필요하다는걸 의미한다.<br />
`plus`는 특정 자릿수에 1을 더했을때 올림처리가 필요한지 아닌지를 판별해서 해당 자릿수와 `up`의 값을 업데이트 해주는 함수이다.<br />
`digits`를 뒤에서 부터 순회하면서 `plus` 함수를 통해 값을 업데이트 해주고, 맨 마지막 0번째 인덱스에서 올림처리가 필요할 경우 1을 더해서 문제를 해결했다.

## Ed

### 풀이

```js
var plusOne = function (digits) {
	// return new String(parseInt(digits.join('')) + 1).split('').map(Number);

	let i = digits.length - 1;
	while (digits[i] === 9) digits[i--] = 0;
	if (i < 0) digits.unshift(1);
	else digits[i] += 1;
	return digits;
};
```

### 설명

이 문제는 처음에 주석의 코드로 시도했는데 잘 되지 않았다. 배열을 수로 변경한 뒤 +1 을 하고 다시 배열로 바꿔주는 식으로 해결하고자 했는데, 굉장히 큰 수가 있어 이 방식은 불가능하게 막아놨다.

제한 시간안에 문제를 다 풀지 못해 다른 답안을 참고했다.

1. 마지막 수가 9라면, 해당 수를 0으로 만들고 `i`를 -1 한다. 9에서 1을 더하면 10이 되는 과정이다. 이 부분에서 `--`에 대한 내 이해가 부족하다고 느꼈다. `--`와 `-= 1` 의 정확한 차이를 더 공부해봐야겠다. `-= 1` 에선 제대로 동작하지 않았다.
2. `i` 가 0 이하라면, 즉 자릿수가 첫번째라면 맨 앞에 1을 붙인다. 자리올림을 나타낸 식이다.
3. 아니라면 자리올림이 더 이상 일어나지 않는 마지막 수에 1을 더한다.

---

## 참고자료
