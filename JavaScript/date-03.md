# 날짜 계산하기 (년/월/일 더하기, 빼기)

- [날짜 계산하기 (년/월/일 더하기, 빼기)](#날짜-계산하기-년월일-더하기-빼기)
  - [연도 더하기, 빼기](#연도-더하기-빼기)
  - [월 더하기, 빼기](#월-더하기-빼기)
  - [일자 더하기, 빼기](#일자-더하기-빼기)

## 연도 더하기, 빼기

```javascript
let date = new Date(2023, 1, 1);
console.log(`기준일자 : ${date}`);

date.setFullYear(date.getFullYear() + 1);
console.log(`1년 후 : ${date}`);

date = new Date(2023, 1, 1);
date.setFullYear(date.getFullYear() - 1);
console.log(`1년 전 : ${date}`);
```

date 객체에서 `getFullYear()` 함수를 이용해서 연도를 추출한 후,  
해당 연도에 1을 더하거나 빼서 1년 후와 1년 전의 연도를 구하고,  
그 값을 다시 `setFullYear()` 함수를 사용해서 원래의 Date 객체의 연도를 변경해 준다.

## 월 더하기, 빼기

```javascript
let date = new Date(2023, 0, 31);
console.log(`기준일자 :  ${date.toLocaleString()}`); //  2023. 1. 31. 오전 12:00:00

date.setMonth(date.getMonth() + 1);
console.log(`1달 후 :  ${date.toLocaleString()}`); // 2023. 3. 3. 오전 12:00:00

date = new Date(2023, 0, 31);
date.setMonth(date.getMonth() - 1);
console.log(`1달 전 :  ${date.toLocaleString()}`); // 2022. 12. 31. 오전 12:00:00
```

1달 후, 1달 전의 날짜를 계산하기 위해 `getMonth()`, `setMonth()` 함수를 사용한다.

`date.setMonth(date.getMonth() + 1)`
1월 31일의 한 달 후 날짜를 계산했을 때 3월 3일이라고 나오는데  
이 경우 2023년 1월 31일에 '월'의 숫자만 2월로 바꿔끼워 2023년 2월 31일이 되기 때문이다.

하지만 2월의 마지막 날은 28일이고 31일은 없다.  
그래서 브라우저는 31-28=3을 적용해 3월 3일이라고 표시한다.

1월 31일의 한 달 후 날짜인 2월 28일이라는 결과를 얻기 위해서는 `말일자를 보정하는 로직을 추가`해야 한다.  
이 같은 현상은 윤년인 해의 2월 29일에서 1년을 더하거나, 뺄 때도 발생한다.

## 일자 더하기, 빼기

```javascript
let date = new Date(2023, 0, 31);
console.log(`기준일자 : ${date.toLocaleString()}`); // 2023. 1. 31. 오전 12:00:00

date.setDate(date.getDate() + 1);
console.log(`1일 후 : ${date.toLocaleString()}`); // 2023. 2. 1. 오전 12:00:00

date = new Date(2023, 0, 31);
date.setDate(date.getDate() - 1);
console.log(`1일 전 : ${date.toLocaleString()}`); // 2023. 1. 30. 오전 12:00:00
```

연도 계산, 월 계산과 마찬가지로 `setDate()`, `getDate()` 함수를 이용하여 어제와 내일 날짜를 계산한다.
