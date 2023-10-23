# 배열 앞, 뒤에 값 추가, 삭제하기 unshift(), shift(), push(), pop()

- [배열 앞, 뒤에 값 추가, 삭제하기 unshift(), shift(), push(), pop()](#배열-앞-뒤에-값-추가-삭제하기-unshift-shift-push-pop)
  - [unshift() 배열 앞에 값 추가하기](#unshift-배열-앞에-값-추가하기)
  - [shift() 배열 앞에 값 삭제하기](#shift-배열-앞에-값-삭제하기)
  - [push() 배열의 끝에 값 추가하기](#push-배열의-끝에-값-추가하기)
  - [pop() 배열의 끝에 값 삭제하기](#pop-배열의-끝에-값-삭제하기)

## unshift() 배열 앞에 값 추가하기

```javascript
arr.unshift([...elementN]);
```

`unshift()` 메서드는 `새로운 요소를 배열의 맨 앞쪽에 추가`하고, `새로운 길이를 반환`한다.

```javascript
const arr = ["apple", "banana"];
const count = arr.unshift("cherry");

console.log(count); // 3
console.log(arr); // ['cherry', 'apple', 'banana']
```

`unshift()` 메서드를 이용해 배열의 맨 앞에 "cherry"을 추가.<br>
새로운 길이인 3을 리턴하고,<br>
arr는 ['cherry', 'apple', 'banana']값을 가지게 된다.

```javascript
const arr = ["apple", "banana"];
const count = arr.unshift("cherry", "strawberry");

console.log(arr.length); // 4
console.log(arr); // ['cherry', 'strawberry', 'apple', 'banana']
```

`unshift()` 메서드를 이용해 배열의 맨 앞에 여러 개의 값을 추가할 수도 있다.

<br>

## shift() 배열 앞에 값 삭제하기

```javascript
arr.shift();
```

`shift()` 메서드는 `배열에서 첫 번째 요소를 제거`하고, `제거된 요소를 반환`한다.<br>
이 메서드는 배열의 길이를 변하게 한다.

```javascript
const arr = ["apple", "banana", "cherry", "strawberry"];
const removed = arr.shift();

console.log(arr); // ['banana', 'cherry', 'strawberry']
console.log(removed); // 'apple'
```

`const removed = arr.shift();`<br>
첫 번째 요소를 삭제하여 ['banana', 'cherry', 'strawberry'] 값이 남게 되었고,<br>
삭제한 요소인 'apple'을 반환함.

```javascript
const arr = ["apple", "banana", "cherry", "strawberry"];
const removed = arr.shift();
removed = arr.shift();

console.log(arr); // ['cherry', 'strawberry']
console.log(removed); // 'banana'
```

`removed = arr.shift();`<br>
배열의 첫 번째 요소를 한 번 더 삭제하여,<br>
arr에는 ['cherry', 'strawberry']가 남게 되고 'banana'를 반환함.

<br>

## push() 배열의 끝에 값 추가하기

```javascript
arr.push(element1[, ...[, elementN]])
```

`push()` 메서드는 `배열의 끝에 하나 이상의 요소를 추가`하고, `배열의 새로운 길이를 반환`한다.

```javascript
const animals = ["pigs", "goats", "sheep"];
const count = animals.push("cows");

console.log(animals); // ["pigs", "goats", "sheep", "cows"]
console.log(count); // 4
```

베열의 맨 끝에 "cows" 요소를 추가함.<br>
push() 메서드는 새로운 배열의 길이인 4를 리턴하고,<br>
['pigs', 'goats', 'sheep', 'cows'] 값을 가지게 됨.

```javascript
const animals = ["pigs", "goats", "sheep"];
const count = animals.push("cows", "dogs", "cats");

console.log(animals); // ["pigs", "goats", "sheep", "cows", "dogs", "cats"]
console.log(count); // 6
```

파라미터를 여러 개 전달하여, 배열의 맨 끝에 여러 개의 요소를 추가할 수도 있다.

<br>

## pop() 배열의 끝에 값 삭제하기

```javascript
arr.pop();
```

pop() 메서드는 `배열에서 마지막 요소를 제거`하고 `그 요소를 반환`한다.

```javascript
const animals = ["pigs", "goats", "sheep"];
const count = animals.pop();

console.log(animals); // ["pigs", "goats"]
console.log(count); // "sheep"
```

배열에서 가장 마지막 요소를 삭제함.<br>
pop() 메서드는 삭제한 요소인 "sheep"를 리턴하고,<br>
animals 배열에는 ["pigs", "goats"]만 남게된다.
