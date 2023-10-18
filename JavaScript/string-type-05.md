# substring() & slice() 차이점

`substring()`과 `slice()`는 모두 시작 index와 끝 index를 인자로 받고 <br>
시작 index는 포함하고 끝 index는 포함하지 않는 문자열을 잘라 리턴한다.

## Syntax

```javascript
const str = "Hello World";

let a = str.substring(0, 5);
let b = str.slice(0, 5);

console.log(a); // "Hello"
console.log(b); // "Hello"
```

인자로 시작 index 0과 끝 index 5를 전달하면 index 0을 포함하고 5를 포함하지 않는 index 4까지의 문자열을 잘라서 리턴한다.

## 차이점: 시작 index가 끝 index보다 큰 경우 (start > end)

`start < end`일 때는 위와 같이 동일한 문자열을 리턴하지만,<br>
`start > end`일 때는 결과가 다름.

```javascript
const str = "Hello World";

let a = str.substring(5, 0);
let b = str.slice(5, 0);

console.log(a); // "Hello"
console.log(b); // ""
```

`substring()` 함수는 start > end일 때, start와 end의 위치를 바꿔서 결과를 계산한다.<br>
즉, substring(5, 0)은 substring(0, 5)으로 계산된다.

`slice()` 함수는 start > end일 때 빈 문자열('')을 리턴한다.

## 차이점 : 시작 index가 음수일 경우

시작 index가 음수일 경우 substring()과 slice()의 계산 결과가 달라진다.

`substring()` 함수는 start index가 음수일 때 0으로 변경되고,<br>
`slice()` 함수는 음수일 때 문자열 끝에서 앞쪽으로 음수만큼 이동된 index로 계산된다.

```javascript
const str = "Hello World";

let a = str.substring(-8, 10);
let b = str.slice(-8, 10);

console.log(a); // "Hello Worl"
console.log(b); // "lo Worl"
```

`substring(-8, 10)`<br>
substring(0, 10)로 계산된다.<br>

`slice(-8, 10)`<br>
slice(3, 10)로 계산된다.

## 차이점 : end index가 음수일 경우

```javascript
const str = "Hello World";

let a = str.substring(0, -2);
let b = str.slice(0, -2);

console.log(a); // ""
console.log(b); // "Hello Wor"
```

`substring()` 함수는 end index가 음수일 때 0으로 계산되며,<br>
`slice()` 함수는 문자열 끝에서 앞쪽으로 이동하며 위치를 찾는다.

---

```javascript
const str = "Hello World";

let a = str.substring(-5, -1);
let b = str.slice(-5, -1);
let c = str.slice(-5, -6);

console.log(a); // ""
console.log(b); // "Worl"
console.log(c); // ""
```

시작 index와 end index가 모두 음수가 될 수 있으며,
`slice()` 함수의 경우 start > end라면 빈 문자열이 아닌 문자열이 리턴된다.<br>

`substring()` 함수는 빈 문자열이 리턴된다.

`slice(-5, -1)`제외한 나머지는 빈 문자열을 리턴함.
