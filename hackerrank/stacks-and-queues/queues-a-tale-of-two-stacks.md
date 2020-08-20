# [Queues: A Tale of Two Stacks](https://www.hackerrank.com/challenges/ctci-queue-using-two-stacks/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=stacks-queues)

> 2020.08.20 (목)

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
```

### 설명

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제이해

아래 두 가지 요구사항을 충족하도록 코드를 구현하고

1. 2개의 stack을 이용해서 queue를 구현한다.
2. `put`, `pop`, `peek` 3개의 메서드를 구현한다. 각각의 메서드가 수행하는 기능은 query 1, 2, 3의 기능과 매칭된다.
   > - query 1 x : `put` (= enqueue(x))
   > - query 2 : `pop` (= dequeue())
   > - query 3 : `peek` (queue의 맨 첫번째 값을 구한다)

query 3을 처리한 결과값(=queue의 맨 첫번째 값)을 콘솔 출력하면 된다.

### 풀이

```js
function processData(input) {
  const stack1 = [];
  const stack2 = [];

  const put = (v) => {
    if (stack2.length) {
      while (stack2.length) {
        stack1.push(stack2.pop());
      }
    }
    stack1.push(v);
  };

  const pop = () => {
    if (stack2.length) {
      return stack2.pop();
    }
    if (stack1.length === 1) {
      return stack1.pop();
    }
    while (stack1.length) {
      stack2.push(stack1.pop());
    }
    return stack2.pop();
  };

  const peek = () => {
    if (!stack1.length) {
      while (stack2.length) {
        stack1.push(stack2.pop());
      }
    }
    console.log(stack1[0]);
  };

  const process = {
    1: put,
    2: pop,
    3: peek,
  };

  const queries = input.split('\n');
  for (let i = 1, length = queries.length; i < length; i++) {
    process[queries[i][0]](queries[i].slice(2));
  }
}
```

1. `put`, `pop`, `peek` 3개의 메서드를 위와 같이 구현한 뒤 `process`라는 객체를 사용해서 query와 맵핑했다.
2. 문자열로된 input을 적절하게 처리해서 오직 배열을 생성했다. (=`queries`)
3. `queries`를 순회하면서 query 번호에 맞춰 `process`에 맵핑해놓은 메서드들을 실행했다. (맨 첫번째 인자는 query의 갯수를 나타내는 값이므로 제외하고 인덱스 1부터 순회를 시작한다.)

코드를 제출해보니 6, 7번 테스트 케이스(query 갯수 10만개)를 시간초과로 통과하지 못했다.
여러 가지 방법을 시도해보다가 정답을 보고 학습하기로 결정.

<br />

```js
function processData(input) {
  const queries = input.split('\n');
  const stack1 = [];
  const stack2 = [];
  for (let i = 1; i < queries.length; i++) {
    if (queries[i][0] === '1') {
      const value = queries[i].slice(2);
      stack1.push(value);
    }
    if (queries[i][0] === '2') {
      if (stack2.length) stack2.pop();
      else {
        while (stack1.length) stack2.push(stack1.pop());
        stack2.pop();
      }
    }
    if (queries[i][0] === '3') {
      if (stack2.length) console.log(stack2[stack2.length - 1]);
      else {
        while (stack1.length) stack2.push(stack1.pop());
        console.log(stack2[stack2.length - 1]);
      }
    }
  }
}
```

문제에서 요구하는 것은 queue의 맨 첫번째 값이다. 그리고 **queue의 맨 첫번째 값은 언제나 `stack2`의 맨 마지막 요소**이다.  
풀이의 핵심은 **`stack2`의 맨 마지막 요소를 최신 상태로 유지해주는 것**이다.

`if (stack2.length)` 의 조건문이 `true`를 반환한다는건 `stack2`의 마지막 요소가 존재한다는 뜻이고, `stack2`의 마지막 요소가 queue의 맨 첫번째 값이라는 뜻이다.  
반대로 조건식이 `false`를 반환하다면 `stack2`가 비어있다는 뜻이고, 이때는 `stack1`의 0번째 인덱스의 값이 queue의 첫번째 값이라는 뜻이다. 이때는 while문을 사용하여 `stack1`의 모든 요소를 `stack2`로 옮겨주는 작업이 필요하다.

> 참고로 요소를 옮기는 작업을 하지 않고 stack 두 개를 모두 사용할 경우 메모리 사용량 초과로 _Abort Called (호출 거부)_ 에러가 뜬다.

결론적으로 query를 실행할때마다 모든 값들을 하나의 stack에서 다른 stack으로 옮길 필요가 없이 **`pop`, `peek`을 실행할때만 _일괄적으로_ 첫번째 `stack1`에서 `stack2`로 옮겨**주면 되고 `put`을 실행할때는 단순하게 `stack1`에 push만 해주면 된다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
