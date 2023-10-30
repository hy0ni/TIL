# 객체에 특정 속성이 존재하는지 체크하기 (3가지 방법)

- [객체에 특정 속성이 존재하는지 체크하기 (3가지 방법)](#객체에-특정-속성이-존재하는지-체크하기-3가지-방법)
  - [hasOwnProperty() 함수](#hasownproperty-함수)
  - [in 연산자 사용하기](#in-연산자-사용하기)
  - [hasOwnProperty()와 in 연산자 차이점](#hasownproperty와-in-연산자-차이점)
  - [undefined와 비교하기](#undefined와-비교하기)
    - [undefined와 비교시 주의할 점](#undefined와-비교시-주의할-점)

## hasOwnProperty() 함수

`Object.prototype.hasOwnProperty()`

```javascript
hasOwnProperty(prop);
```

hasOwnProperty() 함수는 Object 개체가 지정된 속성을 자체 속성으로 갖고 있는지(상속하는 것이 아니라) 여부를 나타내는 boolean 값을 반환합니다.

```javascript
const person = {
  name: "hyoni",
  country: "korea",
};

console.log(person.hasOwnProperty("name")); // true
console.log(person.hasOwnProperty("age")); // false
```

파라미터로 전달된 property(속성)가 객체에 존재하면 true를 리턴하고,  
그렇지 않으면 false를 리턴한다.

## in 연산자 사용하기

```javascript
속성 in 객체명;
```

in 연산자는 명시된 속성이 명시된 객체에 존재하면 true를 반환한다.

```javascript
const person = {
  name: "hyoni",
  country: "korea",
};

console.log("name" in person); // true
console.log("age" in person); // false
```

in 연산자도 hasOwnProperty() 함수와 비슷하게 객체에 프로퍼티가 있으면 true를 리턴하고,  
그렇지 않으면 false를 리턴한다.

## hasOwnProperty()와 in 연산자 차이점

```javascript
const person = {
  name: "hyoni",
  country: "korea",
};

console.log(person.hasOwnProperty("toString")); // false
console.log("toString" in person); // true
```

`toString` 메서드는 모든 객체가 공통적으로 가지는 속성이다.  
`hasOwnProperty()` 함수는, 객체로부터 상속받은 속성을 체크하면 false를 리턴한다.  
`in 연산자`의 경우, toString과 같이 객체로부터 상속받은 속성을 체크하면 true를 리턴한다.

## undefined와 비교하기

```javascript
const person = {
  name: "hyoni",
  country: "korea",
};

console.log(person.name !== undefined); // true
console.log(person.age !== undefined); // false
```

'person.age'와 같이, 객체에 존재하지 않는 속성(property)에 접근하면 undefined가 리턴된다.  
이런 특징을 이용해서, 객체에 특정 속성이 존재하는지를 체크할 수 있다.

### undefined와 비교시 주의할 점

```javascript
const person = {
  name: "hyoni",
  country: "korea",
  age: undefined,
};

console.log(person.age !== undefined); // false
```

person 객체에 age 속성이 존재하지만, 그 값이 undefined로 정의되어 있을 경우  
person.age를 undefined 값과 비교하면 true를 리턴한다.

person 객체에 age 속성이 존재하지만, 속성값이 undefined이기 때문에,  
위 코드에서는 마치 age 속성이 존재하지 않는 것과 같은 결과를 얻게 된다.
