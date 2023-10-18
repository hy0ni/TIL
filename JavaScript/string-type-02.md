# 문자열 공백 제거하기

- 문자열의 모든 공백 제거하기: trim()
- 문자열의 앞 공백 제거하기: trimStart()
- 문자열의 뒤 공백 제거하기: trimEnd()

## trim()

`trim()` 함수는 문자열의 양쪽 끝에서 공백을 제거하고 원본 문자열을 수정하지 않고 새 문자열을 반환한다.

```javascript
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trim());
// Expected output: "Hello world!";
```

## trimStart()

`trimStart()` 함수는 문자열의 시작 부분에서 공백을 제거하고 원본 문자열을 수정하지 않고 새 문자열을 반환한다.

```javascript
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trimStart());
// Expected output: "Hello world!   ";
```

## trimEnd()

`trimEnd()` 함수는 문자열 끝에서 공백을 제거하고 원본 문자열을 수정하지 않고 새 문자열을 반환한다.

```javascript
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trimEnd());
// Expected output: "   Hello world!";
```
