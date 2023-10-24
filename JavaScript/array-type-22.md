# 배열 거꾸로 뒤집기 reverse()

- reverse() 함수
- reverse() 함수 - 원본 배열 유지하기

## reverse() 함수

`Array.prototype.reverse()`

```javascript
arr.reverse();
```

`reverse()` 함수는 배열의 순서를 반전한다. <br>
첫 번째 요소는 마지막 요소가 되며 마지막 요소는 첫 번째 요소가 된다.<br>
이 함수를 실행시키면 `원본 배열이 변형`된다.

```javascript
const array = ["one", "two", "three"];
const reversed = array.reverse();

console.log(reversed); // ['three', 'two', 'one']
console.log(array); // ['three', 'two', 'one']
```

## reverse() 함수 - 원본 배열 유지하기

```javascript
const array = ["one", "two", "three"];
const reversed = [...array].reverse();

console.log(reversed); // ['three', 'two', 'one']
console.log(array); // ['one', 'two', 'three']
```

원본 배열을 유지하며 리턴되는 값만 변경하고 싶을 경우,<br>
원본 배열을 복사해서 사용해야 한다.

배열을 복사하기 위해 spread operator(전개 연산자)를 사용함.<br>
`spread operator(전개연산자)`는 배열이나 객체에서 element들을 꺼내어, 복사해 준다.
