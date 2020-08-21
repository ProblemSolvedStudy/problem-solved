# [Balanced Brackets](https://www.hackerrank.com/challenges/balanced-brackets/problem?isFullScreen=true)

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
function isBalanced(s) {
  let arr = [];
  
  // 1번 풀이
  for (let i = 0; i < s.length; i++) {
    if (s[i] === '{') arr.push('}');
    else if (s[i] === '[') arr.push(']');
    else if (s[i] === '(') arr.push(')');
    else if (s[i] === arr[arr.length - 1]) arr.pop();
    else return "NO";
  }

  // 2번 풀이 
  const opens = ['(', '{', '['];
  const closes = [')', '}', ']'];
  const map = {
      ')': '(',
      '}': '{',
      ']': '['
  };

  for (let i = 0; i < s.length; i++) {
      if (opens.includes(s[i])) arr.push(s[i]);

      if (closes.includes(s[i])) {
          const paired = arr.pop();
          if (map[s[i]] !== paired) return 'NO';
      }
  }

  return arr.length ? "NO" : "YES";
}

```

### 설명

> 괄호들이 짝이 맞는지 확인하는 문제

#### 1번 풀이

- 주어진 괄호인 `{[()]}`의 여는 괄호들을 닫는 괄호로 하나씩 치환해 배열에 추가한다.
- 닫는 괄호가 나오고 배열의 마지막 문자와 같으면 배열에 `pop하여 삭제`한다.
- 위의 두 조건에도 들지 않으면 짝이 맞지 않는 것이므로 `NO를 반환`한다.
- 여는 괄호의 숫자가 많을 때 NO를 반환하기 위해 마지막에 남은 문자의 개수로 `YES와 NO를 판단하여 반환`한다.

#### 2번 풀이

- `opens와 closes`들을 배열로 묶고, 객체를 사용해 `닫는 괄호는 key`로, `여는 괄호는 value`로 묶는다.
- 반복문을 돌며 1번 풀이와 동일하게 여는 괄호이면 배열에 추가한다.
- 닫는 괄호가 나오면 `pop`하여 짝이 맞는지를 만들었던 객체를 통해 판별한다.
- 마지막 반환 부분은 1번 풀이와 동일하다.

## Hoi

### 풀이

```js
```

### 설명

## Reese

### 문제이해

{, [, (, ), ], } bracket이 균형을 이루고 있는지 판별해서 "YES" 또는 "NO"를 반환하는 문제이다.  
균형을 이룬다는건 '{'와 '}' '('와 ')', '['와 ']' 처럼 모양이 같은 bracket 끼리 pair를 이루고 있어야 한다는 뜻이다.

```
{[()]}          // YES
{[(])}          // NO
{{[[(())]]}}    // YES
```

두번째 예시의 경우 ']'와 ')'의 위치가 바뀌어서 균형이 잡혀있지 않은 상태이고, "NO"를 반환해야 한다.

### 풀이

```js
function isBalanced(s) {
  const open = ['{', '(', '['];
  const close = ['}', ')', ']'];

  if (close.includes(s[0])) return 'NO';

  const indice = [];
  for (let i = 0, len = s.length; i < len; i++) {
    const openIdx = open.indexOf(s[i]);
    if (openIdx !== -1) {
      indice.push(openIdx);
    } else {
      if (s[i] !== close[indice[indice.length - 1]]) return 'NO';
      indice.pop();
    }
  }

  return indice.length ? 'NO' : 'YES';
}
```

### 설명

1. opening bracket과 closing bracket을 각각 배열에 할당해놓았다. 이때 pair를 이루는 bracket들이 같은 인덱스에 위치하도록 했다.
2. 만약 인자로 받은 bracket 문자열이 closing bracket으로 시작할 경우 balanced brackets의 조건을 충족하지 않기 때문에 early return을 해준다.
3. 2번의 경우가 아니라면 (문자열이 opening bracket으로 시작한다면) `indice`라는 stack을 만들어놓고 문자열을 순회하면서 bracket이 opening bracket인지 판별하여 opening bracket이 맞을 경우 open 배열에서의 인덱스를 `indice`에 push하고, opening bracket이 아닐 경우 즉, closing bracket일 경우 indice의 마지막 요소 (가장 마지막에 추가된 opening bracket의 인덱스)를 참조하여 pair를 이루는 closing bracket인지를 확인했다.  
   이때 pair를 이루는 bracket인 경우 `indice`의 마지막 요소를 pop하여 제거하고, 그렇지 않을 경우 즉시 "NO"를 반환한다.
4. 순회가 종료된 시점에 indice의 길이를 확인하는데, pair를 이루는 closing bracket이 없어서 `indice`가 완전히 비워지지 않았다면 balanced bracket의 조건을 충족하지 않기 때문에 "NO"를 반환한다.

<br />

## Ed

### 풀이

```js
```

### 설명

---

## 참고자료
