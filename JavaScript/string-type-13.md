# 문자열의 첫 글자 삭제하기

## substring() 사용하기

```javascript
string.substring(start, end);
```

`substring()` 함수는 string 객체의 start index부터 end index 전까지 문자열을 잘라서 리턴한다. end index를 입력하지 않으면 start index부터 문자열의 끝까지 리턴한다.

```javascript
const str = "hello";

const firstStrRemove = str.substring(1); // ello
```

## slice() 사용하기

```javascript
string.slice(start, end);
```

`slice()` 함수는 `substring()` 함수와 사용법이 거의 같다.
start index부터 end index 전까지 문자열을 잘라서 리턴한다. end index를 입력하지 않으면 start index부터 문자열의 끝까지 리턴한다.

```javascript
const str = "hello";

const firstStrRemove = str.slice(1); // ello
```
