# 배열에서 특정 값의 개수 구하기 for(), filter(), reduce()

- [for()](#for)
- [filter()](#filter)
- [reduce()](#reduce)

## for()

### `for()` 반복문을 이용하여 배열에서 "banana"의 개수 구하기

```javascript
const arr = ["apple", "banana", "banana", "banana", "mango"];
let count = 0;

for (let i = 0; i < arr.length; i++) {
  if (arr[i] === "banana") {
    count++;
  }
}

console.log(count); // 3
```

가장 기본적인 방법으로 for() 반복문을 이용해 배열의 모든 요소를 순회하면서,<br>
특정 값이 있을 경우 count값을 증가시킨다.

## filter()

filter() 메서드는 배열의 모든 요소를 순회하며,<br>
조건에 부합하는 요소들을 모아 새로운 배열을 반환한다.<br>
새로운 배열의 length로 특정 요소의 개수를 구할 수 있다.

### `filter()` 메서드를 이용하여 배열에서 "banana"의 개수 구하기

```javascript
const arr = ["apple", "banana", "banana", "banana", "mango"];
let count = arr.filter((element) => element === "banana").length;

console.log(count); // 3
```

`arr.filter(element => "banana" === element)`<br>
arr배열의 element를 순회하며 element가 "banana"인 경우를 모아 새로운 배열을 반환한다.<br>
(이 코드는 새로운 배열["banana", "banana", "banana"]을 반환.)

`let count = arr.filter(element => element === "banana").length`<br>
새로운 배열의 길이를 측정하여 count변수에 저장함.<br>
count를 출력해 보면 arr배열에 들어있는 "banana"의 개수 3이 출력됨을 확인할 수 있다.

## reduce()

```javascript
arr.reduce(callback[, initialValue]);
reduce((누적값, 현재값)=>{다음 누적값},초기값);
```

`reduce()` 메서드를 이용하여 배열의 각 요소에 대해 주어진 callback 함수를 실행하고,<br>
하나의 결과값을 반환한다.

### `reduce()` 메서드를 이용하여 배열에서 "banana"의 개수 구하기

```javascript
const arr = ["apple", "banana", "banana", "banana", "mango"];
let result = arr.reduce((count, element) => count + (element === "banana"), 0);

console.log(result); // 3
```

`(count, element) => count + (element === "banana")`<br>
reduce() 함수의 첫 번째 인자로 전달된 callback함수는<br>
element의 값이 "banana"이면 누적값인 count의 숫자를 하나 증가시켜 반환한다.<br>

이 함수는 아래 코드와 같이 쓸 수도 있음.

```javascript
function(count, element){
  return count + (element === "banana");
}
```

`let result = arr.reduce((count, element) => count + (element === "banana"), 0);`

배열의 값이 "banana"인 경우 초기값이 0인 count의 값을 증가시켜서 반환한다.

result를 출력해 보면 "banana"의 개수 3이 출력됨을 확인할 수 있다.
