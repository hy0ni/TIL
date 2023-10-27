# 시간 계산하기 (시/분/초/ 더하기, 빼기)

- 시간 더하기/빼기
- 분 더하기/빼기
- 초 더하기/빼기

## 시간 더하기/빼기

```javascript
let date = new Date(2023, 0, 1);
console.log(`기준일자 : ${date}`); // 기준일자 : Sun Jan 01 2023 00:00:00 GMT+0900 (한국 표준시)

date.setHours(date.getHours() + 10);
console.log(`10시간 후 : ${date}`); // 10시간 후 : Sun Jan 01 2023 10:00:00 GMT+0900 (한국 표준시)

date = new Date(2023, 0, 1);
date.setHours(date.getHours() - 10);
console.log(`10시간 전 : ${date}`); // 10시간 전 : Sat Dec 31 2022 14:00:00 GMT+0900 (한국 표준시)
```

`getHours()`<br>
Date 객체의 시간을 가져온다. (0~23)

`setHours()`<br>
현지 시간에 따라 지정된 날짜의 시간을 설정한다.(분, 초, 밀리초도 설정할 수 있음)

## 분 더하기/빼기

```javascript
let date = new Date(2023, 0, 1);
console.log(`기준일자 : ${date}`); // 기준일자 : Sun Jan 01 2023 00:00:00 GMT+0900 (한국 표준시)

date.setMinutes(date.getMinutes() + 100);
console.log(`100분 후 : ${date}`); // 100분 후 : Sun Jan 01 2023 01:40:00 GMT+0900 (한국 표준시)

date = new Date(2023, 0, 1);
date.setMinutes(date.getMinutes() - 100);
console.log(`100분 전 : ${date}`); // 100분 전 : Sat Dec 31 2022 22:20:00 GMT+0900 (한국 표준시)
```

`getMinutes()`<br>
Date 객체의 분 정보를 가져온다. (0~59)

`setMinutes()`<br>
현지 시간에 따라 지정된 날짜의 분을 설정한다.

## 초 더하기/빼기

```javascript
let date = new Date(2023, 0, 1);
console.log(`기준일자 : ${date}`); // 기준일자 : Sun Jan 01 2023 00:00:00 GMT+0900 (한국 표준시)

date.setSeconds(date.getSeconds() + 100);
console.log(`100초 후 : ${date}`); // 100초 후 : Sun Jan 01 2023 00:01:40 GMT+0900 (한국 표준시)

date = new Date(2023, 0, 1);
date.setSeconds(date.getSeconds() - 100);
console.log(`100초 전 : ${date}`); // 100초 전 : Sat Dec 31 2022 23:58:20 GMT+0900 (한국 표준시)
```

`getSeconds()`<br>
Date 객체의 초 정보를 가져온다. (0~59)

`setSeconds()`<br>
현지 시간에 따라 지정된 날짜의 초를 설정한다.
