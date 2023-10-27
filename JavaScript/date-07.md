# 경과 시간 계산하기 (시간, 분, 초)

두 시간 사이의 차이를 구하기 위해<br>
먼저 Date 객체의 getTime() 메서드를 이용해서<br>
지정된 날짜의 시간에 해당하는 숫자를 구하고, 그 차이를 계산한다.

##

```javascript
dateObj.getTime();
```

getTime() 메서드는 '1970년 1월 1일 00:00:00 UTC'로부터 주어진 시간 사이의 경과시간(밀리초)을 리턴한다.

'1970년 1월1 일 00:00:00 UTC'의 getTime() 값은 0<br>
'1970년 1월 1일 00:00:01 UTC'의 getTime() 값은 1000

```javascript
// 2023년 7월 1일 0시 0분 0초
const date1 = new Date(2023, 6, 1, 0, 0, 0);
// 2023년 7월 1일 2시 30분 4초
const date2 = new Date(2023, 6, 1, 2, 30, 4);

const elapsedMSec = date2.getTime() - date1.getTime(); // 9004000
const elapsedSec = elapsedMSec / 1000; // 9004
const elapsedMin = elapsedMSec / 1000 / 60; // 150.0666...
const elapsedHour = elapsedMSec / 1000 / 60 / 60; // 2.501111...
```

2023/7/1 0:0:0 ~ 2023/7/1 2:30:4 사이의 경과시간을 계산하고,
각 경과 시간을 초, 분, 시간 단위로 다시 환산한다.

`const elapsedMSec = date2.getTime() - date1.getTime()`<br>
두 시간(date1, date2)의 getTime() 값의 차는<br>
두 시간 사이의 경과시간(밀리 세컨드 단위)을 의미.

`const elapsedSec = elapsedMSec / 1000`<br>
밀리 세컨드(millisecond) 단위를 초 단위(second)로 변환하기 위해 1000으로 나눈다.

`const elapsedMin = elapsedMSec / 1000 / 60`<br>
밀리 세컨드(millisecond) 단위의 경과 시간을 초 단위(second)로 변환하기 위해 1000으로 나누고,<br>
이것을 분 단위(minute)로 변환하기 위해 60으로 다시 나눈다.

`const elapsedHour = elapsedMSec / 1000 / 60 / 60`<br>
밀리 세컨드(millisecond) 단위의 경과 시간을 초 단위(second)로 변환하기 위해 1000으로 나누고,<br>
이것을 분 단위(minute)로 변환하기 위해 60으로 다시 나눈다.
그리고, 시간 단위(hour)로 변환하기 위해 다시 60으로 나눈다.

```javascript
// 2023년 7월 1일 0시 0분 0초
const date1 = new Date(2023, 6, 1, 0, 0, 0);
// 2023년 7월 1일 2시 30분 4초
const date2 = new Date(2023, 6, 1, 2, 30, 4);

const elapsedMSec = date2 - date1; // 9004000
const elapsedSec = elapsedMSec / 1000; // 9004
const elapsedMin = elapsedMSec / 1000 / 60; // 150.0666...
const elapsedHour = elapsedMSec / 1000 / 60 / 60; // 2.501111...
```

`const elapsedMSec = date2 - date1`<br>
Date 객체의 연산을 할 때 getTime() 메서드를 사용하지 않고,<br>
Date 객체끼리 연산을 해도 getTime() 메서드를 사용하여 연산한 것과 같은 결과를 얻을 수 있다.
