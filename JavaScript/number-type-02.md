# 숫자가 정수인지 체크하기 (2가지 방법)

1. Number.isInteger()
2. 나머지 연산자(%) 활용

## Number.isInteger()

```javascript
Number.isInteger(value);
```

전달된 값이 정수인지 여부를 확인한다.

```javascript
Number.isInteger(10); // true
Number.isInteger(-10); // true
Number.isInteger(1.33); // false
```

## 나머지 연산자(%) 활용

정수는 1로 나누었을 경우 항상 나머지가 0이 된다.<br>
이를 이용하여 주어진 숫자가 정수인지 체크한다.

```javascript
function isInteger(number) {
  return number % 1 === 0;
}

isInteger(10); // true
isInteger(-10); // true
isInteger(1.33); // false
```
