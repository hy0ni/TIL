# 배열을 문자열로 변환하기

- join() 함수 사용하기
- toString() 함수 사용하기

## join() 함수 사용하기

`Array.prototype.join()`

```javascript
arr.join([separator]);
```

`join()`함수는 배열의 모든 요소를 연결해 하나의 문자열로 만든다.

```javascript
const elements = ["Fire", "Air", "Water"];

console.log(elements.join()); // "Fire,Air,Water"
console.log(elements.join("")); // "FireAirWater"
console.log(elements.join("-")); // "Fire-Air-Water"
```

`join()` 함수는 파라미터로 값이 아무것도 전달되지 않으면,<br>
배열의 각 값들은 ','를 구분자로 연결된다.

## toString() 함수 사용하기

`Array.prototype.toString()`

```javascript
arr.toString();
```

`toString()` 함수는 지정된 배열 및 그 요소를 나타내는 문자열을 리턴한다.

```javascript
const array = [1, 2, "A", "1a"];

console.log(array.toString()); // 1,2,A,1a
```

배열의 `toString()` 함수는 배열의 값들을 ','로 연결한 문자열을 리턴한다.
