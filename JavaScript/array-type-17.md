# 배열 값 중복 체크, 제거하기 Set 객체

- [배열 값 중복 체크, 제거하기 Set 객체](#배열-값-중복-체크-제거하기-set-객체)
  - [Set 객체](#set-객체)
    - [중복값이 있는지 체크, 제거하기](#중복값이-있는지-체크-제거하기)
    - [중복값 제거 후 객체를 배열로 변환하기](#중복값-제거-후-객체를-배열로-변환하기)

## Set 객체

```javascript
new Set([iterable]);
```

Set 객체는 `중복을 허용하지 않는 유일한 값들의 집합`이다.
Set 내의 값은 유일해야 하기 때문에 값이 같은지 검사를 수행함.
Set 객체는 new 연산자를 사용하여 생성하고, 인자로 iterable 객체를 전달한다.
배열은 iterable 객체이므로, 배열을 인자로 전달하여 Set 객체를 생성할 수 있다.
Set은 length가 아닌 `size로 개수를 확인`한다.

### 중복값이 있는지 체크, 제거하기

```javascript
const arr = ["a", "b", "c", "c"];
const set = new Set(arr);

console.log(arr.length); // 4
console.log(set.length); // undefined
console.log(set.size); // 3
console.log(set); // {'a', 'b', 'c'}

if (arr.length !== set.size) {
  // arr의 길이와 set의 사이즈가 같지 않다면
  console.log("중복되는 요소가 없다.");
}
```

`const set = new Set(arr);`  
arr 배열을 new Set의 인자로 전달하여 set 객체를 생성.

Set 객체는 중복된 값을 허용하지 않기 때문에,  
set 객체는 중복된 값을 제거한 유일한 값들만 가지게 되어  
set 객체의 크기는 3이 된다.

`if(arr.length !== set.size){ `
` console.log("중복되는 요소가 없다.");`
`}`  
Set은 중복을 허용하지 않는다는 점을 활용해  
원본 배열인 arr의 길이와  
원본 배열을 가지고 생성한 set의 크기를 비교하여  
중복이 존재하는지 확인할 수 있다.

### 중복값 제거 후 객체를 배열로 변환하기

```javascript
const arr = ["a", "b", "c", "c"];
const set = new Set(arr);
const setArr = [...set];

console.log(set); // {'a', 'b', 'c'}
console.log(setArr); // ['a', 'b', 'c']
```

중복 값이 있는 arr 배열을  
`const set = new Set(arr)`  
Set 객체로 만들어 중복을 제거한 후,

`const setArr = [...set]`  
Spread Operator(전개 연산자)를 사용하여 Set 객체를 다시 배열로 변환한다.

Set 객체를 배열로 변환할 때, Spread Operator 대신  
Array.from() 또는 forEach() 문을 사용할 수도 있다.
