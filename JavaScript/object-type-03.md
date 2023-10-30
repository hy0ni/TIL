# Set 객체를 배열(Array)로 변환하기 (3가지 방법)

`Set 객체`는 중복을 허용하지 않는 유일한 값들의 데이터를 표현한다.

- Array.from()
- Spread Operator (전개 연산자)
- forEach

## Array.from()

Array.from() 함수는 반복 가능 객체 또는 유사 배열 객체에서 얕은 복사된 새 Array 인스턴스를 만든다.

`유사 배열 객체(array-like object)` : length 속성과 index element를 가지는 객체  
`반복 가능 객체(iterable object) `: 배열을 일반화한 객체 ex)Map, Set

```javascript
const set = new Set([1, 2, 3]);
const arr = Array.from(set);

console.log(Array.isArray(arr)); // true
console.log(arr); // (3) [1, 2, 3]
```

Set 객체를 Array.from() 함수를 사용해 배열로 변환한 후,  
리턴 받은 값이 배열인지 Array.isArray() 함수를 사용하여 확인하고,  
리턴 받은 값(배열)을 출력한다.

## Spread Operator (전개 연산자)

Spread Operator는 ES6의 문법으로  
배열이나 문자열과 같이 반복 가능한 객체를 하나씩 펼쳐서 리턴한다.(전개)  
'`...`'과 같이 점 3개로 표시한다.

```javascript
const set = new Set([1, 2, 3]);
const arr = [...set];

console.log(Array.isArray(arr)); // true
console.log(arr); // (3) [1, 2, 3]
```

Spread Operator(전개 연산자) '...'을 사용하여 Set 객체의 값들을 하나씩 전개하여(꺼내서),  
새로운 배열의 원소로 넣어, arr 변수에 저장한다.

## forEach

```javascript
const set = new Set([1, 2, 3]);
const arr = [];

set.forEach((element) => {
  arr.push(element);
});

console.log(Array.isArray(arr)); // true
console.log(arr); // (3) [1, 2, 3]
```

forEach 반복문과 push() 함수를 사용해 Set 객체를 새로운 배열로 변환한다.
