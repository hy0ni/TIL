# 객체 합치기 (3가지 방법)

- [객체 합치기 (3가지 방법)](#객체-합치기-3가지-방법)
  - [Object.assign()](#objectassign)
  - [Spread Operator (전개연산자)](#spread-operator-전개연산자)
  - [\_.merge (lodash 라이브러리)](#_merge-lodash-라이브러리)

## Object.assign()

```javascript
Object.assign(target, ...sources);
```

Object.assign() 함수는  
파라미터로 입력받은 sources 객체들의 속성을 target 객체로 복사한다.
이때, sources 객체는 1개 이상 여러 개 입력 가능.

```javascript
const obj = {
  name: "banana",
  price: 1000,
  count: 10,
};

const objCopy = {
  name: "banana",
  count: 100,
};

const newObj = Object.assign(obj, objCopy);

console.log(JSON.stringify(newObj)); // {"name":"banana","price":1000,"count":100}
console.log(JSON.stringify(obj)); // {"name":"banana","price":1000,"count":100}
console.log(JSON.stringify(objCopy)); // {"name":"banana","count":100}
```

`Object.assign(obj, objCopy)`  
objCopy에 모든 속성들을 obj에 복사한다.
이때, 같은 속성이 있으면 덮어쓴다.

source object의 속성이 겹치는 경우,
Object.assign() 함수의 파라미터로 `전달된 순서가 뒤인 객체의 값이 복사`된다.

Object.assign() 함수의 첫 번째 파라미터로 전달된 target 객체(obj)가 변경됨.

```javascript
const obj = {
  name: "banana",
  price: 1000,
  count: 10,
};

const objCopy = {
  name: "banana",
  count: 100,
};

const newObj = Object.assign({}, obj, objCopy);

console.log(JSON.stringify(newObj)); // {"name":"banana","price":1000,"count":100}
console.log(JSON.stringify(obj)); // {"name":"banana","price":1000,"count":10}
console.log(JSON.stringify(objCopy)); // {"name":"banana","count":100}
```

obj, objCopy 두 객체를 변경하지 않고, 두 객체를 병합하여 새로운 객체를 만들기 위해서는 target 객체 위치에 빈 객체{}를 전달하면 obj 객체와 objCopy 객체가 빈 객체에 복사되어 병합된다.

병합된 객체는 Object.assign() 함수의 리턴 값으로 리턴된다.

## Spread Operator (전개연산자)

```javascript
const obj = {
  name: "banana",
  price: 1000,
  count: 10,
};

const objCopy = {
  name: "banana",
  count: 100,
};

const newObj = { ...obj, ...objCopy };

console.log(JSON.stringify(newObj)); // {"name":"banana","price":1000,"count":100}
console.log(JSON.stringify(obj)); // {"name":"banana","price":1000,"count":10}
console.log(JSON.stringify(objCopy)); // {"name":"banana","count":100}
```

`const newObj = { ...obj, ...objCopy }`  
Spread Operator(전개 연산자)는 객체나 배열의 원소를 하나씩 펼쳐서 리턴한다.  
Spread Operator(전개 연산자)를 사용해서 여러개의 객체를 하나로 병합할 수 있다.

## \_.merge (lodash 라이브러리)

```javascript
const obj = {
  name: "Kim",
  tel: ["010-0000-0000", "010-2222-2222"],
};

const objCopy = {
  name: "Kim",
  address: "Seoul",
};

const newObj = { ...obj, ...objCopy };

console.log(JSON.stringify(newObj)); // {"name":"Kim","tel":["010-0000-0000","010-2222-2222"],"address":"Seoul"}

obj.tel.push("010-3333-3333");
console.log(JSON.stringify(newObj)); // {"name":"Kim","tel":["010-0000-0000","010-2222-2222","010-3333-3333"],"address":"Seoul"}
```

Spread Operator나 Object.assign을 이용해서 객체를 병합하면
Shallow Copy(얕은 복사)가 되면서 두 객체가 합쳐진다.

객체의 속성값이 Object(객체)이거나 Array와 같이 Reference Type일 경우에는  
해당 객체의 값이 복사되는게 아니라, 해당 객체를 참조하는 주소값을 복사하면서 두 객체를 병합하게 된다.  
(Reference Type이 아닌, 문자열이나 숫자 등은 주소값이 아닌 실제값이 복사된다.)

실제 값이 복사된 것이 아닌 주소값이 복사되었기 때문에  
obj.tel의 배열에 새로운 값을 추가했음에도  
두 객체의 병합으로 만들어진 newObj의 tel값도 같이 변경되었다.

이러한 현상을 피하고, 실제 값을 복사하고 싶은 경우 `lodash 라이브러리`의 `_.merge()` 함수를 이용할 수 있다.

```javascript
const obj = {
  name: "Kim",
  tel: ["010-0000-0000", "010-2222-2222"],
};

const objCopy = {
  name: "Kim",
  address: "Seoul",
};

const newObj = _.merge({}, obj, objCopy);

console.log(JSON.stringify(newObj)); // {"name":"Kim","tel":["010-0000-0000","010-2222-2222"],"address":"Seoul"}

obj.tel.push("010-3333-3333");
console.log(JSON.stringify(newObj)); // {"name":"Kim","tel":["010-0000-0000","010-2222-2222"],"address":"Seoul"}
```

`const newObj = _.merge({}, obj, objCopy)`  
lodash의 '\_.merge()' 함수는 Object.assign() 함수와 사용법이 비슷하다.  
첫 번째 파라미터로는 객체들이 병합될 target 객체를 입력하고,  
두 번째 파라미터부터는 병합될 source 객체들을 나열한다.

\_.merge() 함수를 이용하여 객체를 병합하니(newObj),  
obj1.tel의 배열에 새로운 값을 추가해도,  
newObj.tel의 배열 값이 변경되지 않는다.

👉[lodash library](https://lodash.com/)  
lodash 라이브러리를 사용하기 위해서는 lodash 라이브러리를 다운로드하거나, CND으로 참조해야 한다.
