# 코딩 컨벤션 가이드

**코딩 컨벤션은 읽고, 관리하기 쉬운 코드를 작성하기 위한 일종의 코딩 스타일 규약**이다.<br>
특히 자바스크립트는 다른 언어에 비해 유연한 문법구조(동적 타입, this 바인딩, 네이티브 객체 조작 가능)를 가지기 때문에 통일된 규약이 없다면 코드의 의도를 파악하거나 오류를 찾기 어렵다.<br> 코딩 컨벤션을 준수하면 가독성이 좋아지고, 성능에 영향을 주거나 오류를 발생시키는 잠재적 위험 요소를 줄여준다. 특히 규모가 큰 프로젝트일수록 유지 보수 비용을 줄이는 데 도움이 된다.

- [코딩 컨벤션 가이드](#코딩-컨벤션-가이드)
  - [들여쓰기](#들여쓰기)
  - [문장의 종료](#문장의-종료)
  - [명명 규칙](#명명-규칙)
  - [전역 변수](#전역-변수)
  - [선언과 할당](#선언과-할당)
    - [변수](#변수)
    - [배열과 객체](#배열과-객체)
    - [함수](#함수)
    - [화살표 함수](#화살표-함수)
    - [Promise Executor 함수](#promise-executor-함수)
    - [Destructuring](#destructuring)
    - [템플릿 문자열](#템플릿-문자열)
  - [클래스와 생성자](#클래스와-생성자)
  - [모듈](#모듈)
  - [블록 구문](#블록-구문)
  - [조건 확인하기](#조건-확인하기)
  - [반환하기](#반환하기)
  - [순회하기](#순회하기)
  - [콜백 함수의 스코프](#콜백-함수의-스코프)
  - [주석](#주석)
  - [공백](#공백)

## 들여쓰기

**space와 tab을 섞어서 사용하지 않는다.**

사용하는 개발 환경에 따라 탭 or 스페이스의 들여 쓰기가 다르게 보일 수 있어 이를 통일하지 않으면 가독성이 떨어진다. 따라서 프로젝트 시작 시 반드시 공백 문자와 탭 문자 둘 중 하나를 선택해야 한다.
공백 문자를 사용할 경우 공백 문자 2개를 사용한다.

## 문장의 종료

**한 줄에 하나의 문장만 허용하며, 문장 종료 시에는 반드시 세미콜론(;)을 사용한다.**

## 명명 규칙

**카멜 케이스**을 사용하며 **예약어**를 사용하지 않는다.

대표적인 표기법으로 카멜 케이스, 파스칼 표기법, 헝가리안 표기법, 스네이크 표기법이 있다.

```javascript
// Bad
let class;
let const;
let import;
```

**상수: 영문 대문자 스네이크 표기법(Snake case) 사용.** <br>

```javascript
SYMBOLIC_CONSTANTS;
```

**생성자: 대문자 카멜 케이스을 사용.**

```javascript
class ConstructorName {
  ...
};
```

**변수, 함수: 카멜 케이스 사용.**<br>
DOM요소를 담을 변수일 경우 변수명 앞에 달러($)표시

```javascript
// 숫자, 문자, 불리언
let dog;
let variableName;

// 배열: 배열은 복수형 이름 사용
const dogs = [];

// 정규표현식: 정규표현식은 'r'로 시작
const rDesc = /.*/;

// 함수
function getPropertyName() {
  ...
}

// 이벤트 핸들러: 이벤트 핸들러는 'on'으로 시작
const onClick = () => {};
const onKeyDown = () => {};

// 불리언 반환 함수 - 반환 값이 불리언인 함수는 'is'로 시작
let isAvailable = false;
```

**(지역 변수 or private 변수)명은 '\_'로 시작한다.**

```javascript
let _privateVariableName;
let _privateFunctionName;

// 객체일 경우
const customObjectName = {};
customObjectName.propertyName;
customObjectName._privatePropertyName;
_privateCustomObjectName;
_privateCustomObjectName._privatePropertyName;
```

**URL, HTML 같은 범용적인 대문자 약어는 대문자 그대로 사용한다.**

```javascript
parseHTML;
parseXML;
```

## 전역 변수

**전역 변수를 사용하지 않는다.**

자바스크립트는 전역 변수에 기반을 둔다. 즉, 모든 컴파일 단위는 하나의 공용 전역 객체(window)에 로딩된다. 전역 변수는 언제든지 프로그램의 모든 부분에서 접근할 수 있기 때문에 편하지만, 바꿔 말하면 프로그램의 모든 부분에서 변경될 수 있고, 그로 인해 프로그램에 치명적인 오류를 발생시킬 수 있다.

```javascript
// Bad
myglobal = "hello";
```

**암묵적 전역 변수를 사용하지 않는다.**

```javascript
// Bad
function sum(x, y) {
  result = x + y;
  return result;
}
// Bad
function foo() {
  let a = (b = 0); // let a = (b = 0);와 같다. b가 암묵적 전역이 된다.
}

// Good
function sum(x, y) {
  let result = x + y;
  return result;
}
// Good
function foo() {
  let a, b;
  a = b = 0;
}
```

전역 변수를 피하기 위한 방법으로는 IIFE(immediately invoked function expression) 즉시 실행 함수를 사용할 수도 있다.
함수를 선언함과 동시에 즉시 실행하여 함수의 지역을 생성하고, 함수 안에 선언된 변수들은 함수의 지역 안에 생성된 지역변수가 된다.<br>
외부에서는 함수 안 변수에 접근할 수 없으며, 변수의 중첩, 재할당 등 전역변수의 문제를 피해 갈 수 있다.

## 선언과 할당

### 변수

**값이 변하지 않는 변수는 const를, 값이 변하는 변수는 let을 사용하여 선언한다.**<br>**var는 절대로 사용하지 않도록 한다.**

const를 우선하여 선언하면 "이 변수는 결코 재 할당되지 않습니다"라고 알려줌으로써 코드를 읽기 쉽게 하여 유지보수에 도움이 된다.<br>
let은 블록 범위로 할당되기 때문에 다른 많은 프로그래밍 언어에서와 같은 규칙으로 적용되어 실수를 피하는데 도움이 된다.

**const를 let 보다 위에 선언**하면 코드가 정리되어 가독성이 좋아진다.

```javascript
// Bad - 그룹화 없음
let foo;
let i = 0;
const $input;
let bar;

// Good
const $input;
let i = 0;
let foo, bar;
```

**const와 let은 사용 시점에 선언 및 할당을 한다.**

const와 let으로 선언한 변수는 블록 스코프이므로 호이스팅(hoisting) 되지 않는다.

```javascript
// Bad - 블록 스코프 밖에서 변수 선언
function foo() {
  const len = this._array.length;
  let i = 0;
  let j = 0;
  let len2, item;

  for (; i < len; i++) {
      ...
  }

  len2 = this._array2.length;
  for (j = 0, j < len2; j++) {
      item = this._array2[j];
      ...
  }
}


// Good
function foo() {
  const len = this._array.length;
  for (let i = 0; i < len; i++) {
      ...
  }

  // 사용 시점에 선언 및 할당
  const len2 = this._array2.length;
  for (let j = 0; j < len2; j++) {
      const item = this._array2[j];
      ...
  }
}
```

### 배열과 객체

**배열과 객체는 반드시 리터럴로 선언한다.**

리터럴 표기법은 생성자 함수보다 짧고 명확하며 실수를 줄일 수 있다.

```javascript
// Bad - 배열 생성자 사용
const emptyArr = new Array();
const arr = new Array(1, 2, 3, 4, 5);

// Good
const emptyArr = [];
const arr = [1, 2, 3, 4, 5];

// Bad - 객체 생성자 사용
const emptyObj = new Object();
const obj = new Object();

// Good
const emptyObj = {};
const obj = {
  pro1: "val1",
  pro2: "val2",
};
```

**배열 복사 시 순환문을 사용하지 않는다.**

복잡한 객체를 복사할 때 전개 연산자를 사용하면 좀 더 명확하게 정의할 수 있고 가독성이 좋아진다.

```javascript
const len = items.length;
let i;

// Bad
for (i = 0; i < len; i++) {
  itemsCopy[i] = items[i];
}

// Good
const itemsCopy = [...items];
```

**배열의 시작 괄호 안에 요소가 줄 바꿈으로 시작되었다면 끝 괄호 이전에도 일관된 줄 바꿈 해야한다.**

일관된 줄 바꿈 스타일은 협업 개발자 간 코드 가독성을 높혀준다.

```javascript
// Bad
let a = [1];

// Good
let a = [1];
```

**배열의 요소중 하나라도 줄 바꿈이 있다면 배열 안의 요소는 일관되게 모두 줄 바꿈을 해주어야 한다.**

```javascript
// Bad
const a = [1, 2, 3];
const b = [
  function foo() {
    dosomething();
  },
  function bar() {
    dosomething();
  },
];

// Good
const a = [1, 2, 3];
const b = [1, 2, 3];
```

**객체의 프로퍼티가 1개인 경우에만 한 줄 정의를 허용하며, 2개 이상일 경우에는 개행을 강제한다.**

```javascript
// Bad - 개행
const obj = { foo: "a", bar: "b" };

// Good
const obj = { foo: "a" };

// Good
const obj = {
  foo: "a",
};
```

**객체 리터럴 정의 시 콜론 앞은 공백을 허용하지 않으며 콜론 뒤는 항상 공백을 강제한다.**

```javascript
// Bad
let obj = {
  foo: "a",
};

// Good
let obj = {
  foo: "a",
};
```

**객체의 메서드 표현 시 축약 메소드 표기를 사용한다.**

복잡한 객체 리터럴을 보다 명확하게 정의할 수 있다.

```javascript
// Bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// Good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

**메서드 문법 사용 시 메서드 사이에 개행을 추가한다.**

```javascript
// Bad
class MyClass {
  foo() {
    //...
  }
  bar() {
    //...
  }
}

// Good
class MyClass {
  foo() {
    //...
  }

  bar() {
    //...
  }
}
```

### 함수

**함수 생성자를 사용하여 선언하지 않는다.**

문자열로 전달되는 파라미터가 수행 시점에 eval(evaluate의 약자로,문자열이 코드라고 가정하고 평가해서 실행됨)로 처리되어 실행 속도가 느려진다.

```javascript
// Bad - 함수 생성자 사용
const doSomething = new Function("param1", "param2", "return param1 + param2;");

// Good - 함수 선언식 사용
function doSomething(param1, param2) {
  return param1 + param2;
}

// Good - 함수 표현식 사용
const doSomething = function (param1, param2) {
  return param1 + param2;
};
```

**함수는 사용 전에 선언해야 하며, 함수 선언문은 변수 선언문 다음에 오도록 한다.**

함수 표현식으로 생성된 함수는 호이스팅 시 값이 할당되지 않으므로 선언 이전에 사용하면 오류가 발생한다.

```javascript
// Bad - 선언 이전에 사용
const sumedValue = sum(1, 2);
const sum = function (param1, param2) {
  return param1 + param2;
};

// Bad - 선언 이전에 사용
const sumedValue = sum(1, 2);
function sum(param1, param2) {
  return param1 + param2;
}

// Good
const sum = function (param1, param2) {
  return param1 + param2;
};
const sumedValue = sum(1, 2);
```

즉시 실행 함수는 권장되는 패턴으로만 사용한다.
즉시 실행 함수에서 사용하는 괄호는 여러가지 형태로 표현할 수 있지만 혼란을 줄 수 있음으로 아래와 같이 한 가지 스타일로 작성한다.

```javascript
// Bad
(function() {
  ...
})();

// Good
(function() {
  ...
}());
```

### 화살표 함수

**함수 표현식 대신 화살표 함수를 사용한다.**

화살표 함수는 별도의 this 바인딩 없이 상위 컨텍스트에 바인딩되기 때문에 함수 표현식보다 혼란이 적으며 덜 장황하고 추론이 쉽다.

```javascript
// Bad
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// Good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

**화살표 함수의 파라미터가 하나이면 괄호를 생략한다.**

파라미터가 하나일 때 괄호를 생략하면 화살표 함수의 장점을 살릴 수 있다.

```javascript
// Bad
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});

// Good
[1, 2, 3].map((x) => x * x);

// Good
[1, 2, 3].reduce((y, x) => x + y);
```

**암시적 반환을 최대한 활용한다.**

함수의 본체가 하나의 표현식이면 중괄호를 생략하고 암시적 반환을 사용할 수 있다.<br>
그 외에는 return문을 명시해야 한다.

```javascript
// Bad
[1, 2, 3].map((number) => {
  const nextNumber = number + 1;
  `A string containing the ${nextNumber}.`;
});

// Good - 암시적 return을 사용
[1, 2, 3].map((number) => `A string containing the ${number + 1}.`);
```

**암시적 반환을 사용할 경우 함수 본문 전에 개행을 하지 않는다.**

실수로 인한 return문 누락과 암시적 반환을 판단하는데 혼란을 피할 수 있다.

```javascript
// Bad
(foo) => bar;

(foo) => bar;

(foo) => (bar) => baz;

// Good
(foo) => bar;

(foo) => bar;

(foo) => (bar) => baz;

(foo) => bar();
```

### Promise Executor 함수

**Promise Executor 함수에 async 함수를 사용하지 않는다.**

비동기 Excutor 함수가 throw한 오류를 잡을 수 없고, Promise가 reject되지 않아 디버깅이 어렵다.

```javascript
// Bad
const result = new Promise(async (resolve, reject) => {
  resolve(await foo);
});

// Good
const result = new Promise((resolve, reject) => {
  readFile("foo.txt", function (err, result) {
    if (err) {
      reject(err);
    } else {
      resolve(result);
    }
  });
});
```

### Destructuring

**오브젝트의 프로퍼티에 접근할 때는 Destructuring을 이용한다.**

오브젝트에서 필요한 값만을 추출하여 변수에 할당하는 방법은 직관적이며 코드를 이해하기 쉬어진다.

```javascript
// Bad
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;

  return `${firstName} ${lastName}`;
}

// Good
function getFullName(obj) {
  const { firstName, lastName } = obj;

  return `${firstName} ${lastName}`;
}

// Bad
const first = arr[0];
const second = arr[1];

// Good
const [first, second] = arr;

// Good
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}
```

**새로운 이름으로 변수에 할당 할 때는 꼭 Destructuring을 사용하지 않아도 된다.**

```javascript
// Good
const changeFirstName = user.firstName;

// Good
const { firstName: changeFirstName } = user;
```

### 템플릿 문자열

**변수 등을 조합해서 문자열을 생성하는 경우 템플릿 문자열을 이용한다.**

자바스크립트에서 문자열을 보다 쉽고 명확하게 다룰 수 있어 코드 복잡도가 낮아진다.

```javascript
// Bad
function sayHi(name) {
  return "How are you, " + name + "?";
}

// Good
function sayHi(name) {
  return `How are you, ${name}?`;
}

// Bad - 일반적인 경우, 홑따옴표를 사용
function sayHi(name) {
  return `How are you name?`;
}

// Good
function sayHi(name) {
  return "How are you name?";
}
```

## 클래스와 생성자

**class와 extends를 이용해서 객체 생성 및 상속을 구현한다.**

prototype기반으로 상속을 구현한 것보다 문법이 훨씬 간단하다.

```javascript
// Bad
function Queue(contents = []) {
  this._queue = [...contents];
}
Queue.prototype.pop = function () {
  const value = this._queue[0];
  this._queue.splice(0, 1);
  return value;
};

// Good
class Queue {
  constructor(contents = []) {
    this._queue = [...contents];
  }
  pop() {
    const { value } = this._queue;
    this._queue.splice(0, 1);
    return value;
  }
}
```

**mixin을 제외하고 명시적으로 prototype을 호출하지 않는다.**

미리 약속한 방법으로만 객체를 확장하여 예측 가능한 코드가 되도록 한다.

```javascript
// Bad
const inherits = require("inherits");
function PeekableQueue(contents) {
  Queue.apply(this, contents);
}
inherits(PeekableQueue, Queue);
PeekableQueue.prototype.peek = function () {
  return this._queue[0];
};

// Good
class PeekableQueue extends Queue {
  peek() {
    return this._queue[0];
  }
}
```

## 모듈

**항상 import와 export를 이용한다.**

다른 모듈 로드 방법과 혼용하여 사용하면 코드의 일관성이 없어진다.

```javascript
// Best
import {es6} from './AirbnbStyleGuide';
export default es6;

// Bad
const AirbnbStyleGuide = require('./AirbnbStyleGuide');
module.exports = AirbnbStyleGuide.es6;

// Good
import AirbnbStyleGuide from './AirbnbStyleGuide';
export default AirbnbStyleGuide.es6;
```

**wildcard import는 사용하지 않는다.**

with문법을 지양해야 하는 것과 같은 이유로, 이름을 지정하지 않으면 모듈이 변경될 때마다 식별자 충돌이 발생할 수 있다.

```javascript
// Bad
import * from './AirbnbStyleGuide';

// Good
import * as AirbnbStyleGuide from './AirbnbStyleGuide';
```

**import문으로부터 직접 export하지 않는다.**

한 줄로 표현되어 간결하기는 하지만, import와 export 하는 방법을 명확하게 구분함으로써 일관성을 유지하자.

```javascript
// Bad
export { es6 as default } from "./airbnbStyleGuide";
```

## 블록 구문

**한 줄짜리 블록일 경우라도 {}를 생략하지 않으며 명확히 줄 바꿈 하여 사용한다.**

한 줄짜리 블록일 경우 {}를 생략할 수 있지만, 이는 코드 구조를 애매하게 만든다. 당장은 두 줄을 줄일 수 있겠지만 이후 오류 발생 확률이 높아 잠재된 위험 요소가 된다.

```javascript
// Bad
if(condition) doSomething();

// Bad
if (condition) doSomething();
else doAnything();

// Bad
for(let prop in object) someIterativeFn();

// Bad
while(condition) iterating += 1;

// Good
if (condition) {
  ...
}

// Good
if (condition) {
  ...
} else {
  ...
}
```

**키워드와 조건문 사이에 빈칸을 사용한다.**

키워드와 조건문 사이가 빼곡하면 코드를 읽기 어렵다.

```javascript
// Bad
let i = 0;
for (; i < 100; i += 1) {
  someIterativeFn();
}

// Good
let i = 0;
for (; i < 100; i += 1) {
  someIterativeFn();
}
```

**do-while문 사용 시 while문 끝에 세미콜론을 쓴다.**

```javascript
// Bad
do statement while(condition)

// Good
do {
  ...
} while (condition);
```

**switch-case 사용 시 첫 번째 case문을 제외하고 case문 사용 이전에 개행한다.**

```javascript
// Good
switch (value) {
  case 1:
    doSomething1();
    break;

  case 2:
    doSomething2();
    break;

  case 3:
    return true;

  default:
    throw new Error("This shouldn't happen.");
}
```

**switch-case 사용 시 각 구문은 `break`, `return`, `throw` 중 한 개로 끝나야 하며 default문이 없으면 `// no default` 표시를 해준다.**

여러 케이스가 하나의 기능을 한다면 `break`를 생략해도 좋지만, 조금이라도 다른 기능을 포함한다면 `break`를 생략하지 말고 다른 방식으로 코드를 수정한다.

```javascript
// Bad - 케이스 1 과 2 가 서로 다른 처리를 하지만 break가 생략됨
switch (value) {
  case 1:
    doSomething1();

  case 2:
    doSomething2();
    break;

  case 3:
    return true;

  // no default
}

// Bad - default문이 없지만 아무런 표기가 없음
switch (value) {
  case 1:
    doSomething1();
    break;

  case 2:
    doSomething2();
    break;

  case 3:
    return true;
}

// Good - 여러 케이스가 하나의 처리를 할 때는 break생략 허용
switch (value) {
  case 1:
  case 2:
    doSomething();
    break;

  case 3:
    return true;

  // no default
}
```

## 조건 확인하기

**삼중 등호 연산자인 ===, !==만 사용한다.**

==이나 !=는 암묵적 캐스팅으로 타입에 관계없이 판단되어 조건문의 의도를 파악하기 어렵고 버그로 이어진다.

```javascript
const numberB = 777;

// Bad
if (numberB == '777') {
  ...
}

// Good
if (numberB === 777) {
  ...
}
```

## 반환하기

**함수 내에서 반환은 한 번만 한다.**

특정 값을 반환해야 하는 경우, 함수 맨 마지막에서 한 번만 반환한다. 단, 예외로 빠져나가는 경우는 제외한다. 코드를 예측하기 쉬우며 흐름이 간결한 함수를 작성할 수 있다.

```javascript
// Bad
function getResult() {
  ...
  if (condition) {
    ...
    return someDataInTrue;
  }
  ...
  return someDataInFalse;
}

// Allow
function foo(isValid) {
  ...
  // 예외처리로 바로 빠져나감
  if (!isValid) {
    return;
  }
  ...

  return someDataInTrue;
}

// Good
function getResult() {
  let resultData;
  ...

  if (condition) {
    ...
    resultData = someDataInTrue;
  } else {
    ...
    resultData = someDataInFalse;
  }

  return resultData;
}
```

**return문 바로 위는 한 칸 비워 놓는다.**

다른 명령과 return문이 붙어있으면 가독성이 좋지 않으므로 return문 전에 한 줄 띄운다

```javascript
// Bad
function getResult() {
  ...
  return someDataInFalse;
}

// Good
function getResult() {
  ...

  return someDataInFalse;
}
```

## 순회하기

**반복문 사용은 일반화된 순회 메서드 사용을 권장한다.**

일반화된 순회 메서드를 사용하면 실수를 줄일 수 있다.

```javascript
// Good
let i, len
for (i = 0, len = array.length; i < len; i += 1) ...

// Good
[1, 2, 3].forEach(array, function(value, index) {
  ...
});
```

**for-in문 안에서는 hasOwnProperty 조건 검사를 수행한다**

예상치 않게 상속받은 프로퍼티로 인해 문제가 생길 수 있다.

```javascript
// Good
for (const prop in object) {
  if (object.hasOwnProperty(prop)) {
    ...
  }
}
```

## 콜백 함수의 스코프

**콜백 등 익명 함수를 사용하는 경우, 최대한 클로저 사용을 피하고 각 스코프에 알맞게 변수를 선언한다.**

꼭 필요하지 않은 클로저를 사용할 경우 스코프 체인의 참조가 늘어남으로 성능이 저하되고 가독성을 떨어뜨릴 수 있다.

```javascript
// bad
let data1, data2, ...;

forEach(arr, function() {
  data1 = someFunction1();
  data2 = someFunction2();
  ...
});

// Allow
function foo() {
  const length = ary.length;
  let i = 0;
    ...

  forEach(ary, function(data1, data2) {
    ...

    // 필요에 따라 외부에 변수 선언 가능 (클로저 사용 허용)
    i += (length + 2);
    ...
  });
}

// Good
function foo() {
  ...

  // 익명 함수의 스코프 안에서 변수 선언
  forEach(ary, function(data1, data2) {
    const data1 = someFunction1(data1);
    const data2 = someFunction2(data2);
  ...
  });
}
```

## 주석

**주석은 설명하려는 구문에 맞춰 들여쓰기 한다.**

```javascript
// Bad
function someFunction() {
  ...

// statement에 관한 주석
  statements
}

// Good
function someFunction() {
  ...

  // statement에 관한 주석
  statements
}
```

**문장 끝에 주석을 작성할 경우, 한 줄 주석을 사용하며 공백을 추가한다.**

```javascript
// Bad
let someValue = data1; //주석 표시 전후 공백

// Bad
let someValue = data1; /* 여러 줄 주석 */

// Good
let someValue = data1; // 주석 표시 전후 공백
```

**여러 줄 주석을 작성할 때는 \*의 들여쓰기를 맞춘다. 주석의 첫 줄과 마지막 줄은 비워둔다.**

```javascript
// Bad - '*' 표시의 정렬
/*
* 주석내용
*/

// Bad - 주석의 첫 줄에는 기술하지 않는다
...
/* let foo = '';
 * let bar = '';
 * let quux;
 */

// Good - '*' 표시의 정렬을 맞춘다
/*
 * 주석내용
 */
```

**코드 블럭 주석 처리를 위해서는 한 줄 주석을 사용한다.**

```javascript
// Bad - 여러 줄 주석을 사용
...
/*
 * let foo = '';
 * let bar = '';
 * let quux;
 */

// Good - 한 줄 주석 사용
...
// let foo = '';
// let bar = '';
// let quux;
```

## 공백

**키워드, 연산자와 다른 코드 사이에 공백이 있어야 한다.**

빼곡한 연산자와 키워드가 있는 코드는 읽기 어렵다.

```javascript
// Bad
let value;
if (typeof str === "string") {
  value = a + b;
}

// Good
let value;
if (typeof str === "string") {
  value = a + b;
}
```

**시작 괄호 바로 다음과 끝 괄호 바로 이전에 공백이 있으면 안 된다.**

```javascript
// Bad - 괄호 안에 공백
if ( typeof str === 'string' )

// Good
if (typeof str === 'string') {
  ...
}


// Bad - 괄호 안 공백
let arr = [ 1, 2, 3, 4 ];

// Good
let arr = [1, 2, 3, 4];
```

**콤마 다음에 값이 올 경우 공백이 있어야 한다.**

콤마로 구분된 아이템 간에 간격을 두면 가독성이 향상된다.<br>
콤마 바로 뒤에 공백을 추가한다.

```javascript
// Bad - 콤마 뒤 공백
let arr = [1, 2, 3, 4];

// Good
let arr = [1, 2, 3, 4];
```
