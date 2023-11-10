# 배열 중복 값 개수 구하기 reduce()

### reduce() 함수 이용하여 중복 값 개수 구하기

```javascript
arr.reduce(callback[, initialValue]);
reduce((누적값, 현재값)=>{다음 누적값},초기값);
```

reduce() 함수는, 배열의 값을 순회하면서 배열의 값을 특정 형태로 누적하는데 사용한다.

```javascript
const arr = ["a", "b", "a", "b", "c"];

const result = arr.reduce((acc, curr) => {
  acc[curr] = (acc[curr] || 0) + 1;
  return acc;
}, {});

console.log(JSON.stringify(result)); // {"a":2,"b":2,"c":1}
```
