# 문자열 뒤에서 자르기 slice()

## slice() 함수 사용하기

```javascript
str.slice(beginIndex[, endIndex])
```

`slice()` 함수는 어떤 배열의 beginIndex부터 endIndex까지(end 미포함)에 대한 얕은 복사본을 새로운 배열 객체로 반환한다. 원본 배열은 바뀌지 않음. <br>
index는 0부터 시작.

```javascript
const str = "hello";

const lastStr2 = str.slice(-2); // lo
const lastStr3 = str.slice(-2, str.length); // lo
```

beginIndex or endIndex의 값으로 음수가 입력되면,
index 값은 문자열의 길이 + index 값으로 계산됨.

`str.slice(-2)`

endIndex 파라미터가 생략되면,
slice() 함수는 문자열의 마지막 글자까지 문자열을 잘라 리턴한다.

`str.slice(-2, str.length)`

str의 문자열의 길이는 5이고, beginIndex 값은 -2이므로,
str.slice(5+(-2),5), 즉 str.slice(3, 5)로 계산되어 문자열의 마지막 2글자를 리턴한다.

`str.slice(-2)`<br>
`str.slice(-2, str.length)`<br>
같은 결과값을 낸다.
