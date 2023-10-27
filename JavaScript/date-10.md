# 함수 실행 시간 측정하기

현재 시간을 구하는 방법으로 함수의 실행 시간 계산하기.

```javascript
function test() {
  let sum = 0;
  for (let i = 1; i <= 1000000; i++) {
    sum = sum + i;
  }
}

let start = new Date(); // 시작
test();
let end = new Date(); // 종료

console.log(end - start); // 경과시간(밀리초)
```

`let start = new Date()`<br>
실행 시간을 측정할 함수 시작 전의 현재 시간을 측정한다.

`test()`<br>
실행 시간을 측정할 함수를 실행한다.

`let end = new Date()`<br>
함수가 종료된 시점의 현재 시간을 end에 저장한다.

`end - start`<br>
'함수가 종료된 시점의 시간 - 함수가 시작되기 직전 시점의 시간'을 계산하면<br>
두 시간 사이의 경과시간을 밀리초 단위로 반환한다.
