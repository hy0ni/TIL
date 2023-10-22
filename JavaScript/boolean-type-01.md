# 연산자(operator)

1. [산술 연산자](#산술-연산자)
2. [증가 및 감소 연산자 ](#2-증가-및-감소-연산자)
3. [문자열 연산자](#3-문자열-연산자)
4. [대입 연산자](#4-대입-연산자)
5. [비교 연산자](#5-비교-연산자)
6. [논리 연산자](#6-논리-연산자--or-and-not)
7. [조건 (삼항) 연산자](#7-조건-삼항-연산자)
8. [단항 연산자](#8-단항-연산자)
9. [관계 연산자](#9-관계-연산자)

`**참고: 피연산자는 연산자에 의해 처리되는 데이터를 의미.`<br>
`예를 들어, 숫자 두 개를 더하는 경우 두 숫자는 피연산자이고 "+"는 연산자다.`

## 1. 산술 연산자

산술 연산자는 두 개의 숫자 값(리터럴 또는 변수)을 피연산자로 받아서 하나의 숫자 값을 반환한다.

표준 산술 연산자: 더하기(+), 빼기(-), 곱하기(\*), 나누기(/)<br>
(0으로 나눌 경우 Infinity를 반환하므로 주의해야 한다.)

```javascript
1 + 1; // add(추가)
1 - 1; // substract(빼기)
1 / 1; // divide(나누기)
1 * 1; // multiply(곱하기)
5 % 2; // remainder(나머지)
2 ** 3; // exponentiation(지수) (3의 제곱)
```

## 2. 증가 및 감소 연산자

반복해서 숫자 변수의 값을 1씩 더하거나 빼고 싶을 때 증가(++) 연산자와 감소(--) 연산자를 사용한다.

### 증가(++) 연산자

증가(++) 연산자는 피연산자를 증가(1을 더함) 시키고
연산자의 위치에 따라 증가하기 전이나 후의 값을 반환한다.

#### `후위 증가`

```javascript
let x = 3;
const y = x++;

console.log(x); // x = 4
console.log(y); // y = 3
```

`x++;`
피연산자 뒤에 연산자를 붙여서 사용하면,<br>
증가 연산자는 수를 증가시키고 증가하기 전 값을 반환한다.

#### `전위 증가`

```javascript
let x = 3;
const y = ++x;

console.log(x); // x = 4
console.log(y); // y = 4
```

`++x;`
피연산자 앞에 연산자를 붙여서 사용하면,<br>
증가 연산자는 수를 증가시키고 증가 후 값을 반환한다.

### 감소(--) 연산자

#### `후위 감소`

```javascript
let x = 3;
const y = x--;

console.log(x); // x = 2
console.log(y); // y = 3
```

` x--;`<br>
감소(--) 연산자는 피연산자를 감소(1을 뺌)시키고
연산자의 위치에 따라 감소하기 전이나 후의 값을 반환한다.

#### `전위 감소`

```javascript
let x = 3;
const y = --x;

console.log(x); // x = 2
console.log(y); // y = 2
```

`--x;`<br>
피연산자 앞에 연산자를 붙여서 사용하면,<br>
감소 연산자는 수를 감소시키고 감소 후 값을 반환한다.

## 3. 문자열 연산자

```javascript
console.log("my" + " cat"); //my cat
console.log("1" + 2); // 12
console.log(`string literals: 1 + 2 = ${1 + 2}`);
//string literals: 1 + 2 = 3
console.log("my" + " cat"); // my cat
```

`+` 기호를 사용하여 문자열과 문자열을 더해 새로운 문자열을 만들 수 있다.

```javascript
let mystring = "한";
mystring += "글";
console.log(mystring); // 한글
```

단축 할당 연산자인 `+=` 또한 문자열을 연결할 때 사용할 수 있다.

```javascript
console.log("1" + 2); // 12
```

문자열에 숫자를 더하게 되면 숫자가 문자열로 변환되어 새로운 문자열을 만들 수 있다.

```javascript
console.log(`string literals: 1 + 2 = ${1 + 2}`);
//string literals: 1 + 2 = 3
```

` 백틱(``) `기호를 활용하여 스트링 리터럴 값으로 만들 수 있다.

템플릿 문자열 사용: ` 백틱(``) `으로 문장을 감싸고 `변수가 들어갈 부분`에 달러 기호($)와 중괄호({})를 사용해` ${변수명}`과 같은 형태로 입력해 주면 된다.

## 4. 대입 연산자

변수에 값을 대입하는 연산자.<br>
(=) 연산자는 변수 오른쪽에 있는 값을 대입한다.

```javascript
let x = 3; // x의 값 3
let y = 6; // y의 값 6
x = y; // 이제 x의 값은 y와 같은 3이 된다.

x += y; // x = x + y;
x -= y;
x *= y;
x /= y;
```

`x = x + y`<br>
반복되는 x를 생략해서

`x += y`<br>
코드를 더 깔끔하고 효율적으로 작성할 수 있다.

| 연산자 |    이름     |                            목적                            |   예시   |    의미     |
| :----: | :---------: | :--------------------------------------------------------: | :------: | :---------: |
|   +=   | 더하기 대입 | 오른쪽의 값을 왼쪽 변수 값에 더하고 새 변수 값을 반환한다. | x += 4;  | x = x + 4;  |
|   -=   |  빼기 대입  | 오른쪽의 값을 왼쪽 변수 값에서 빼고 새 변수 값을 반환한다. | x -= 3;  | x = x - 3;  |
|  \_=   | 곱하기 대입 | 오른쪽의 값을 왼쪽 변수 값에 곱하고 새 변수 값을 반환한다. | x \_= 3; | x = x \* 3; |
|   /=   | 나누기 대입 | 오른쪽의 값을 왼쪽 변수 값에 나누고 새 변수 값을 반환한다. | x /= 5;  |  x = x / 5  |

## 5. 비교 연산자

비교 연산자는 피연산자를 서로 비교하고, 비교 결과가 참인지에 따라 논리 값을 반환한다.

참/거짓 테스트를 실행한 결과에 따라 다르게 처리하고자 할 때 자주 사용 됨.

```javascript
console.log(10 < 5); // 보다 작음
console.log(10 <= 5); // 작거나 같음
console.log(10 > 5); // 보다 큼
console.log(10 >= 5); // 보다 크거나 같음
```

| 연산자 |       이름        |                                              목적                                              |    예시     |
| ------ | :---------------: | :--------------------------------------------------------------------------------------------: | :---------: |
| ==     |    동등 연산자    |                       왼쪽과 오른쪽의 값이 서로 같으면 true를 반환한다.                        |  3 == '3'   |
| !=     |    부등 연산자    |                       왼쪽과 오른쪽의 값이 서로 다르면 true를 반환한다.                        |  1 != '3'   |
| ===    |    일치 연산자    | 왼쪽과 오른쪽의 값이 완전히 동일한지 테스트.<br>(값과 타입이 모두 같은 경우 true를 반환한다.)  | 5 === 2 + 4 |
| !==    |   불일치 연산자   | 왼쪽과 오른쪽 값이 서로 동일하지 않은지 테스트.<br>(값 또는 타입이 다를 경우 true를 반환한다.) | 5 !== 2 + 3 |
| <      |    ~보다 작음     |                        왼쪽 값이 오른쪽 값보다 작으면 true를 반환한다.                         |   10 < 6    |
| >      |     ~보다 큼      |                         왼쪽 값이 오른쪽 값보다 크면 true를 반환한다.                          |   10 > 20   |
| <=     | ~보다 작거나 같음 |                     왼쪽 값이 오른쪽 값보다 작거나 같으면 true를 반환한다.                     |   3 <= 2    |
| >=     | ~보다 크거나 같음 |                     왼쪽 값이 오른쪽 값보다 크거나 같으면 true를 반환한다.                     |   5 >= 4    |

`**참고: => 는 연산자가 아닌 화살표 함수의 표기법이다.`

### `'=='와 '==='의 차이점`

==와 != 동등성과 불일치성을 테스트하는 데 사용한다.<br>
==와 != 값이 동일한지는 테스트하지만, 값의 데이터 유형이 동일한지의 여부는 테스트하지 않는다.

===와 !== 값과 값의 데이터 유형의 동일성을 모두 테스트한다.<br>
===와 !== 오류가 적은 편이기 때문에 === / !==사용하는 것을 권장함.

```javascript
0 == false; //true
0 === false; // false
"" == false; // true
"" === false; // false
null == undefined; //true
null === undefined; // false
```

**`false로 간주되는 값`**

- undefined, null
- NaN
- 0 (숫자 리터럴) , -0
- " " (빈 문자열)
- false

## 6. 논리 연산자 ( ||(or), &&(and), !(not) )

### `||(or)`

||(or) 연산자는 비교값 중 하나라도 true면 true를 반환.
첫 번째 값이 true면 true를 반환하고 계산을 종료함.

```javascript
// || (논리 OR) 연산자
let or1 = true || true; // true || true는 true 반환
let or2 = false || true; // false || true는 true 반환
let or3 = true || false; // true || false는 true 반환
let or4 = false || 3 == 4; // false || false는 false 반환
let or5 = "Cat" || "Dog"; // true || true는 Cat 반환
let or6 = false || "Cat"; // false || true는 Cat 반환
let or7 = "Cat" || false; // true || false는 Cat 반환
```

### `&&(and)`

&&(and) 연산자는 비교값이 모두 true여야 true를 반환하고,<br>
하나라도 false면 false를 반환

```javascript
// && (논리 AND) 연산자
let and1 = true && true; // true && true는 true 반환
let and2 = true && false; // true && false는 false 반환
let and3 = false && true; // false && true는 false 반환
let and4 = false && 3 == 4; // false && false는 false 반환
let and5 = "Cat" && "Dog"; // true && true는 Dog 반환
let and6 = false && "Cat"; // false && true는 false 반환
let and7 = "Cat" && false; // true && false는 false 반환
```

### `!(not)`

!(not) 연산자는 값을 반대로 바꿔주는 역할을 함.

```javascript
// ! (논리 NOT) 연산자
let n1 = !true; // !t는 false 반환
let n2 = !false; // !f는 true 반환
let n3 = !"Cat"; // !t는 false 반환
```

## 7. 조건 (삼항) 연산자

조건 (삼항) 연산자는 JavaScript에서 세 개의 피연산자를 받는 유일한 연산자다.

삼항 연산자를 이용해 if조건문을 좀 더 간결하게 사용할 수 있다.

앞에서부터 조건문, 물음표(?), 조건문이 참(true) 일 경우 실행할 표현식, 콜론(:), 조건문이 거짓(false) 일 경우 실행할 표현식이 배치된다.

삼항 연산자는 주어진 조건에 따라 두 값 중 하나를 반환한다.

```javascript
condition ? val1 : val2;
```

만약 condition이 true라면, 조건 연산자는 val1을 반환하고, false라면 val2를 반환한다.

```javascript
const age = 20;
let status = age >= 18 ? "성인" : "미성년자";

console.log(status); // "성인"
```

age가 18 이상이라면 status 변수에 "성인"을 할당하고, 그렇지 않으면 "미성년자"를 할당 함.

## 8. 단항 연산자

### `typeof`

[데이터 타입 확인하기 typeof](./string-type-21.md)

```javascript
typeof operand;
```

typeof 연산자는 피연산자 타입을 나타내는 문자열을 반환한다.

operand는 문자열, 변수, 키워드, 객체 등 타입을 알아낼 값.(주위의 괄호는 선택 사항)

### `delete`

delete 연산자는 객체의 속성을 삭제한다.

```javascript
delete object.property;
delete object[propertyKey];
delete objectName[index];
```

`object.property`<br>
property: 객체에 존재하는 속성.

`object[propertyKey]`<br>
propertyKey: 존재하는 속성을 가리키는 문자열이나 심볼.

`objectName[index]`<br>
objectName: 객체의 이름.

```javascript
console.log(delete Math.PI); // false 반환 (설정 불가한 속성 삭제 불가)

const myObj = { h: 5 };

console.log(delete myObj.h); // true 반환 (사용자 정의 속성 삭제 가능)
console.log(myObj.h); // undefined 반환
```

delete 연산자가 속성을 삭제한 이후,
해당 속성을 접근하려고 하면 undefined를 반환한다.

delete는 속성을 제거할 수 있는 경우 true를 반환하고,
제거할 수 없을 땐 false를 반환한다.

### `void`

```javascript
void expression;
```

void 연산자는 표현식을 평가할 때 값을 반환하지 않도록 지정한다.

expression은 평가할 JavaScript 표현식이다.

`void (expression);`<br>
주위 괄호는 선택 사항이지만, 사용하면 좋음.

## 9. 관계 연산자

관계 연산자는 피연산자를 서로 비교하고,
비교 결과가 true인지에 따라 boolean 값을 반환한다.

### `in`

in 연산자는 지정한 속성이 지정한 객체에 존재할 경우 true를 반환한다.

```javascript
propNameOrNumber in objectName;
```

propNameOrNumber는 속성이나 배열 index를 나타내는 문자열, 숫자, 심볼 표현식이며,<br>
objectName은 객체의 이름이다.

##### `(배열)`

```javascript
let trees = ["redwood", "bay", "cedar", "oak", "maple"];
console.log(0 in trees); // true 반환
console.log(3 in trees); // true 반환
console.log(6 in trees); // false 반환
console.log("bay" in trees); // false 반환
```

`0 in trees`<br>
trees배열에 0번째 index에 값이 있으므로 true를 반환.

`3 in trees`<br>
trees배열에 3번째 index에 값이 있으므로 true를 반환.

`6 in trees`<br>
trees배열의 길이는 5, 6번째 index에 값이 없으므로 false를 반환.

`"bay" in trees`
index에 위치한 값이 아니라 index 자체를 지정해야 하므로 false를 반환.

##### `(내장 객체)`

```javascript
let myString = new String("coral");

console.log(myString); // 0:"c" 1:"o" 2:"r "3:"a" 4:"l"
console.log("length" in myString); // true 반환
```

"문자열" 값을 담은 String객체를 생성.

myString은 객체이기 때문에 내장객체인 length를 사용할 수 있으므로 true를 반환.

##### `(사용자 정의 객체)`

```javascript
let mycar = { make: "Honda", model: "Accord", year: 1998 };

console.log("make" in mycar); // true 반환
console.log("model" in mycar); // true 반환
```

mycar에 정의한 객체의 속성값 "make"와 "model"이 모두 존재하므로 true를 반환.

### `instanceof`

instanceof 연산자는 지정한 객체가 지정한 객체 타입에 속하면 true를 반환한다.

```javascript
objectName instanceof objectType;
```

objectName은 objectType과 비교할 객체의 이름이고,

objectType은 Date, Array와 같은 객체 타입이다.

객체의 타입을 확인할 필요가 있을 때 instanceof 연산자를 사용한다.

#### (instanceof 연산자를 사용해서 theDay 객체가 Date 객체인지 알아내는 예제)

```javascript
let theDay = new Date(2023, 09, 27);

if (theDay instanceof Date) {
  // 실행할 명령문
}
```

theDay 객체는 Date 객체이기 때문에, true값을 반환하여 if 명령문 안의 내용이 실행된다.
