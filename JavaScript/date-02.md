# Date 객체로 원하는 날짜, 시간 표현하기

- [Date 객체로 원하는 날짜, 시간 표현하기](#date-객체로-원하는-날짜-시간-표현하기)
  - [new Date()](#new-date)
  - [new Date(year, month, day, hours, minutes, seconds, milliseconds)](#new-dateyear-month-day-hours-minutes-seconds-milliseconds)
  - [new Date(milliseconds)](#new-datemilliseconds)
  - [1970년 1월 1일 이전의 날짜 표현하기](#1970년-1월-1일-이전의-날짜-표현하기)
  - [new Date('date')](#new-datedate)

## new Date()

아무것도 전달하지 않고 Date 객체를 생성하면 현재 날짜와 시간을 가진 Date 객체가 생성된다.

## new Date(year, month, day, hours, minutes, seconds, milliseconds)

Date 객체를 생성할 때 7개 파라미터를 순서대로 전달하면
지정한 날짜와 시간으로 Date 객체가 생성된다.  
(`연도, 월, 일, 시, 분, 초, 밀리초`)

```javascript
let date = new Date(2023, 0, 10, 12, 1, 10, 22);

console.log(date); // Tue Jan 10 2023 12:01:10 GMT+0900 (한국 표준시)
console.log(date.toLocaleString()); // 2023. 1. 10. 오후 12:01:10
```

**주의해야할 점**

- `연도`와 `월`은 `필수 입력값`.  
  연도만 파라미터로 전달하면, 전달된 연도는 new Date(milliseconds)로 해석된다.

- `월은 0에서 11 사이의 숫자(0~11)가 입력` 되어야 한다.  
  0은 1월, 11은 12월이다.

## new Date(milliseconds)

```javascript
let date = new Date(1000);

console.log(date); // Thu Jan 01 1970 09:00:01 GMT+0900 (한국 표준시)
console.log(date.toLocaleString()); // 1970. 1. 1. 오전 9:00:01
```

Date 객체를 생성할 때 파라미터를 1개만 지정하면 이 값은 milliseconds로 해석된다.

milliseconds 값으로 1000을 전달하였는데 출력된 날짜가 1970년 1월 1일 9시 0분 1초인 것을 볼 수 있다.

여기에서 `milliseconds의 기준 일자는 1970년 1월 1일 0시 0분 0초 0밀리초(UTC 시간 기준)이기 때문`이다.

( ※ UTC 시간이란? '협정 세계시'로 1972년 1월 1일부터 시행된 국제 표준시 )

`new Date(1000)`  
즉, 1970년 1월 1일 0시 0분 0초 0밀리 초에 1000이 더해진 시간인 1970년 1월 1일 0시 0분 1초를 표현하는 Date 객체가 생성됨.

그런데, 자세히 보면 `1970년 1월 1일 0시 0분 1초`가 아닌,  
`1970년 1월 1일 9시 0분 1초`인 이유는  
우리나라는 UTC 시간과 9시간의 시차가 나기 때문에 1970년 1월 1일 9시 0분 1초라고 나온다.

즉, milliseconds를 파라미터로 전달하면  
1970년 1월 1일 0시 0분 0초 0밀리초를 기준으로,  
입력된 millisecond 만큼 지난 후의 날짜를 가진 Date 객체를 생성하게 된다.  
그리고, 생성된 Date 객체를 출력하면,  
해당 브라우저에 설정된 시간대 기준으로 시간을 표현해 준다.

```javascript
let date = new Date(1000);

console.log(date.toUTCString()); // Thu, 01 Jan 1970 00:00:01 GMT
```

UTC 시간 기준으로 시간을 표현하고 싶으면, `toUTCString()` 함수를 사용하면 된다.

## 1970년 1월 1일 이전의 날짜 표현하기

```javascript
let date = new Date(-100000000);

console.log(date.toUTCString()); // Tue, 30 Dec 1969 20:13:20 GMT
```

milliseconds 자리에 마이너스 값을 넣어 1970년 1월 1일 이전의 시간을 표현할 수 있다.

## new Date('date')

```javascript
let date = new Date("August 15, 2023 11:22:33");

console.log(date); // Tue Aug 15 2023 11:22:33 GMT+0900 (한국 표준시)
```

파라미터로 날짜와 시간을 의미하는 String을 직접 입력하는 방법.
