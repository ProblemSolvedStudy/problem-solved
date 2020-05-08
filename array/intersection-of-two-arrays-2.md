# [Intersection of Two Arrays II](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/674/)

> 2020.05.02.(토)

## Hoo

### 풀이

```js
const intersect = (nums1, nums2) => {
    let result = [];
    
    for (let i = nums1.length-1; i >= 0; i--) {
        for (let j = 0; j < nums2.length; j++) {
            if (nums1[i] === nums2[j]) {
                result.push(nums1[i]);
                nums1.splice(i, 1);
                nums2.splice(j, 1);
            }
        }
    }
    
    return result;
};
```

### 설명

> 두 배열에서 중복되게 들어있는 값만 배열로 반환하는 문제

마땅한 더 좋은 방법이 생각이 나지 않아서 이중 반복문을 사용했다.  
이중 반복문을 돌아 값을 하나씩 비교하면서 같으면 배열에 `push`하고 두 배열에서는 삭제하도록 했다.  
삭제하지 않으면 `[4,9,4,9]`와 같은 중복되는 값이 걸러지지 않고 추가로 배열에 들어가 버린다.  


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

이 문제는 제대로 풀지 못했다. 추후 다시 풀어보려고 한다.

---

## 참고자료
