# 배열 선언하기 (2가지 방법)

## 대괄호([])를 사용하여 배열 선언하기

```javascript
const arr = [];
const arr1 = ["bread", "milk", "cheese"];
const arr2 = ["tree", 7, true, [0, 1, 2]];

console.log(arr); // []
console.log(arr1); // ["bread", "milk", "cheese"]
console.log(arr2); // ['tree', 7, true, Array(3)]
console.log(arr2.length); // 4
```

`const arr = [];`  
대괄호를 사용하여 빈 배열을 생성하거나

`const arr1 = ["bread", "milk", "cheese"];`  
배열을 선언할 때 초기값을 할당하여 배열을 생성할 수 있다.

`const arr2 = ["tree", 7, true, [0, 1, 2]];`  
배열에는 다양한 데이터 유형을 저장할 수 있다.  
(문자열, 숫자, 개체, 다른 변수, 심지어 다른 배열)

arr2 배열에는 배열 안에 정수 3개를 가진 [0, 1, 2] 배열이 추가되었지만  
arr2 배열의 길이는 4가 출력된다.
배열 안에 배열이 들어갈 경우 1개의 배열로 취급되기 때문이다.

## Array() 생성자 함수를 사용하여 배열 선언하기

대괄호를 사용하여 배열을 선언하는 것이 보편적으로 선호하는 방법이지만
Array() 생성자 함수를 사용하여 배열을 선언할 수 도 있다.

**Array()는 new를 붙이거나 붙이지 않고 호출할 수 있다.**  
**둘 다 새 Array 인스턴스를 생성한다.**

```javascript
const arry = new Array();
const arry1 = new Array(5);
const arry2 = new Array("bread", "milk", "cheese");

console.log(arry); // []
console.log(arry1); // [empty × 5]
console.log(arry2); // ['bread', 'milk', 'cheese']

const arry3 = Array();
const arry4 = Array(5);
const arry5 = Array("bread", "milk", "cheese");

console.log(arry3); // []
console.log(arry4); // [empty × 5]
console.log(arry5); // ['bread', 'milk', 'cheese']
```

`const arry = new Array();`  
매개변수로 아무것도 전달되지 않으면 빈 배열이 생성된다.

`const arry1 = new Array(5);`  
생성자의 전달된 인수가 정수인 경우,  
배열의 길이가 해당 숫자로 설정된 새 배열을 생성한다.

길이가 5인 배열이 생성되며,  
배열의 원소는 모두 undefined로 채워지는데 배열의 길이만큼의 빈 슬롯 배열을 의미한다.

`const arry2 = new Array("bread", "milk", "cheese");`  
생성자에 두 개 이상의 매개변수를 전달한 경우,  
매개변수를 원소로 하는 새로운 배열이 생성된다.

3개의 매개변수가 전달되어  
길이가 3인 "bread", "milk", "cheese"를 원소로 하는 배열이 생성되었다.
