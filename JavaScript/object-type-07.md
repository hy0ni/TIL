# 빈 객체 체크하기 (2가지 방법)

- [빈 객체 체크하기 (2가지 방법)](#빈-객체-체크하기-2가지-방법)
  - [Object.keys() 함수](#objectkeys-함수)
  - [lodash library 사용하기](#lodash-library-사용하기)

## Object.keys() 함수

```javascript
Object.keys(obj);
```

Object.keys() 함수는 주어진 객체의 속성 이름들을 일반적인 반복문과 동일한 순서로 순회되는 열거할 수 있는 배열로 반환한다.

```javascript
const obj1 = {};
const obj2 = { a: 12 };
const obj3 = "JS";

function isEmptyObj(obj) {
  if (obj.constructor === Object && Object.keys(obj).length === 0) {
    return true;
  }

  return false;
}

console.log(isEmptyObj(obj1)); // true
console.log(isEmptyObj(obj2)); // false
console.log(isEmptyObj(obj3)); // false
```

`obj.constructor === Object`<br>
데이터가 객체인지 체크하기 위해 constructor를 확인한다.

`Object.keys(obj).length === 0`<br>
Object.keys() 함수는 파라미터로 입력받은 객체의 key 목록을 배열로 리턴한다.<br>
만약 Object.keys()를 호출한 결과 배열의 길이가 0이면 비어있는 객체임을 확인할 수 있다.

## lodash library 사용하기

lodash 라이브러리를 이용할 수도 있다.

`lodash 라이브러리를 사용하기 위해서는 lodash 라이브러리를 다운로드하거나, CND으로 참조해야 한다.`<br>
👉 [lodash library](https://lodash.com/)

```javascript
const obj1 = {};
const obj2 = { a: 12 };
const obj3 = "JS";

function isEmptyObj(obj) {
  if (obj.constructor === Object && _.isEmpty(obj)) {
    return true;
  }
  return false;
}

console.log(isEmptyObj(obj1)); // true
console.log(isEmptyObj(obj2)); // false
console.log(isEmptyObj(obj3)); // false
```

`_.isEmpty()`<br>
lodash의 isEmpty() 함수는
object, collection, map, set이 비어있는지를 체크해 주는 함수다.

간단하게 이 lodash의 isEmpty() 함수를 사용할 수도 있다.
