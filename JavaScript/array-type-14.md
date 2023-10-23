# 배열의 합계, 평균 구하기 reduce()

- [배열의 합계, 평균 구하기 reduce()](#배열의-합계-평균-구하기-reduce)
  - [Array.prototype.reduce()](#arrayprototypereduce)
  - [reduce() 함수로 배열의 합계 구하기](#reduce-함수로-배열의-합계-구하기)
  - [reduce() 함수로 배열의 평균 구하기](#reduce-함수로-배열의-평균-구하기)

## Array.prototype.reduce()

```javascript
arr.reduce(callback[, initialValue])
```

**reduce((누적값, 현재값)=>{다음 누적값},초기값)**

reduce() 메서드는 배열의 각 요소에 대해 주어진 리듀서 (reducer) 함수를 실행하고, 하나의 결과값을 반환한다.

**initialValue**<br>
callback의 최초 호출에서 첫 번째 인수에 제공하는 값.<br>
초기값을 제공하지 않으면 배열의 첫 번째 요소를 사용한다.<br>
빈 배열에서 초기값 없이 reduce()를 호출하면 오류가 발생한다.

## reduce() 함수로 배열의 합계 구하기

```javascript
const num = [1, 2, 3, 4].reduce((a, c) => {
  return a + c;
});
console.log(num); // 10
```

return 생략 가능.

```javascript
[1, 2, 3, 4].reduce((a, c) => a + c);
```

초기값을 넣지 않는 경우는 첫 번째 값이 초기값이 된다. (항상 초기값을 확인해야 한다.)

arr.reduce((누적값, 현재 값)=>{다음 누적값},초기값)<br>
a: 1 c: 2 `1 + 2 = 3`<br>
a: 3 c: 3 `3 + 3 = 6`<br>
a: 6 c: 4 `6 + 4 = 10`<br>
result: `10`

## reduce() 함수로 배열의 평균 구하기

```javascript
const arr = [1, 2, 3, 4];
const result = arr.reduce((a, c) => a + c, 0) / arr.length;

console.log(result); // 2.5
```

`ex. [1,2,3,4] -> 1+2+3+4 / (배열의 총 길이)`

reduce() 함수로 배열 요소의 합을 구하고 그 결과를 배열의 길이로 나누어 배열 element의 평균값을 계산할 수 있다.
