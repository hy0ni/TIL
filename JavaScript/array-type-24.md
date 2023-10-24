# 배열 첫 번째 값, 마지막 값 가져오기

## 배열 첫 번째 값 가져오기

```javascript
const arr = ["one", "two", "three"];
const firstValue = arr[0];

console.log(firstValue); // 'one'
```

배열의 index는 0부터 시작한다.

## 배열 마지막 값 가져오기

```javascript
const arr = ["one", "two", "three"];
const firstValue = arr[arr.length - 1];

console.log(firstValue); // 'three'
```

arr.length(배열의 길이)는 3이지만<br>
배열의 index는 0부터 시작하므로<br>
마지막 index 값은 arr.length - 1, 즉 2가 된다.
