# 배열에 특정 값 포함 여부 확인하기

- [배열에 특정 값 포함 여부 확인하기](#배열에-특정-값-포함-여부-확인하기)
  - [indexOf(), lastIndexOf()](#indexof-lastindexof)
  - [findIndex()](#findindex)
  - [includes()](#includes)
  - [some()](#some)
  - [includes()와 some() 차이점](#includes와-some-차이점)
    - [includes()](#includes-1)
    - [some()](#some-1)

## indexOf(), lastIndexOf()

```javascript
arr.indexOf(searchElement[, fromIndex])
arr.lastIndexOf(searchElement[, fromIndex])
```

`indexOf()`<br>
배열 안에서 찾으려는 값(searchElement)과 정확하게 일치(===)하는'첫번째' element의 index를 리턴.

`lastIndexOf()`<br>
배열 안에서 찾으려는 값(searchElement)과 정확하게 일치(===)하는 '마지막' element의 index를 리턴.

두 함수 모두 찾으려는 값이 배열에 없으면 -1을 리턴한다.<br>
이 특징을 이용하여 특정 값이 배열에 포함되어 있는지 확인할 수 있다.

```javascript
const arr = [1, 2];
let isElementYn = true;

if (arr.indexOf(3) < 0) {
  isElementYn = false;
}

console.log(isElementYn); // false
```

숫자 3이 arr 배열에 포함되어 있는지 체크.<br>
arr.indexOf(3)은 찾을 수 없으므로 -1 리턴.

## findIndex()

```javascript
arr.findIndex(callback(element[, index[, array]])[, thisArg])
```

```javascript
const arr = [1, 2, 3, 2];

function findNumberTwo(element) {
  if (element === 2) {
    return true;
  }
}

console.log(arr.findIndex(findNumberTwo)); // 1
console.log(arr.findIndex(findNumberTwo) > -1); // true
```

arr.findIndex()에 전달된 callback 함수는<br>
배열의 각각의 element를 받아서 그 값이 2인지 확인하고,<br>
그 값이 2이면 true를 리턴한다.

배열에 찾으려는 값이 있다면
findIndex 함수는 0 이상의 값을 리턴하게 된다.

```javascript
const arr = [1, 2, 3, 2];

function findNumberTwo(element) {
  if (element === 4) {
    return true;
  }
}

console.log(arr.findIndex(findNumberTwo)); // 1
console.log(arr.findIndex(findNumberTwo) > -1); // false
```

만약 찾으려는 값이 없으면, findIndex 함수는 -1을 리턴한다.

## includes()

```javascript
arr.includes(valueToFind[, fromIndex])
```

`includes()` 함수는 배열이 특정값을 포함하고 있는지의 여부를 `boolean 값으로 반환`한다.

```javascript
const arr = [1, 2];

console.log(arr.includes(1)); // true
console.log(arr.includes(3)); // false
console.log(arr.includes(1, 2)); // false
```

`arr.includes(1)`<br>
arr 배열에 1이 있으므로 true 리턴.

`arr.includes(3)`<br>
arr 배열에 3이 없으므로 fasle 리턴.

`arr.includes(1, 2)`<br>
두 번째 파라미터인 fromIndex에 배열의 길이보다 크거나 같은 값이 들어가면,<br>
무조건 false를 리턴한다.

arr배열의 길이는 2인데, fromIndex 자리에 2가 들어갔으므로 false가 리턴된다.

`arr.includes(2, -1)`<br>
fromIndex 자리에 음수가 들어가면, 실제 시작 index는 '배열의 길이 + fromIndex'로 계산된다.<br>
배열의 길이는 2이고, fromIndex는 -1이므로,<br>
실제 검색을 시작하는 index는 1이 된다. (2 + (-1))

arr[1]에 2가 있으므로, true가 리턴 된다.

## some()

```javascript
arr.some(callback(element[, index[, array]])[, thisArg])
```

`some()` 함수는 배열에서 값을 찾는 조건을 callback 함수로 전달하고,<br>
배열에 조건에 맞는 값이 있는지 여부(boolean)를 리턴한다.<br>
조건에 맞는 값이 있으면 true, 조건에 맞는 값이 없으면 false를 리턴한다.<br>
`some()` 함수 배열을 변경하지 않는다.

```javascript
const arr1 = [1, 2, 3, 2];
const arr2 = [4, 5, 6, 7];

function findNumberTwo(element) {
  if (element === 2) {
    return true;
  }
}
console.log(arr1.some(findNumberTwo)); // true
console.log(arr2.some(findNumberTwo)); // false
```

## includes()와 some() 차이점

### includes()

- 배열에 특정 요소가 포함되어 있는지 여부를 나타내는 boolean 값을 반환한다.
- 기본 값과 기본 값이 아닌 값 모두와 함께 사용할 수 있다.
- 찾은 요소의 인덱스에 대한 액세스를 제공하지 않는다.
- 배열을 수정할 수 있는 수단을 제공하지 않는다.
- 더 간단하고 읽기 쉽다.

```javascript
const fruits = ["apple", "banana", "orange"];

console.log(fruits.includes("apple")); // true
console.log(fruits.includes("pear")); // false
```

### some()

- 배열의 적어도 하나의 요소가 특정 조건을 만족하는지 여부를 나타내는 boolean 값을 반환한다.
- 기본 값과 기본 값이 아닌 값 모두와 함께 사용할 수 있다.
- 조건을 만족하는 첫 번째 요소의 인덱스에 대한 액세스를 제공한다.
- 사용된 콜백 함수가 true를 반환하는 경우(예: 요소 제거) 배열을 수정하는 데 사용할 수 있다.
- 더 복잡한 조건을 확인할 수 있으므로 더 유연하다.

```javascript
const fruits = ["apple", "banana", "orange"];

console.log(fruits.some((fruit) => fruit === "apple")); // true
console.log(fruits.some((fruit) => fruit === "pear")); // false
```

- 배열에 특정 값이 포함되어 있는지 단순히 확인하는 경우 includes()가 더 적절한 선택일 수 있음.
- 배열의 요소가 특정 조건을 충족하는지 여부를 확인해야 하는 경우 some()이 더 적절한 선택일 수 있음.
