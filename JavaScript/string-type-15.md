# 문자열이 숫자인지 체크하기 isNaN()

Javascript의 문자열이 숫자인지 체크하기 위해서 isNaN() 함수를 사용한다.

## isNaN()

```javascript
isNaN(value);
```

`NaN은 'Not a Number'의 약자`이다.

파라미터가 `숫자가 아닌 경우 true`를 리턴하고,<br>
파라미터가 `숫자일 경우 false`를 리턴한다.

**숫자가 아닌가? 숫자가 아니라면 true, 숫자라면 false임.**

```javascript
isNaN("123"); // false
isNaN("abc"); // true
isNaN("123+123"); // true
isNaN(undefined); // true
isNaN({}); // true
isNaN(""); // false
isNaN(null); // false
isNaN(true); // false
isNaN([]); // false
isNaN(123); // false
isNaN(new Date()); // false
isNaN(new Date().toString()); // true
isNaN(123); // false
```

`"123"`<br>
문자열 타입이든 숫자 타입이든 숫자가 입력되면 isNaN() 함수는 false를 리턴한다.

`"abc"`<br>
문자열이 입력되면 true를 리턴한다.

`"123+123"`<br>
숫자로 이루어진 문자열 안에 숫자가 아닌 '+' 기호가 있기 때문에 true를 리턴한다.

`undefined`<br>
undefined, {}는 true를 리턴한다.

`"", null, true, []`<br>
빈 문자열, null, boolean 값, 배열은 false를 리턴한다.

`new Date()`<br>
new Date()는 false를 리턴한다.

`new Date().toString()`<br>
new Date().toString()은 문자를 리턴하므로 true를 리턴한다.

`123`<br>
숫자이므로 false를 리턴한다.
