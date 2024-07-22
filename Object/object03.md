> 객체(Object)

- [Object prototypes](#object-prototypes)
- [프로토타입 기반 언어?](#프로토타입-기반-언어)
- [프로토타입](#프로토타입)
- [프로토타입 체인](#프로토타입-체인)
- [프로토타입 객체 이해하기](#프로토타입-객체-이해하기)
  - [valueOf 메서드 호출](#valueof-메서드-호출)
    - [valueOf 메서드 기본 동작](#valueof-메서드-기본-동작)
    - [커스터마이징된 valueOf 메서드](#커스터마이징된-valueof-메서드)
    - [최상위 프로토타입:](#최상위-프로토타입)
  - [특정 객체의 프로토타입 객체에 접근하는 방법.](#특정-객체의-프로토타입-객체에-접근하는-방법)

## Object prototypes

자바스크립트에서는 객체를 상속하기 위하여 프로토타입이라는 방식을 사용합니다.

## 프로토타입 기반 언어?

자바스크립트는 흔히 프로토타입 기반 언어(protorype-based language)라 불립니다.  
모든 객체들이 메소드와 속성들을 상속 받기 위한 템플릿으로써 프로토타입 객체(prototype object)를 가진다는 의미입니다.

## 프로토타입

자바스크립트에서 객체는 속성과 메서드의 모음입니다.  
모든 객체는 또 다른 객체를 참조할 수 있는데, 이 참조되는 객체를 "프로토타입"이라고 합니다.  
프로토타입은 그 객체의 부모 객체로 볼 수 있으며, 해당 객체가 사용할 수 있는 속성과 메서드를 정의한 객체입니다.

```javascript
// 새로운 객체 생성
let person = {
  name: "Alice",
  age: 25,
  greet: function () {
    console.log`Hello, ${this.name}`;
  },
};

// 객체 메서드 호출
person.greet(); // Hello, Alice
```

person 객체는 greet라는 메서드를 가지고 있습니다.  
만약 person 객체에 존재하지 않는 속성이나 메서드를 호출하려고 하면,  
자바스크립트는 person객체의 프로토타입(부모 객체)을 찾아보게 됩니다.

## 프로토타입 체인

자바스크립트는 프로토타입 체인을 통해 객체를 검색합니다.
예를 들어, 어떤 객체에 원하는 속성이나 메서드가 없다면,
자바스크립트는 그 객체의 프로토타입을 계속해서 따라 올라가며 검색합니다.

```javascript
let animal = {
  eats: true,
};

let rabbit = {
  jumps: true,
};

rabbit.__proto__ = animal; // rabbit의 프로토타입을 animal로 설정

console.log(rabbit.eats); // true
console.log(rabbit.jumps); // true
```

rabbit 객체는 jumps 속성을 가지고 있지만, eats 속성은 없습니다.  
그러나 rabbit의 프로토타입인 animal 객체가 eats 속성을 가지고 있기 때문에  
rabbit.eats를 호출하면 true가 출력됩니다.

## 프로토타입 객체 이해하기

생성자 함수와 인스턴스
생성자 함수는 주로 대문자로 시작하는 이름을 사용하며, new키워드를 사용하여 인스턴스를 생성합니다.

```javascript
function Person(name, age, gender) {
  // 속성과 메소드 정의
  this.name = name;
  this.age = age;
  //...
}
```

Person이라는 생성자 함수를 만듭니다.
Person 생성자 함수는 name과 age라는 속성을 초기화합니다.

```javascript
// 새로운 인스턴스 생성
let alice = new Person("Alice", 25, "female");
let bob = new Person("Bob", 30, "man");

console.log(alice.name); // Alice
console.log(bob.age); // 30
```

new Person('Alice', 25)와 같이 new 키워드를 사용하여 Person의 인스턴스를 생성할 수 있습니다.
이렇게 생성된 alice와 bob은 각각 Person의 인스턴스입니다.

```javascript
console.log(alice.valueOf());
```

### valueOf 메서드 호출

기본적으로 자바스크립트의 모든 객체는 Object.prototype으로부터 <b>valueOf 메서드</b>를 상속받습니다.
이 메서드는 일반적으로 객체 자체를 반환하지만, 객체에 따라 다르게 정의될 수도 있습니다.

#### valueOf 메서드 기본 동작

```javascript
let person = {
  name: "Alice",
  age: 25,
};

console.log(person.valueOf()); // {name: 'Alice', age: 25}
```

person 객체는 valueOf 메서드를 호출하면 객체 자체를 반환합니다. 이는 기본 Object.prototype.valueOf 메서드의 동작입니다.

#### 커스터마이징된 valueOf 메서드

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}
let person1 = new Person("Alice", 25);
console.log(person1.valueOf()); // Person {name: 'Alice', age: 25}
```

1. 브라우저는 우선 person1 객체가 valueOf 메서드를 가지고 있는지 확인합니다.
2. person1 객체는 valueOf 메서드가 없으므로 프로토타입 객체(Person() 생성자의 프로토타입)에 valueOf 메서드가 있는지 확인합니다.
3. 여전히 없으므로 Person() 생성자의 프로토타입 객체의 프로토타입 객체(Object() 생성자의 프로토타입)가 valueOf 메서드를 가지고 있는지 체크합니다. 여기에 있으니 호출하며 끝납니다.

person1 ----> Person.prototype ----> Object.prototype

#### 최상위 프로토타입:

Person.prototype과 Object.prototype은 다릅니다.

모든 객체는 Object.prototype을 최상위 프로토타입으로 갖습니다. 이는 자바스크립트의 객체가 기본적으로 동일한 메서드와 속성을 사용할 수 있게 합니다.

Person.prototype은 Object.prototype을 상속받기 때문에 프로토타입 체인에 의해 Object.prototype에 정의된 메서드를 사용할 수 있습니다.

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

let person1 = new Person("Alice", 25);
```

여기서 Person은 생성자 함수입니다.  
Person을 통해 생성된 모든 객체는 Person.prototype을 상속받습니다.

1. Person.prototype:
   Person.prototype은 Person 생성자 함수의 프로토타입입니다. 이는 Person으로 생성된 모든 객체가 공유하는 프로토타입 객체입니다.

```javascript
console.log(Person.prototype); // Person {constructor: f}
```

2. Object.prototype:
   Object.prototype은 모든 자바스크립트 객체의 최상위 프로토타입입니다. 모든 객체는 궁극적으로 Object.prototype을 상속받습니다.

```javascript
console.log(Object.prototype); // { ... }
```

3. 프로토타입 체인:
   Person.prototype은 Object.prototype을 상속받습니다. 즉, Person.prototype 자체가 객체이기 때문에 Object.prototype을 프로토타입으로 가집니다. 이를 통해 Person으로 생성된 객체도 Object.prototype의 메서드를 사용할 수 있게 됩니다.

```javascript
console.log(Person.prototype.__proto__ === Object.prototype); // true
```

[Recap]

- Person.prototype과 Object.prototype은 다른 객체입니다.
- Person.prototype은 Person 생성자 함수로 생성된 객체가 상속받는 프로토타입입니다.
- Object.prototype은 모든 자바스크립트 객체가 상속받는 최상위 프로토타입입니다.
- Person.prototype은 Object.prototype을 상속받으므로, Person 생성자 함수로 생성된 객체는 Object.prototype의 메서드를 사용할 수 있습니다.

### 특정 객체의 프로토타입 객체에 접근하는 방법.

Object.getPrototypeOf(obj)는 자바스크립트에서 객체 obj의 프로토타입(즉, 내부 프로토타입 링크)을 반환하는 메서드입니다. 이는 객체가 직접 상속받는 프로토타입 객체를 제공합니다. 이 메서드는 ES5(ECMAScript 5)에서 도입되었으며, 객체의 프로토타입 체인을 이해하고 조작하는 데 유용합니다.

```javascript
console.log(Object.getPrototypeOf(person1)); // Person {constructor: f}
console.log(Object.getPrototypeOf(Person)); // ƒ () { [native code] }

let obj = { a: 1 };
console.log(Object.getPrototypeOf(obj)); // { ... }
```

자바스크립트의 프로토타입 체인과 객체의 상속 구조를 이해하는 데 Object.getPrototypeOf 메서드는 매우 유용합니다.
