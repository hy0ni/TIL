# for...of 반복문

for...of 반복문은 반복 가능한 객체 (Array, Map, Set, String, TypedArray, arguments 객체 등을 포함)의 값들을 순회할 수 있다.

for...of를 사용하면 배열의 인덱스는 알 수 없음.

```javascript
for (variable of iterable) {
  statement;
}
```

`object 는 iterable 객체`이다. (배열 또는 Map, Set, String 등)  
`variable은 iterable 객체에서 하나씩 뽑아온 값`이다.

### Array에 대해 반복

```javascript
const iterable = ["a", "b", "c"];

for (const element of iterable) {
  console.log(element);
}

// output: "a"
// output: "b"
// output: "c"
```

블록 내부 변수를 수정하지 않는 경우, let 대신 const도 사용할 수 있음.

## String에 대해 반복

```javascript
let iterable = "boo";

for (let value of iterable) {
  console.log(value);
}

// output: "b"
// output: "o"
// output: "o"
```

for...of 구문으로 문자열 객체를 순회하면, 문자열의 한 글자씩 가져온다.

## Map에 대해 반복

```javascript
let iterable = new Map([
  ["a", 1],
  ["b", 2],
  ["c", 3],
]);

for (let entry of iterable) {
  console.log(entry);
}
// output: [a, 1]
// output: [b, 2]
// output: [c, 3]

for (let [key, value] of iterable) {
  console.log(value);
}
// output: 1
// output: 2
// output: 3
```

for...of 구문으로 Map 객체를 순회하면 [key, value] 형태의 배열 객체를 하나씩 가져온다.

## Set에 대해 반복

```javascript
let iterable = new Set([1, 1, 2, 2, 3, 3]);

for (let value of iterable) {
  console.log(value);
}
// output: 1
// output: 2
// output: 3
```

for...of 구문으로 Set 객체를 순회하면, 각각의 값들을 하나씩 가져온다.
