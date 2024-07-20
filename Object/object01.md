> Object(객체)

- [객체란?](#객체란)
- [객체 생성](#객체-생성)
- [객체 프로퍼티에 접근하기](#객체-프로퍼티에-접근하기)
    - [\[점 표기법과 대괄호 표기법의 차이점\]](#점-표기법과-대괄호-표기법의-차이점)
- [하위 namespaces](#하위-namespaces)
- [객체 멤버 설정하기](#객체-멤버-설정하기)
  - [점 표기법이 동적 멤버 이름을 지원하지 않는 이유](#점-표기법이-동적-멤버-이름을-지원하지-않는-이유)

## 객체란?

자바스크립트에서 객체(Object)는 데이터를 구조화하고 저장하는데 사용되는 중요한 요소입니다.  
객체는 키(key)-값(value) 쌍으로 구성되어 있으며,
키는 문자열이고, 값은 다양한 데이터 타입을 가질 수 있습니다.

객체는 다른 객체를 포함할 수도 있고, 함수를 값으로 가질 수도 있습니다.  
객체의 key는 유일해야 하지만, value는 중복될 수 있습니다.

```javascript
const objectName = {
  key: value,
  key: value,
};
```

## 객체 생성

1. 객체 리터럴(object literal) 표기법  
   객체를 생성할 때 컨텐츠를 그대로 대입합니다.

```javascript
let person = {
  name: "John",
  age: 30,
  sayHello: function () {
    return `Hi! I'm ${this.name}`;
  },
};
```

1. Object 생성자 함수 사용

```javascript
let person = new Object();
person.name = "John";
person.age = 30;
person.sayHello = function () {
  return `Hi! I'm ${this.name}`;
};
```

## 객체 프로퍼티에 접근하기

1. 점 표기법 (Dot notation)  
   객체내에 캡슐화되어있는것에 접근하려면 먼저 점을 입력해야합니다. 그 다음 접근하고자 하는 항목을 적습니다.

```javascript
person.name; // "John"
person.age; // 30
person.sayHello(); // Hi! I'm John
```

2. 대괄호 표기법 (Bracket notation)

```javascript
console.log(person["name"]); // "John"
console.log(person["age"]); // 30
```

#### [점 표기법과 대괄호 표기법의 차이점]

점 표기법은 <span style="background-color:#f7ddbe;padding:.2rem">속성 이름이 유효한 자바스크립트 식별자일 때 사용</span>합니다. 여기에는 공백, 특수 문자, 숫자로 시작하는 이름이 포함되지 않습니다.

```javascript
let person = {
  name: "Alice",
  age: 30,
};

console.log(person.name); // "Alice"
console.log(person.age); // 30
```

<br/>

대괄호 표기법은 <span style="background-color:#f7ddbe;padding:.2rem">속성 이름이 문자열로 제공될 때 사용</span>합니다. 속성 이름에 공백이나 특수 문자가 포함되거나, 속성 이름이 변수로 동적으로 결정될 때 유용합니다.

```javascript
let propertyName = "name";
console.log(person[propertyName]); // "Alice"

let obj = {
  "first name": "Bob",
  "age!": 25,
};

console.log(obj["first name"]); // "Bob"
console.log(obj["age!"]); // 25
```

<b>Recap</b>

- 점 표기법: 코드가 간결하고 가독성이 좋습니다.  
  속성 이름이 고정된 경우 사용합니다.
- 대괄호 표기법: 속성 이름에 공백이나 특수 문자가 포함되거나 동적으로 속성 이름을 참조할 때 사용합니다.

## 하위 namespaces

다른 객체를 객체 멤버의 값으로 갖는 것도 가능합니다.

```javascript
let person = {
  name: ["Bob", "Smith"],
};
```

해당 코드를 아래와 같이 바꿔봅시다.

```javascript
let person = {
  name: {
    first: "Bob",
    last: "Smith",
  },
};
```

성공적으로 하위 namespace 를 만들었습니다.

객체의 속성이 바뀌었으니까, 기존 메서드 코드를 바꿔 줘야 합니다.

```javascript
console.log(person.name[0]);
console.log(person.name[1]);
```

아래와 같이 바꿔줍니다.

```javascript
console.log(person.name.first); // Bob
console.log(person.name.last); // Smith
```

## 객체 멤버 설정하기

"멤버"란 객체에 속하는 모든 속성(property)과 메서드(method)를 의미합니다.  
객체의 멤버는 객체가 가진 데이터(속성)와 객체가 수행할 수 있는 동작(메서드)을 포함합니다.

점이나 대괄호 표기법을 사용하여 객체 멤버의 값을 설정(갱신)하는 것도 가능합니다.

```javascript
let person = {
  name: {
    first: "Bob",
    last: "Smith",
  },
};
person.age = 45;
person["name"]["last"] = "Cratchit";

console.log(person.age);
console.log(person["name"]["last"]);
console.log(person);
```

객체 멤버를 설정하는 것은 단순히 기존에 존재하는 프로퍼티나 메서드로 값을 설정하는 것 뿐 아니라, 완전히 새로운 멤버를 생성할 수도 있습니다.

```javascript
person["eyes"] = "hezel";
person.farewell = function () {
  return "Bye";
};
console.log(person["eyes"]);
console.log(person.farewell());
```

대괄호 표현의 이점 중 하나는 멤버의 값을 동적으로 변경할 수 있을뿐아니라, 멤버 이름까지도 동적으로 사용할 수 있다는 것입니다.

<b>대괄호 표기법은 멤버 이름을 문자열로 지정하기 때문에 동적 멤버 이름을 사용할 수 있습니다.  
변수나 표현식을 사용하여 멤버 이름을 지정할 수 있습니다.</b>

```javascript
let data = {};
let key = "a";
let value = "b";
data[key] = value;

console.log(data[key]);
console.log(data); // { a: 'b' }
```

data객체에 새 멤버의 이름과 값을 추가하고,
data객체에 대괄호를 붙여 제대로 동작하는지 확인할 수 있습니다.

점 표기법을 사용할 경우 undefined가 리턴됩니다.  
점 표기법으로는 위의 예제처럼 멤버의 이름을 동적으로 사용할 수 없고, 상수 값만을 사용해야 합니다.  
즉, <b>객체의 프로퍼티 이름을 변수로 사용할 수 없습니다.</b>

```javascript
console.log(data.key); // undefined
```

### 점 표기법이 동적 멤버 이름을 지원하지 않는 이유

점 표기법은 멤버 이름을 정적으로 결정하는 것이 문법적으로 간단하고 명확하기 때문에 동적 멤버 이름을 지원하지 않습니다. 동적 멤버 이름을 지원하려면, 런타임(프로그램이 실행되는 동안 값이 결정된다)에 평가될 수 있는 문자열을 처리해야 하며, 이는 점 표기법의 간결함과 단순함을 해칩니다.
