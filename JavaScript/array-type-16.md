# 배열 정렬하기 (오름차순, 내림차순, 문자열, 객체)

- [배열 정렬하기 (오름차순, 내림차순, 문자열, 객체)](#배열-정렬하기-오름차순-내림차순-문자열-객체)
  - [sort()](#sort)
  - [숫자 정렬하기](#숫자-정렬하기)
    - [숫자 오름차순 정렬하기 `(a-b 오름차순)`](#숫자-오름차순-정렬하기-a-b-오름차순)
    - [숫자 내림차순 정렬하기 `(b-a 내림차순)`](#숫자-내림차순-정렬하기-b-a-내림차순)
  - [문자열 정렬하기](#문자열-정렬하기)
    - [문자열 오름차순으로 정렬하기](#문자열-오름차순으로-정렬하기)
    - [문자열 내림차순으로 정렬하기](#문자열-내림차순으로-정렬하기)
    - [첫번째 글자의 코드넘버를 비교하여 오름차순 정렬하기](#첫번째-글자의-코드넘버를-비교하여-오름차순-정렬하기)
    - [첫번째 글자의 코드넘버를 비교하여 내림차순 정렬하기](#첫번째-글자의-코드넘버를-비교하여-내림차순-정렬하기)
    - [사전순으로 오름차순 정렬하기](#사전순으로-오름차순-정렬하기)
    - [사전순으로 내림차순 정렬하기](#사전순으로-내림차순-정렬하기)
  - [문자열 대소문자구분 없이 정렬하기](#문자열-대소문자구분-없이-정렬하기)
    - [문자열 오름차순으로 정렬하기(대소문자 구분 없이)](#문자열-오름차순으로-정렬하기대소문자-구분-없이)
    - [문자열 내림차순으로 정렬하기(대소문자 구분 없이)](#문자열-내림차순으로-정렬하기대소문자-구분-없이)
  - [객체로 구성된 배열 정렬하기](#객체로-구성된-배열-정렬하기)
    - [가격순 오름차순으로 정렬하기](#가격순-오름차순으로-정렬하기)
    - [가격순 내림차순으로 정렬하기](#가격순-내림차순으로-정렬하기)
    - [이름순 오름차순 정렬하기](#이름순-오름차순-정렬하기)
    - [이름순 내림차순 정렬하기](#이름순-내림차순-정렬하기)

## sort()

```javascript
arr.sort([compareFunction]);
sort(compareFunction(a, b));
```

sort() 메서드는 기본적으로 오름차순으로 정렬한다.

정렬 순서를 정의하는 함수(compareFunction)가 생략되면,  
배열 요소를 문자열로 변환하고 변환된 문자열은 유니코드 코드 포인트 순서로 비교하여 정렬된다.

sort() 함수가 리턴하는 값이 0보다 작은 경우 a를 b보다 앞에 오도록 정렬. `(a-b 오름차순)`  
sort() 함수가 리턴하는 값이 0보다 큰 경우 b를 a보다 앞에 오도록 정렬. `(b-a 내림차순)`  
sort() 함수가 0을 리턴하면 a와 b의 순서를 변경하지 않음. `(a == b)`

배열의 요소가 undefined인 경우 문자열로 변환되지 않는다.  
배열의 요소가 undefined인 경우 배열의 맨 끝에 정렬된다.

`반환 값`  
정렬한 배열을 반환.  
이때, `복사본이 만들어지는 것이 아니기 때문에 원본 배열이 정렬되는 것에 유의`해야 한다.

## 숫자 정렬하기

```javascript
const array = ["6", "8", "10", "1", "4"];
array.sort(); // ['1', '10', '4', '6', '8']
```

sort() 메서드 사용 시 compare 함수를 생략하면  
유니코드 순서로 비교하여 오름차순으로 정렬된다.

유니코드 순서에 따라 ['1', '10', '4', '6', '8']로 정렬됨.

ex) "바나나"는 "체리" 앞에 정렬됨.

숫자 정렬에서는 9가 10보다 앞에 오지만 `숫자는 문자열로 변환`되기 때문에  
`"10"은 유니코드 순서에서 "9"앞에 온다.`

### 숫자 오름차순 정렬하기 `(a-b 오름차순)`

```javascript
const arr = [6, 3, 1, 10, 9, 13];
arr.sort((a, b) => a - b); // [1, 3, 6, 9, 10, 13]
```

sort() 메서드를 사용해 숫자를 `오름차순`으로 정렬하기 위해서는 compare 함수를 활용해야 한다.

`arr.sort((a, b) => a - b)`
두 숫자의 차이를 리턴하는 함수를 sort() 메서드의 인자로 전달하여,  
배열을 오름차순으로 정렬.  
이때, 배열을 복사하여 정렬하는 것이 아니기 때문에 원본 배열도 정렬된다.

### 숫자 내림차순 정렬하기 `(b-a 내림차순)`

```javascript
const arr = [6, 3, 1, 10, 9, 13];
arr.sort((a, b) => b - a); // [13, 10, 9, 6, 3, 1]
```

sort() 메서드를 사용해 숫자를 `내림차순`으로 정렬하기 위해서는 compare 함수를 활용해야 한다.

`arr.sort((a, b) => b - a)`  
두 숫자의 차이를 리턴하는 함수를 sort() 메서드의 인자로 전달하여,  
배열을 내림차순으로 정렬.  
오름차순으로 정렬할 때와 달리 compare 함수에서 b - a값을 리턴함.  
이때, 배열을 복사하여 정렬하는 것이 아니기 때문에 원본 배열도 정렬된다.

## 문자열 정렬하기

### 문자열 오름차순으로 정렬하기

```javascript
const arr = ["B", "A", "D", "C"];
arr.sort(); // ['A', 'B', 'C', 'D']
```

문자열일 경우 sort() 메서드는 compare 함수를 생략했을 때  
문자열의 유니코드 순서에 따라 정렬되기 때문에  
문자열을 오름차순으로 정렬할 때에는 인자를 생략해도 된다.

### 문자열 내림차순으로 정렬하기

```javascript
const arr = ["B", "A", "D", "C"];
const result = arr.sort((a, b) => {
  if (a > b) return -1;
  if (a < b) return 1;
  return 0;
});

console.log(result); //['D', 'C', 'B', 'A']
```

문자열을 a - b 또는 b - a와 같이 - 연산자를 사용하여 숫자 정렬처럼 사용할 경우  
정상적으로 정렬이 되지 않으므로 비교 연산자를 사용해야 한다.

### 첫번째 글자의 코드넘버를 비교하여 오름차순 정렬하기

```javascript
const arr = ["B", "A", "D", "C"];
arr.slice().sort((a, b) => a[0].charCodeAt() - b[0].charCodeAt()); // ['A', 'B', 'C', 'D']
```

### 첫번째 글자의 코드넘버를 비교하여 내림차순 정렬하기

```javascript
const arr = ["B", "A", "D", "C"];
arr.slice().sort((a, b) => b[0].charCodeAt() - a[0].charCodeAt()); // ['D', 'C', 'B', 'A']
```

### 사전순으로 오름차순 정렬하기

```javascript
const arr = ["B", "A", "D", "C"];
arr.slice().sort((a, b) => a.localeCompare(b)); // ['A', 'B', 'C', 'D']
```

### 사전순으로 내림차순 정렬하기

```javascript
const arr = ["B", "A", "D", "C"];
arr.slice().sort((a, b) => b.localeCompare(a)); // ['D', 'C', 'B', 'A']
```

## 문자열 대소문자구분 없이 정렬하기

```javascript
const arr = ["banana", "b", "B"];
arr.sort(); //['B', 'b', 'banana']
```

대소문자가 섞여있는 경우 sort() 메서드를 사용하여 정렬하면  
유니코드로 정렬 시 대문자가 소문자보다 앞서기 때문에  
대문자가 소문자보다 앞에 오도록 정렬된다.

### 문자열 오름차순으로 정렬하기(대소문자 구분 없이)

```javascript
const arr = ["banana", "b", "B"];
arr.sort(function (a, b) {
  const upperCaseA = a.toUpperCase();
  const upperCaseB = b.toUpperCase();

  if (upperCaseA > upperCaseB) return 1;
  if (upperCaseA < upperCaseB) return -1;
  if (upperCaseA === upperCaseB) return 0;
});

console.log(arr); //['b', 'B', 'banana']
```

sort() 메서드의 compare 함수에서 문자열을 비교할 때  
`문자열을 모두 대문자로 변환하여 비교`

toUpperCase() 메서드는 문자열을 대문자로 변환해 반환한다.

### 문자열 내림차순으로 정렬하기(대소문자 구분 없이)

```javascript
const arr = ["banana", "b", "B"];
arr.sort(function (a, b) {
  const upperCaseA = a.toUpperCase();
  const upperCaseB = b.toUpperCase();

  if (upperCaseA < upperCaseB) return 1;
  if (upperCaseA > upperCaseB) return -1;
  if (upperCaseA === upperCaseB) return 0;
});

console.log(arr); //['banana', 'b', 'B']
```

오름차순과 구문은 비슷하지만 연산자를 반대로 비교하여  
내림차순으로 정렬한다.

## 객체로 구성된 배열 정렬하기

배열의 객체 요소들을 정렬하기 위해서는  
객체 내의 속성을 키(key)로 잡고 어떤 기준으로 정렬할지 지정해야 한다.

### 가격순 오름차순으로 정렬하기

```javascript
const fruits = [
  { name: "apply", price: 1000 },
  { name: "banana", price: 2000 },
  { name: "pear", price: 4000 },
  { name: "lemon", price: 3000 },
];

const result = fruits.sort((a, b) => a.price - b.price);
console.log(result);
/*
  {name: 'apply', price: 1000}
  {name: 'banana', price: 2000}
  {name: 'lemon', price: 3000}
  {name: 'pear', price: 4000}
*/
```

`fruits.sort((a, b) => a.price - b.price)`  
price값을 기준으로 오름차순으로 정렬.

### 가격순 내림차순으로 정렬하기

```javascript
const fruits = [
  { name: "apply", price: 1000 },
  { name: "banana", price: 2000 },
  { name: "pear", price: 4000 },
  { name: "lemon", price: 3000 },
];

const result = fruits.sort((a, b) => b.price - a.price);
console.log(result);
/*
  {name: 'pear', price: 4000}
  {name: 'lemon', price: 3000}
  {name: 'banana', price: 2000}
  {name: 'apply', price: 1000}
*/
```

`fruits.sort((a, b) => b.price - a.price)`  
price값을 기준으로 내림차순으로 정렬.

### 이름순 오름차순 정렬하기

```javascript
const fruits = [
  { name: "apply", price: 1000 },
  { name: "banana", price: 2000 },
  { name: "pear", price: 4000 },
  { name: "lemon", price: 3000 },
];

const result = fruits.sort((a, b) =>
  a.name.toLowerCase() < b.name.toLowerCase() ? -1 : 1
);
console.log(result);
/*
  {name: 'apply', price: 1000}
  {name: 'banana', price: 2000}
  {name: 'lemon', price: 3000}
  {name: 'pear', price: 4000}
*/
```

`fruits.sort((a, b) => a.name.toLowerCase() < b.name.toLowerCase() ? -1 : 1)`  
name값을 기준으로 오름차순으로 정렬.

### 이름순 내림차순 정렬하기

```javascript
const fruits = [
  { name: "apply", price: 1000 },
  { name: "banana", price: 2000 },
  { name: "pear", price: 4000 },
  { name: "lemon", price: 3000 },
];

const result = fruits.sort((a, b) =>
  a.name.toLowerCase() > b.name.toLowerCase() ? -1 : 1
);
console.log(result);
/*   
  {name: 'apply', price: 1000}
  {name: 'banana', price: 2000}
  {name: 'lemon', price: 3000}
  {name: 'pear', price: 4000}
*/
```

`fruits.sort((a, b) => a.name.toLowerCase() > b.name.toLowerCase() ? -1 : 1)`

name값을 기준으로 내림차순으로 정렬.
