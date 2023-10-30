# 난수 생성하기 Random Number

- [난수 생성하기 Random Number](#난수-생성하기-random-number)
  - [Math.random()](#mathrandom)
  - [범위를 지정한 난수 생성하기](#범위를-지정한-난수-생성하기)
  - [난수 생성 함수 만들기 (범위 지정)](#난수-생성-함수-만들기-범위-지정)
    - [min \<= number \<= max ( max 값 포함)](#min--number--max--max-값-포함)
    - [min \<= number \< max (max 값 불포함)](#min--number--max-max-값-불포함)

## Math.random()

```javascript
Math.random();
```

Math.random() 함수는 0~1(1은 미포함) 구간에서 부동소수점의 난수를 생성한다.

```javascript
const random = Math.random();
```

이 코드는 실행할 때마다 다른 난수를 생성한다.
생성된 값은 0~1 사이의 부동소수점 값이다. (1은 미포함)

## 범위를 지정한 난수 생성하기

Math.random() 함수는 0~1 사이의 부동소수점 난수를 생성하는데,  
정수인 난수를 생성하기 위해서는  
Math.random() 함수와 Math.floor() 함수를 함께 사용해야 한다.

`Math.floor() 함수`  
소수점 1번째 자리를 버림하여 정수를 리턴하는 함수

```javascript
const random1 = Math.random();
const random2 = Math.floor(Math.random());
const random3 = Math.floor(Math.random() * 10);
const random4 = Math.floor(Math.random() * 11);
const random5 = Math.floor(Math.random() * 100);
```

`Math.random()`  
Math.random() 함수는 0~1 사이의 실수를 리턴(1 미포함)

`Math.floor(Math.random())`  
Math.floor() 함수는 소수점 첫 번째 자리 이후의 숫자를 버림하고, 정수를 리턴한다.
Math.random() 함수는 0~0.99999...인 숫자를 리턴하기 때문에,
Math.floor(Math.random()) 의 결과는 항상 0이 된다.

`Math.floor(Math.random() * 10)`  
Math.random() 함수의 결과는 0~0.99999...이고,
Math.random() \* 10 의 결과는 0~9.99999...이다.

Math.floor(Math.random() \* 10)의 결과는 0~9 범위의 정수다.

`Math.floor(Math.random() * 11)`  
10을 포함하는 랜덤한 정수를 얻고 싶다면  
Math.random() 함수의 결과에 11을 곱하고, 소수점 이하를 버림한다.

`Math.floor(Math.random() * 100)`  
0~99 범위의 랜덤한 정수를 얻고 싶다면,  
Math.random() 함수의 결과에 100을 곱해주고, 소수점 이하를 버림한다.

## 난수 생성 함수 만들기 (범위 지정)

### min <= number <= max ( max 값 포함)

```javascript
function rand(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

console.log(rand(1, 5));
```

최소값을 지정하고 싶을 때는  
Math.random() \* (max - min + 1) 값을 계산하고, 소수점 이하를 버림 한다.  
그리고, min 값을 더해준다.

min ~ max 값까지의 정수 랜덤 넘버를 만들어주는 함수  
1 ~ 5까지의 랜덤한 정수를 리턴한다.

### min <= number < max (max 값 불포함)

```javascript
function rand(min, max) {
  return Math.floor(Math.random() * (max - min)) + min;
}

console.log(rand(1, 5));
```

max값을 포함하지 않는, min ~ max 값까지의 정수 랜덤 넘버를 만들어주는 함수
