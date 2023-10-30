# 해당 월의 마지막 날짜, 말일을 구하는 방법

```javascript
new Date(year, month, day);
```

```javascript
// 3월 1일
let date = new Date(2023, 2, 1);
console.log(date.toLocaleString()); // 2023. 3. 1. 오전 12:00:00

// 2월 28일(말일)
let lastDate = new Date(2023, 2, 0);
console.log(lastDate.toLocaleString()); // 2023. 2. 28. 오전 12:00:00
console.log(lastDate.getDate()); // 28

// 2월 27일
let lastDateBefore = new Date(2023, 2, -1);
console.log(lastDateBefore.toLocaleString()); // 2023. 2. 27. 오전 12:00:00
```

`let date = new Date(2023, 2, 1)`  
이 코드의 결과는 2023년 3월 1일이다.  
( month는 0~11까지의 숫자가 입력되어야 하고, 0은 1월이다.)

`let lastDate = new Date(2023, 2, 0)`  
2023년 3월 0일이 되지만 2023년 3월 0일은 없으므로  
3월 1일의 하루 전날인 2월의 마지막 날짜를 반환한다.

그래서, 결과는 2월의 마지막 날인 `2023년 2월 28일`이 된다.

마지막 날짜 2자리 숫자만 얻고 싶다면, getDate() 함수를 사용하면 된다.

`let lastDateBefore = new Date(2023, 2, -1)`  
2023년 3월 -1일은 없으므로,  
2023년 3월 1일의 2일 전날인 `2023년 2월 27일`을 반환하게 된다.

Date() 함수의 day란에 0 이하의 값을 입력하여, 해당 월의 1일을 기준으로, (|day|+1)의 전일자를 계산할 수 있다.
