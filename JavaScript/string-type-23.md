# 숫자 3자리(천 단위)마다 콤마 찍기 (2가지 방법)

- 정규식(Regular Expression) 이용하기
- toLocaleString() 함수 이용하기

## 정규식(Regular Expression) 이용하기

```javascript
const n1 = 12345.6789;
const n2 = -12345.6789;

const cn1 = n1.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
const cn2 = n2.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");

console.log(cn1); // 12,345.6789
console.log(cn2); // -12,345.6789
```

정규식을 사용하여 천 단위마다 콤마 추가.

## toLocaleString() 함수 이용하기

toLocaleString() 메서드를 이용하려면 반드시 Number 타입에 사용해야 한다.  
만일 숫자 데이터가 아닌 문자열에 사용을 하면 오류를 반환한다.

```javascript
number.toLocaleString(locales, options);
```

toLocaleString() 함수는 숫자를 로컬의 language format에 맞는 문자열로 변경해 준다.  
파라미터로 아무것도 전달되지 않으면 사용자 로컬 환경의 locale을 default로 사용함.

```javascript
const num = 123456789;

console.log(num.toLocaleString()); // 123,456,789

console.log(num.toLocaleString("ko-KR")); // 123,456,789

const number = 123456789.123456;

console.log(number.toLocaleString("ko-KR", { maximumFractionDigits: 4 })); // 123,456,789.1234
```

`num.toLocaleString()`  
`toLocaleString()`는 인자 없이 사용할 경우 사용자의 PC의 환경 로컬을 따라서 표시해 준다.

`num.toLocaleString("ko-KR")`  
로컬을 인자로 넣으면 해당 로컬의 포맷으로 표시해 준다.

`number.toLocaleString("ko-KR", { maximumFractionDigits: 4 })`  
toLocaleString() 함수를 통해서 나온 결과는 소수점 3자리까지만 표현되는데,
이것은 toLocaleString() 함수의 default fraction digit 값이 3이기 때문이다.
소수점 4자리까지 표현해 주기 위해서는
toLocaleString() 함수를 호출할 때 두 번째 파라미터로 option 객체를 전달해야 한다.

option 인자로 전달되는 객체 안에는 maximumFractionDigits 값이 4로 지정되어 있어서 소수점 4자리까지 표시된다.
