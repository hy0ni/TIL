> Array(배열)

- [배열이란?](#배열이란)
- [배열 만들기](#배열-만들기)
- [배열 요소 접근과 수정](#배열-요소-접근과-수정)
- [다중 배열](#다중-배열)
  - [2차원 배열이란?](#2차원-배열이란)
  - [2차원 배열 요소에 접근하기](#2차원-배열-요소에-접근하기)
  - [2차원 배열 요소 변경하기](#2차원-배열-요소-변경하기)
- [배열의 개수 알아내기(배열 길이)](#배열의-개수-알아내기배열-길이)

## 배열이란?

자바스크립트에서 배열(Array)은 여러 개의 값을 하나의 변수에 저장할 수 있는 데이터 구조입니다. 배열을 사용하면 같은 변수에 관련된 데이터들을 그룹화하여 관리할 수 있습니다.

## 배열 만들기

배열은 대괄호로 구성되며 쉼표로 구분된 항목들을 포함합니다.

1. 리터럴 표기법

```javascript
const fruits = ["apple", "banana", "cherry"];
```

2. Array 생성자

```javascript
const fruits = new Array("apple", "banana", "cherry");
```

fruits라는 배열이 생성되었으며,  
배열 안에는 "apple", "banana", "cherry"라는 세 개의 문자열이 포함되어 있습니다.

문자열 외에도 다양한 데이터 유형을 배열에 저장할 수 있습니다.  
(문자열, 숫자, 객체, 다른 변수, 심지어 다른 배열)

```javascript
const users = []; // empty array
const grades = [10, 8, 13, 15]; // array of numbers
const attendees = ["Sam", "Alex"]; // array of strings
const values = ["tree", 795, false, [0, 1, 2]]; // mixed
```

<b>배열은 여러 항목을 포함할 수 있으므로 복수형으로 이름을 지정합니다.  
이는 배열을 반복해야 할 때 특히 유용할 것입니다.</b>

## 배열 요소 접근과 수정

배열의 각 요소는 인덱스(번호)를 통해 접근할 수 있습니다.  
배열의 인덱스는 0부터 시작합니다.

```javascript
const fruits = ["apple", "banana", "cherry"];
```

```javascript
console.log(fruits[0]); // "apple"
console.log(fruits[1]); // "banana"
console.log(fruits[2]); // "cherry"
```

인덱스가 0부터 시작하는 대괄호 구문 []을 사용하여 배열에서 요소를 가져올 수 있습니다.

단일 배열 항목에 새 값을 제공하여, 배열의 항목을 수정할 수도 있습니다.

```javascript
const fruits = ["apple", "banana", "cherry"];
fruits[0] = "mango";

console.log(fruits[0]); // "mango"
console.log(fruits); // ['mango', 'banana', 'cherry']
```

위 코드처럼 단일 배열 항목에 새로운 값을 넣으면 기존 배열이 변경됩니다.

## 다중 배열

다중 배열(Multidimensional Array)은 배열 안에 배열이 포함된 구조입니다.  
쉽게 말해, 배열의 요소 중 일부가 또 다른 배열인 경우입니다.  
예를 들어, 표(table)처럼 데이터를 정리할 수 있습니다.

### 2차원 배열이란?

2차원 배열은 배열의 요소가 또 다른 배열인 구조입니다.  
보통 행(row)과 열(column)로 데이터를 저장할 때 사용합니다.

```javascript
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];
```

위 코드는 3x3 크기의 2차원 배열입니다.  
여기서 matrix는 3개의 배열을 포함하는 배열입니다.  
각 내부 배열은 3개의 숫자를 포함하고 있습니다.

### 2차원 배열 요소에 접근하기

2차원 배열의 요소에 접근하려면 두 개의 인덱스를 사용합니다.  
(array[행(row)][열(column)] 형태로 접근할 수 있습니다.)  
첫 번째 인덱스는 행을 가리키고, 두 번째 인덱스는 그 행의 열을 가리킵니다.

```javascript
const matrix = [
  [1, 2, 3], // 첫 번째 행 index 0
  [4, 5, 6], // 두 번째 행 index 1
  [7, 8, 9], // 세 번째 행 index 2
  // 0  1  2
];

console.log(matrix[1][1]); // 5
```

위 예제는 숫자 5에 접근하기 위한 코드입니다.  
여기서 matrix[1]은 [4, 5, 6] 행을 가리키고, 다시 [4, 5, 6][1]이 5를 가리킵니다.

### 2차원 배열 요소 변경하기

2차원 배열의 특정 요소를 변경하는 것도 같은 방식입니다.

```javascript
matrix[1][1] = 99; // [4, 5, 6]이 [4, 99, 6]로 변경됩니다
```

## 배열의 개수 알아내기(배열 길이)

.length 속성을 사용하여 배열의 요소 수를 얻을 수 있습니다.

```javascript
const fruits = ["apple", "banana", "cherry"];
console.log(fruits.length); //3
```

<span style="background-color:#f7ddbe;padding:.2rem">.length는 함수가 아니라 속성(미리 계산된 값)입니다. 그렇기 때문에 뒤에 ()를 붙이면 안 됩니다.</span>

