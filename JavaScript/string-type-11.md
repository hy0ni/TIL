# 문자열 합치기 (4가지 방법)

1. '+' 연산자
2. '+=' 연산자
3. String.prototype.concat()
4. join()

## '+' 연산자

```javascript
const str = "Hello" + " " + "world";

console.log(str); // Hello world
```

숫자를 더할 때 '+' 연산자를 사용하는 것처럼 문장을 연결할 때도 '+'연산자를 사용할 수 있다.

## '+=' 연산자

```javascript
let str = "Hello";
str += " ";
str += "world";
console.log(str); // Hello world
```

'+=' 연산자를 사용할 수도 있다.

## String.prototype.concat()

`concat()` 함수는 매개변수로 전달된 모든 문자열을 호출 문자열에 붙인 새로운 문자열을 리턴한다.

```javascript
str.concat(string2, string3[, ..., stringN])
```

```javascript
const result = "Hello".concat(" ", "world");
console.log(result); // Hello world
```

#### 파라미터로 문자열 이외의 다른 타입 넣기

```javascript
const str = "";
const str1 = str.concat(null);
const str2 = str.concat(1, 2);
const str3 = str.concat(true, false);
const str4 = str.concat({ name: "hyoni" });
const str5 = str.concat([1, 2]);

console.log(str1); // null
console.log(str2); // 12
console.log(str3); // truefalse
console.log(str4); // [object Object]
console.log(str5); // 1,2
```

`concat()` 함수의 파라미터로 전달되는 다른 타입들은 문자열을 이어붙이면서 모두 string type으로 자동 변경된다.

`str.concat(null)`<br>
이 경우 str은 반드시 문자열이어야 한다.
그 이유는,<br>
배열에도 배열을 이어붙이는 함수인 concat() 함수가 있으므로
str 자리에 배열이 들어가게 되면 문자열이 아닌 배열을 이어붙이게 됨.

문자열을 합칠 때는<br>**concat() 함수를 사용하는 것보다 할당 연산자(+, +=)를 사용하는 게 성능 면에서 더 좋음.**

## join()

join() 함수는 배열의 모든 요소를 연결해 하나의 문자열로 만든다.

```javascript
const elements = ["Fire", "Air", "Water"];

console.log(elements.join()); // "Fire,Air,Water"
console.log(elements.join("")); // "FireAirWater"
console.log(elements.join("-")); // "Fire-Air-Water"
```

`join()` 함수는 문자열을 이어 붙일 때 separator(구분자)를 지정해 줄 수 있다.

`join()` 함수를 활용하면 반복문을 사용하지 않고도, 문자열에 구분자를 넣어서 이어붙일 수 있다.
