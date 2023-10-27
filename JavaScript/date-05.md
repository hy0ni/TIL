# 마지막 날짜(말일)/윤달/윤년 처리하기 Date()

- Date() 함수를 이용한 날짜 계산에서 발생하는 말일자 문제
- 날짜 계산(Date)에서 마지막 날짜/윤달/윤년 처리하기

## Date() 함수를 이용한 날짜 계산에서 발생하는 말일자 문제

```javascript
let date = new Date(2023, 0, 31);
console.log(`기준일자 : ${date.toLocaleString()}`); // 기준일자 : 2023. 1. 31. 오전 12:00:00

date.setMonth(date.getMonth() + 1);
console.log(`1달 후 : ${date.toLocaleString()}`); // 1달 후 : 2023. 3. 3. 오전 12:00:00

date = new Date(2023, 0, 31);
date.setMonth(date.getMonth() - 1);
console.log(`1달 전 : ${date.toLocaleString()}`); // 1달 전 : 2022. 12. 31. 오전 12:00:00
```

월의 마지막 날짜에 1개월을 더하거나 뺐을 때 문제가 발생한다.

2월의 말일자인 2월 28일(또는 2월 29일, 윤달인 경우)을 구하기 위해<br>
1월 31일 + 1개월을 계산하면<br>
1월 31+1개월 = 2월 31일이라고 계산하게 되고,<br>
실제로 2월 31일은 존재하지 않으므로,<br>
2월의 마지막 날짜인 2월 28일로부터 3일 후의 날짜(31-28 = 3)를 적용하여,<br>
3월 3일이라고 표현된다.

## 날짜 계산(Date)에서 마지막 날짜/윤달/윤년 처리하기

2월 28일을 얻기 위해서는 별도로 로직을 구현해야 한다.

```javascript
// 기준일자
let date = new Date(2023, 0, 31);
console.log(`기준일자 : ${date.toLocaleString()}`); // 기준일자 : 2023. 1. 31. 오전 12:00:00

// 1달 후의 1일
let nextMonthFirstDate = new Date(date.getFullYear(), date.getMonth() + 1, 1);
console.log(`1달 후의 1일 : ${nextMonthFirstDate.toLocaleString()}`); // 1달 후의 1일 : 2023. 2. 1. 오전 12:00:00

// 1달 후의 말일
let nextMonthLastDate = new Date(
  nextMonthFirstDate.getFullYear(),
  nextMonthFirstDate.getMonth() + 1,
  0
);
console.log(`1달 후의 말일 ${nextMonthLastDate.toLocaleString()}`); // 1달 후의 말일 2023. 2. 28. 오전 12:00:00
```

먼저, 기준이 되는 달(1월 31일),
1월 31일로부터 "1달 후의 첫 번째 날짜(2월 1일)"와 "마지막 날짜(2월 28일)"을 계산한다.

월의 마지막 일자를 계산하는 방법을 응용해서 말일자를 체크하는 함수를 작성하고,<br>
이 함수를 사용하여 날짜를 계산해야 한다.

```javascript
function addMonth(date, month) {
  // month달 후의 1일
  let addMonthFirstDate = new Date(
    date.getFullYear(),
    date.getMonth() + month,
    1
  );

  // month달 후의 말일
  let addMonthLastDate = new Date(
    addMonthFirstDate.getFullYear(),
    addMonthFirstDate.getMonth() + 1,
    0
  );

  let result = addMonthFirstDate;
  if (date.getDate() > addMonthLastDate.getDate()) {
    result.setDate(addMonthLastDate.getDate());
  } else {
    result.setDate(date.getDate());
  }

  return result;

  let janLastDate = new Date(2023, 0, 31);
  // 말일 테스트
  console.log(`기준일자 :  ${janLastDate.toLocaleString()}`); // 기준일자 :  2023. 1. 31. 오전 12:00:00
  console.log(`1달 후 :  ${addMonth(janLastDate, 1).toLocaleString()}`); // 1달 후 :  2023. 2. 28. 오전 12:00:00
  console.log(`2달 후 :  ${addMonth(janLastDate, 2).toLocaleString()}`); // 2달 후 :  2023. 3. 31. 오전 12:00:00
  console.log(`3달 후 :  ${addMonth(janLastDate, 3).toLocaleString()}`); // 3달 후 :  2023. 4. 30. 오전 12:00:00
  console.log(`13달 후(윤년) :  ${addMonth(janLastDate, 13).toLocaleString()}`); // 13달 후(윤년) :  2024. 2. 29. 오전 12:00:00

  let janSomeDate = new Date(2023, 0, 11);
  // 중간날짜 테스트
  console.log(`기준일자 :  ${janSomeDate.toLocaleString()}`); // 기준일자 :  2023. 1. 11. 오전 12:00:00
  console.log(`1달 후 :  ${addMonth(janSomeDate, 1).toLocaleString()}`); // 1달 후 :  2023. 2. 11. 오전 12:00:00
  console.log(`2달 후 :  ${addMonth(janSomeDate, 2).toLocaleString()}`); // 2달 후 :  2023. 3. 11. 오전 12:00:00
  console.log(`3달 후 :  ${addMonth(janSomeDate, 3).toLocaleString()}`); // 3달 후 :  2023. 4. 11. 오전 12:00:00
  console.log(`13달 후(윤년) :  ${addMonth(janSomeDate, 13).toLocaleString()}`); // 13달 후(윤년) :  2024. 2. 11. 오전 12:00:00
}
```

말일 자 처리를 위해서 addMonth(date, month)라는 함수를 만든다.<br>
이 함수는 date(기준 일자)와 month(더해질 개월 수)를 파라미터로 받는다.

1. 기준 일자에 month 만큼 더한 월의 첫 번째 날짜를 구한다. (addMonthFirstDate)
2. month 만큼 더한 월의 마지막 날짜를 구한다. (addMonthLastDate)
3. 리턴 값(result) 변수를 선언하고, 1에서 계산한 값을 할당한다.
4. 파라미터로 받은 기준 일자의 날짜와 2에서 구한 날짜의 date 값(즉, 2자리 일자)을 비교하여 작은 값을 리턴 값의 date 값으로 할당해 준다.<br>
   즉, MIN(기준 일자의 날짜 중 date 값, 2에서 구한 날짜의 date 값)을 3에서 만든 리턴 값의 date 값으로 할당해 주는 것.
5. 마지막으로, addMonth() 함수를 호출해서 테스트를 해보면,
   원하는 대로 결과가 나오는 것을 확인할 수 있다.

보통은 월을 계산할 때 발생하는 말일 자 문제(윤달, 윤년 포함)를 해결하는 코드를 직접 로직을 구현해서 사용해도 되지만,<br>
이미 구현이 되어 있는 오픈소스들을 활용하는 것도 좋은 방법이다.
