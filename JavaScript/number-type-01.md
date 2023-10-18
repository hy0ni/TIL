# 올림 Math.ceil() / 내림 Math.floor() / 반올림 Math.round() / 소수점 반올림 tofixed(), toprecision()

- [올림 Math.ceil() / 내림 Math.floor() / 반올림 Math.round() / 소수점 반올림 tofixed(), toprecision()](#올림-mathceil--내림-mathfloor--반올림-mathround--소수점-반올림-tofixed-toprecision)
  - [올림 Math.ceil()](#올림-mathceil)
    - [정수 올림 (음수 포함)](#정수-올림-음수-포함)
    - [자릿수 지정 (소수점 이하, 10단위, 100단위)](#자릿수-지정-소수점-이하-10단위-100단위)
  - [내림 Math.floor()](#내림-mathfloor)
    - [정수 내림 (음수 포함)](#정수-내림-음수-포함)
    - [자릿수 지정 (소수점 이하, 10단위, 100단위)](#자릿수-지정-소수점-이하-10단위-100단위-1)
  - [반올림 Math.round()](#반올림-mathround)
    - [정수 반올림 (음수 포함)](#정수-반올림-음수-포함)
    - [자릿수 지정 (소수점 이하, 10단위, 100단위)](#자릿수-지정-소수점-이하-10단위-100단위-2)
    - [소수점 숫자 정밀도 문제](#소수점-숫자-정밀도-문제)
  - [소수점 반올림 toFixed(), toPrecision()](#소수점-반올림-tofixed-toprecision)
    - [toFixed() 함수](#tofixed-함수)
    - [toPrecision() 함수](#toprecision-함수)

## 올림 Math.ceil()

`Math.ceil()` 함수는 올림 처리한 정수를 리턴한다.

### 정수 올림 (음수 포함)

```javascript
// 올림
const ceil_1 = Math.ceil(1); // 1
const ceil_2 = Math.ceil(1.222); // 2
const ceil_3 = Math.ceil(1.5); // 2
const ceil_4 = Math.ceil(1.6); // 2

// null 또는 0인 경우
const ceil_5 = Math.ceil(null); // 0
const ceil_6 = Math.ceil(0); // 0

// 음수인 경우
const ceil_7 = Math.ceil(-1); // -1
const ceil_8 = Math.ceil(-1.111); // -1
const ceil_9 = Math.ceil(-1.5); // -1
const ceil_10 = Math.ceil(-1.666); // -1
```

### 자릿수 지정 (소수점 이하, 10단위, 100단위)

```javascript
// 소수점이하
const ceil_1 = Math.ceil(1.222 * 10) / 10; // 1.3
const ceil_2 = Math.ceil(1.222 * 100) / 100; // 1.23

// 10단위, 100단위
const ceil_3 = Math.ceil(1222 / 10) * 10; // 1230
const ceil_4 = Math.ceil(1222 / 100) * 100; // 1300
```

**소수점 아래에서 값을 올림 하고 싶은 경우**

처리하려는 숫자의 부동소수점을 올림 하고 싶은 숫자 앞까지 옮겨준 후 (10, 100, 1000... 숫자를 곱하여)
Math.ceil() 함수를 적용하고 다시 소수점의 위치를 원복 시킨다. (10, 100, 1000.. 숫자로 나누어서)

**10단위, 100단위에서 올림 하고 싶은 경우**

숫자의 부동소수점을 올림 하고 싶은 숫자 앞까지 옮겨준 후
(올림하고 싶은 숫자가 10, 100의 단위이므로 해당 숫자로 나눈다.)
Math.ceil() 함수를 적용하고 다시 소수점의 위치를 원복시킨다.
(10, 100.. 숫자로 다시 곱해준다.)

## 내림 Math.floor()

`Math.floor()` 함수는 내림 처리한 정수를 리턴한다.

### 정수 내림 (음수 포함)

```javascript
// 내림
const floor_1 = Math.floor(1); // 1
const floor_2 = Math.floor(1.222); // 1
const floor_3 = Math.floor(1.5); // 1
const floor_4 = Math.floor(1.666); // 1

// null 또는 0인 경우
const floor_5 = Math.floor(null); // 0
const floor_6 = Math.floor(0); // 0

// 음수인 경우
const floor_7 = Math.floor(-1); // -1
const floor_8 = Math.floor(-1.111); // -2
const floor_9 = Math.floor(-1.5); // -2
const floor_10 = Math.floor(-1.666); // -2
```

### 자릿수 지정 (소수점 이하, 10단위, 100단위)

```javascript
// 소수점이하
const floor_1 = Math.floor(1.666 * 10) / 10; // 1.6
const floor_2 = Math.floor(1.666 * 100) / 100; // 1.66

// 10단위, 100단위
const floor_3 = Math.floor(1666 / 10) * 10; // 1660
const floor_4 = Math.floor(1666 / 100) * 100; // 1600
```

## 반올림 Math.round()

소수점 이하의 값이 0.5보다 크면, 입력받은 수보다 다음으로 높은 절대값을 가지는 정수를 리턴한다.<br>
소수점 이하의 값이 0.5보다 작으면, 입력받은 수보다 절대값이 더 낮은 정수를 리턴한다.<br>
소수점 이하의 값이 0.5와 같으면, 입력받은 수보다 큰 다음 정수를 리턴한다.

### 정수 반올림 (음수 포함)

```javascript
// 반올림
const round_1 = Math.round(1); // 1
const round_2 = Math.round(1.222); // 1
const round_3 = Math.round(1.5); // 2
const round_4 = Math.round(1.666); // 2

// null 또는 0인 경우
const round_5 = Math.round(null); // 0
const round_6 = Math.round(0); // 0

// 음수인 경우
const round_7 = Math.round(-1); // -1
const round_8 = Math.round(-1.111); // -1
const round_9 = Math.round(-1.5); // -1
const round_10 = Math.round(-1.666); // -2
```

### 자릿수 지정 (소수점 이하, 10단위, 100단위)

```javascript
// 소수점이하
const round_1 = Math.round(1.222 * 10) / 10; // 1.2
const round_2 = Math.round(1.5 * 10) / 10; // 1.5
const round_3 = Math.round(1.888 * 10) / 10; // 1.9

// 10단위
const round_4 = Math.round(1001 / 10) * 10; // 1000
const round_5 = Math.round(1005 / 10) * 10; // 1010
const round_6 = Math.round(1008 / 10) * 10; // 1010
```

### 소수점 숫자 정밀도 문제

소수점 이하의 값을 올림(ceil), 내림(floor), 반올림(round) 처리할 때
부동 소수점의 정밀도 문제 때문에 예상하지 못한 결과가 나오기도 한다.

```javascript
// 부동소수점 오차 확인 (1.005 반올림)
const n1 = 1.005 * 100; // 100.49999999999999
const round_1 = Math.round(1.005 * 100) / 100; // 1

// 부동소수점 오차 보정 (1.005 반올림)
const n2 = (1.005 + Number.EPSILON) * 100; // 100.50000000000001
const round_2 = Math.round((1.005 + Number.EPSILON) * 100) / 100; // 1.01
```

1.005 \* 100의 결괏값이 100.5가 나올 거라 예상했지만 실제 결과는 100.49999999999999가 나온다.<br>
JavaScript에서 실수를 처리하는 방식 때문에 약간의 오차가 발생된다.

`Math.round(1.005 * 100) / 100;` 이 경우 1.01의 결괏값이 반환되어야 하지만 위와 같은 이유로 결괏값은 1이 나옴.

부동 소수점 오차를 해결하기 위해 Number.EPSILON 값을 더해 준 뒤, 그 값으로 반올림을 처리해도 정확하게 100.5가 나오지 않음.
오차는 많이 줄어든 게 확인된다.

\*\*정적 `Number.EPSILON` 데이터 속성은 1과 1보다 큰 가장 작은 부동 소수점 수 사이의 차이를 나타냅니다.

## 소수점 반올림 toFixed(), toPrecision()

### toFixed() 함수

```javascript
numObj.toFixed([digits]);
```

부동소수점(Floating Point) 숫자를 고정소수점(Fixed Point) 숫자로 바꿔서 리턴한다.

이때, 파라미터로 숫자(digits)를 전달하면, 'digits'만큼의 소수점 이하 자릿수를 가지는 문자열로 리턴해준다.<br>
원본 숫자(numObj)의 소수점 이하 길이가 'digits'보다 길면 숫자를 반올림하고, 짧으면 뒤를 0으로 채워서 리턴한다.

```javascript
// 소수점이하
const fixed_1 = (1.222).toFixed(1); // 1.2
const fixed_2 = (1.5).toFixed(1); // 1.5
const fixed_3 = (1.777).toFixed(1); // 1.8

// 음수
const fixed_4 = (-1.222).toFixed(1); // -1.2
const fixed_5 = (-1.5).toFixed(1); // -1.5
const fixed_6 = (-1.777).toFixed(1); // -1.8
```

### toPrecision() 함수

```javascript
numObj.toPrecision([precision]);
```

숫자(numObj)를 파라미터로 전달된 유효 자릿수(precision) 길이의 문자열로 만들어서 리턴한다.

만약, 유효 자릿수(precision)가 원본 숫자의 자릿수보다 작으면 반올림한 값을 리턴한다.

```javascript
// 1.소수점이하
const precision_1 = (1.222).toPrecision(2); // 1.2
const precision_2 = (1.5).toPrecision(2); // 1.5
const precision_3 = (1.777).toPrecision(2); // 1.8

// 2.음수
const precision_4 = (-1.222).toPrecision(2); // -1.2
const precision_5 = (-1.5).toPrecision(2); // -1.5
const precision_6 = (-1.777).toPrecision(2); // -1.8
```
