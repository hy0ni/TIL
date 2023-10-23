# 배열 합치기(3가지 방법)

- [배열 합치기(3가지 방법)](#배열-합치기3가지-방법)
  - [concat() 함수](#concat-함수)
  - [...spread operator(전개 연산자)](#spread-operator전개-연산자)
  - [push() 함수와 ...spread operator(전개 연산자)](#push-함수와-spread-operator전개-연산자)
    - [push() 메서드로 배열 합치기](#push-메서드로-배열-합치기)
    - [push() 메서드와 spread operator(...)로 배열 합치기](#push-메서드와-spread-operator로-배열-합치기)

## concat() 함수

```javascript
array.concat([value1[, value2[, ...[, valueN]]]])
```

Array 인스턴스의 `concat()` 메서드는 `두 개 이상의 배열을 병합하는 데 사용`된다.<br>
`concat()` 메서드는 `기존 배열을 변경하지 않고, 새 배열을 반환`한다.

```javascript
const arr = ["a"];
const newArr = arr.concat(["b", "c"]);

console.log(arr); // ['a']
console.log(arr.length); // 1

console.log(newArr); // ['a', 'b', 'c']
console.log(newArr.length); // 3
```

`const newArr = arr.concat(["c", "d"]);`<br>
concat() 메서드는 arr 배열(['a'])에 전달받은 3개(['a', 'b', 'c'])의 파라미터를 병합해 새로운 배열을 반환.<br>
`["a"] + ["b", "c"] = ['a', 'b', 'c']`

concat() 메서드는 인자로 전달받은 값 순으로 배열 끝에서부터 값을 추가한다.

인자가 배열인 경우, 배열 안에 요소들을 꺼내어 새로운 배열에 포함시킨다.<br>
기존 arr 배열의 값은 변하지 않음.

새로운 newArr 배열의 길이는 3이 된다.

## ...spread operator(전개 연산자)

ES6(ECMAScript6)에서 제공하는 `spread(...) 구문`을 사용하여 배열을 이어 붙일 수 있다.

스프레드 구문은 객체나 배열의 모든 요소를 ​​새 배열이나 객체에 포함해야 하거나
함수 호출의 인수(Argument) 목록에 하나씩 적용해야 할 때 사용할 수 있다.

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = [7, 8, 9];

const newArr = [...arr1, ...arr2, ...arr3];

console.log(newArr); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(newArr.length); // 9
```

`...`배열 리터럴은 배열의 어느 위치에서나 사용할 수 있으며 두 번 이상 사용할 수 있다.

spread operator `...`은 배열의 요소를 각각 분해하여 개별 요소로 반환한다.<br>
newArr는 이렇게 분해된 개별 요소들을 인자로 가진 새로운 배열이다.

concat() 메서드와 마찬가지로 `원본 배열을 변경하지 않고, 새로운 배열을 반환`한다.

## push() 함수와 ...spread operator(전개 연산자)

`push() `메서드를 사용하여 배열을 합치려면 `spread operator`와 함께 사용해야 한다.

### push() 메서드로 배열 합치기

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
arr1.push(arr2);

console.log(arr1); //[ 1, 2, 3, [ 4, 5, 6 ] ]
console.log(arr2); // [4, 5, 6]
console.log(arr1.length); // 4
```

`push()` 메서드는 배열에 값을 넣기 위해 사용되는데 `인자로 전달된 배열 자체가 push` 된다.

인자로 전달된 배열은 arr1의 2번째 요소가 되어 arr1의 길이는 6이 아닌 4가 된다.

### push() 메서드와 spread operator(...)로 배열 합치기

spread operator ...은 배열의 요소를 각각 분해하여 개별 요소로 반환합니다.

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
arr1.push(...arr2);

console.log(arr1); // [ 1, 2, 3, 4, 5, 6 ]
console.log(arr1.length); // 6
```

인자로 전달되는 arr2배열에 spread operator를 사용하여<br>
`배열의 요소를 각각 분해해 요소 하나하나가 push` 됨.

따라서 arr1의 길이는 6이 된다.

arr1.push(...arr2) 이 표현식은<br>
arr1.push(4, 5, 6)와 같다.

이 방법은 `원본 배열을 변경`한다.
