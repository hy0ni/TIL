# for...of와 for...in의 차이점

`for...of`는 배열의 반복에서 사용되고,
`for...in`은 객체의 반복에서 사용된다.

```javascript
Object.prototype.objCustom = function () {};
Array.prototype.arrCustom = function () {};

let iterable = [3, 5, 7];
iterable.foo = "hello";

for (let i in iterable) {
  console.log(i);
  // output: 0, 1, 2, "foo", "arrCustom", "objCustom"
}

for (let i of iterable) {
  console.log(i);
  // output: 3, 5, 7
}
```

모든 객체는 objCustom 프로퍼티를 상속받고,
Array인 모든 객체는 arrCustom 프로퍼티를 상속받는다.<br>
iterable 객체는 상속과 프로토타입 체인의 영향으로 objCustom과 arrCustom 프로퍼티 둘 다 상속받는다.

`for...in`문은 임의의 순서로 iterable 객체의 열거 가능한 프로퍼티만 출력한다.<br>
Array 요소인 3, 5, 7이나 "hello"는 프로퍼티가 아니라 값이기 때문에 열거 가능한 프로퍼티가 아니므로 출력하지 않는다.

`for...of`문은 iterable 객체가 iterable이 반복하도록 정의한 값을 반복하고 출력한다.
객체의 property는 출력되지 않고, Array의 요소인 3, 5, 7만 출력된다.
