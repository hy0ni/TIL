# 함수 파라미터(매개변수) 기본값 설정하기

## ES6이전

```javascript
function multiply(a, b) {
  if (b === undefined) {
    b = 1;
  }

  return a * b;
}

console.log(multiply(3, 2)); // 6
console.log(multiply(3)); // 3
```

ES6 이전의 Javascript에서는<br>
함수 매개변수의 기본값을 설정하기 위해<br>
함수의 안에서 조건문을 사용하여 매개변수의 값을 체크하고,<br>
기본값을 설정함.

multiply() 함수는<br>
두 번째 파라미터인 b가 입력되지 않으면 기본값을 '1'로 세팅한다.

## ES6

```javascript
function multiply(a, b = 1) {
  return a * b;
}

console.log(multiply(3, 2)); // 6
console.log(multiply(3)); // 3
```

ES6에서는 함수 매개변수의 기본값을 설정할 수 있다.

두 번째 파라미터 b가 입력되지 않으면 b의 값을 1로 세팅해서 계산한다.

파라미터가 입력되지 않는 경우 값이 어떻게 처리되는지 쉽게 알 수 있다.

함수 내부에 매개변수 유효성 체크(validation) 부분이 삭제되고, 함수의 원래 기능만 구현할 수 있게 된다.

가독성이 좋아짐.
