# 문자열의 첫 글자만 대문자로 변환하기

1. 첫 번째 글자 찾기
2. 첫 번째 글자를 대문자로 변환하기
3. 첫 번째 글자를 제외한 나머지 글자 찾기
4. 2에서 대문자로 변환한 첫 번째 글자와 3에서 찾은 나머지 글자 이어 붙이기

## 1. 첫 번째 글자 찾기

```javascript
const str = "hello";

const firstChar1 = str.charAt(0); // h
const firstChar2 = str[0]; // h
```

특정 위치의 문자를 찾기 위해 `charAt() 함수` 또는 `대괄호([])`를 사용할 수 있다.

## 2. 첫 번째 글자를 대문자로 변환하기

```javascript
const str = "hello";

const firstChar = str.charAt(0); // h

const firstCharUpper = firstChar.toUpperCase(); // H
```

toUpperCase() 함수를 사용하여 첫 번째 글자 대문자로 변환.

## 3. 첫 번째 글자를 제외한 나머지 글자 찾기

```javascript
const str = "hello";

const leftChar = str.slice(1, str.length); // ello
```

`slice()` 함수를 이용하여 1번째 자리부터 str.length를 추출.

## 4. 2에서 대문자로 변환한 첫 번째 글자와 3에서 찾은 나머지 글자 이어 붙이기

```javascript
const result = firstCharUpper + leftChar; // Hello
```

문자열을 이어붙일 때는 concat() 함수나 '+'연산자를 사용할 수 있음.

## 임시 변수의 사용을 줄여 간결하게 만들기

```javascript
const result = `${str[0].toUpperCase()}${str.slice(1, str.length)}`;
console.log(result); // Hello
```
