# 문자열에서 원하는 index의 문자 가져오기 (3가지 방법)

1. charAt()
2. substring()
3. slice()

## charAt()

`charAt()` 함수는 전달된 파라미터의 index에 위치한 글자를 리턴한다.

```javascript
const str = "Hello World";

console.log(str.charAt(0)); // "H"
console.log(str.charAt(1)); // "e"
console.log(str.charAt(2)); // "l"

console.log(str.charAt(str.length - 1)); // "d"
```

첫 글자의 index 0부터 시작.
`str.charAt(str.length -1)`
마지막 글자의 index는 **전체 문자열의 길이 -1**로 가져올 수 있다.

## substring()

`substring()` 함수는 문자열의 시작 index부터 끝 index까지 문자열의 일부를 반환한다.<br>
끝 index가 제공되지 않은 경우 문자열의 끝까지 반환한다.

```javascript
const str = "Hello World";

console.log(str.substring(1, 3)); // "el"
console.log(str.substring(2)); // "llo World"
```

## slice()

`slice()` 함수는 원본 문자열을 수정하지 않고 이 문자열의 섹션을 추출해 새 문자열로 반환한다.

`substring()` 함수와 동일하게 문자열의 시작 index부터 끝 index까지 문자열의 일부를 반환한다.<br>
끝 index가 제공되지 않은 경우 문자열의 끝까지 반환한다.

```javascript
const str = "Hello World";

console.log(str.slice(2, 5)); // "llo"
console.log(str.slice(3)); // "lo World"
```
