# 배열에서 특정 값 삭제하기

- [배열의 전체 값 삭제](#배열의-전체-값-삭제)
- [배열의 첫 번째 값 삭제](#배열의-첫-번째-값-삭제)
- [배열의 역순으로 값 삭제](#배열의-역순으로-값-삭제)
- [배열의 특정 index값 삭제](#배열의-특정-index값-삭제)
- [배열의 특정 값 삭제](#배열의-특정-값-삭제)

## 배열의 전체 값 삭제

### 빈 배열 할당하기

```javascript
let arr = ["apple", "banana", "mango"];
arr = [];

console.log(arr); // []
console.log(arr.length); // 0
```

새로운 빈 배열을 만들어 배열 변수에 할당.

### 배열의 길이 0으로 변경하기

```javascript
let arr = ["apple", "banana", "mango"];
arr.length = 0;

console.log(arr); // []
console.log(arr.length); // 0
```

`arr.length = 0`  
길이가 3인 arr배열의 길이를 0으로 설정해 주면,  
arr배열의 길이는 0으로 설정되어 빈 배열이 된다.

### 빈 배열 할당하기(참조 변수)

```javascript
let arr = ["apple", "banana", "mango"];
let copyArr = arr;

arr = [];

console.log(arr.length); // 0
console.log(copyArr.length); // 3
```

배열에 빈 배열을 새로 할당하는 경우,  
arr에 새로운 배열 객체(비어있는)가 할당되고,  
copyArr는 원본 배열을 참조한다.

### 배열의 길이 0으로 변경하기(참조 변수)

```javascript
let arr = ["apple", "banana", "mango"];
let copyArr = arr;

arr.length = 0;

console.log(arr.length); // 0
console.log(copyArr.length); // 0
```

배열의 길이를 0으로 세팅하는 경우,  
새로운 배열 객체를 만들어 할당하는 것이 아닌  
원본 배열의 length 값만 0으로 변경해 주는 것이기 때문에  
copyArr가 참조하는 배열의 길이도 0이 된다.

## 배열의 첫 번째 값 삭제

### shift() 메서드 사용하기

```javascript
const arr = ["apple", "banana", "mango"];
arr.shift();

console.log(arr); //['banana', 'mango']
```

## 배열의 역순으로 값 삭제

### 배열의 길이 지정하기

```javascript
const arr = ["apple", "banana", "mango", "lemon"];
arr.length = 3;

console.log(arr); // ['apple', 'banana', 'mango']
```

배열의 뒤에서부터 역순으로 값을 삭제하고 싶을 때는  
남겨두고 싶은 배열의 길이만큼 배열의 length값을 설정해 주면 된다.

### pop() 메서드 사용하기

```javascript
const arr = ["apple", "banana", "mango", "lemon"];
arr.pop();
console.log(arr); //['apple', 'banana', 'mango']
```

## 배열의 특정 index값 삭제

### splice() 메서드 사용하기

```javascript
const arr = ["apple", "banana", "mango", "lemon"];
arr.splice(2, 1);

console.log(arr); // ['apple', 'banana', 'lemon']
```

splice() 메서드를 이용해 특정 index값을 삭제할 경우  
첫 번째 파라미터는 배열의 변경을 시작할 index를 입력하고  
두 번째 파라미터는 삭제할 요소의 개수를 입력한다.

## 배열의 특정 값 삭제

### filter() 메서드 사용하기

```javascript
const arr = ["apple", "banana", "mango", "lemon"];
const filtered = arr.filter((element) => element !== "banana");

console.log(arr); // ["apple", "banana", "mango", "lemon"]
console.log(filtered); // ['apple', 'mango', 'lemon']
```

filter() 메서드는 특정 조건에 일치하는 모든 요소를 새로운 배열로 반환한다.

배열에서 "banana"값을 삭제하기 위해  
`arr.filter((element) => element !== "banana")`  
arr배열의 원소의 값이 "banana"가 아닌 요소들만 가진 새로운 배열을 만듬.

새로운 배열을 가진 filtered를 출력해 보면  
"banana"를 제외한 나머지 요소들만 들어있는 배열을 확인할 수 있다.
