# 숫자를 문자열로 변환하기 (4가지 방법)

1. toString()
2. String()
3. Template String (템플릿 문자열)
4. 빈 문자열 이어붙이기

## toString()

```javascript
const num = 10;
const str = num.toString();

console.log(typeof num); // number
console.log(typeof str); // string
```

## String()

```javascript
const num = 10;
const str = String(num);

console.log(typeof num); // number
console.log(typeof str); // string
```

## Template String (템플릿 문자열)

템플릿 문자열(``) 사용하기

```javascript
const num = 10;

console.log(typeof num); // number
console.log(typeof `num`); // string
```

## 빈 문자열 이어붙이기

숫자에 빈 문자열("") 연결하기

```javascript
const num = 10;
const str = num + "";
console.log(typeof num); // number
console.log(typeof str); // string
```
