# 두 날짜 사이 경과 일수 계산하기

```javascript
// 2023년 10월 1일
const date1 = new Date(2023, 9, 1);
// 2023년 10월 3일
const date2 = new Date(2023, 9, 3);

const elapsedMSec = date2.getTime() - date1.getTime(); // 172800000
const elapsedDay = elapsedMSec / 1000 / 60 / 60 / 24; // 2
```

Date의 getTime() 메서드는<br>
'1970년 1월 1일 00:00:00 UTC'로부터 주어진 시간 사이의 경과시간(밀리초)을 리턴한다.

'1970년 1월 1일 00:00:00 UTC'의 getTime() 값은 0<br>
'1970년 1월 1일 00:00:01 UTC'의 getTime() 값은 1000

`const elapsedDay = elapsedMSec / 1000 / 60 / 60 / 24`<br>
종료일자.getTime() - 시작일자.getTime()을 계산하면<br>
두 날짜 사이의 '경과 밀리초'를 얻을 수 있다.

- 1초 = 1000 밀리초
- 1분 = 60초
- 1시간 = 60분
- 1일 = 24시간
