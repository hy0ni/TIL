# do..while 반복문

```javascript
do {
  // 반복할 코드
} while (조건문);
```

do...while문은 조건문을 판단하기 전에 do 블록의 코드를 먼저 실행한다.<br>
그리고, 조건문을 판단하여, 조건문의 결과가 true이면 do 블록의 코드를 다시 실행한다.<br>
이 과정을 반복.

```javascript
let i = 1;
do {
  console.log(`${i}번 째 반복문`);
  i++;
} while (i < 1);

// Expected output: 1번째 반복문
```

## while문과 do...while의 차이점

```javascript
let j = 1;
while (j < 1) {
  console.log(`${j}번째 반복문`);
  j++;
}
// output:
```

`while문`은 처음 while문을 실행시켰을 때 while문의 결과가 false이면,<br>
while문 안의 코드블록은 한 번도 실행되지 않을 수 있다.

`do...while문`은
조건문의 결과와 상관없이 무조건 do 블록의 코드가 적어도 1번은 실행된다.
