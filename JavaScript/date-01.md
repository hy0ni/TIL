# 현재 날짜, 시간 구하기

- [현재 날짜, 시간 구하기](#현재-날짜-시간-구하기)
  - [현재 날짜 구하기](#현재-날짜-구하기)
  - [현재 연도/월/일/요일 구하기](#현재-연도월일요일-구하기)
  - [현재 시간/분/초/밀리초 구하기](#현재-시간분초밀리초-구하기)

## 현재 날짜 구하기

```javascript
let today = new Date();
```

## 현재 연도/월/일/요일 구하기

```javascript
let today = new Date();

let year = today.getFullYear();
let month = today.getMonth() + 1;
let date = today.getDate();
let day = today.getDay();
```

`getFullYear()`  
Date 객체의 연도를 가져온다.

`getMonth()`  
Date 객체의 월 정보를 가져온다.  
1월은 0으로 표현됨(0~11)

`getDate()`  
Date 객체의 일자 정보를 가져온다. (0~31)

`getDay()`  
Date 객체의 요일 정보를 가져온다. (0~6)  
일요일이 0, 월요일이 1, 토요일이 6으로 표현됨.

## 현재 시간/분/초/밀리초 구하기

```javascript
let today = new Date();

let hours = today.getHours();
let minutes = today.getMinutes();
let seconds = today.getSeconds();
let milliseconds = today.getMilliseconds();
```

`getHours()`  
Date 객체의 시간을 가져온다. (0~23)

`getMinutes()`  
Date 객체의 분 정보를 가져온다. (0~59)

`getSeconds()`  
Date 객체의 초 정보를 가져온다. (0~59)

`getMilliseconds()`  
Date 객체의 밀리초 정보를 가져온다. (0~999)

---

```javascript
let today = new Date();

console.log(today.toLocaleDateString());
console.log(today.toLocaleTimeString());
console.log(today.toLocaleString());

console.log(today.toLocaleDateString("en-US"));
```

`toLocaleDateString()`,
`toLocaleTimeString()`,
`toLocaleString()` 함수들은 브라우저에서 설정된 국가에서 사용되는 날짜, 시간 표현 형식으로 날짜와 시간을 보여준다.

우리나라에서는 보통 년/월/일 순서로 날짜를 표현하므로,  
toLocaleDateString() 함수를 사용하면 년/월/일 순서로 날짜를 표현해 준다.

toLocaleDateString에 'en-US'로 설정하면,  
미국에서 날짜를 표현하는 방식인 월/일/연도 순서로 날짜가 표현된다.
