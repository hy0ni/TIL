# 문자열 날짜로 변환하기

```javascript
const str = "2023-10-10";
const strArr = str.split("-");
const date = new Date(strArr[0], strArr[1] - 1, strArr[2]);

console.log(date); // Tue Oct 10 2023 00:00:00 GMT+0900 (한국 표준시)
```

`str.split('-') `  
문자열의 연월일이 '-'로 구분되므로, split() 함수를 이용하여 문자열을 잘라 배열에 담는다.

`new Date(strArr[0], strArr[1]-1, strArr[2])`  
Date(년, 월, 일) 함수를 이용하여, 날짜로 변환한다.

Date의 파라미터로 '월'을 넘겨줄 때는 '-1'을 해줘야 한다.  
0은 1월, 1은 2월을 의미하기 때문이다.  
즉, Date(2023, 10, 10)은 2023년 10월 10일을 의미한다.
