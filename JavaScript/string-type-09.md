# 문자열을 배열로 변환하기 split()

## split()

`split()`함수는 String 객체를 지정한 구분자를 이용하여 여러 개의 문자열로 나눈다.

## split() 함수 사용하여 문자열 배열로 변환하기

```javascript
const str = "apple banana orange cherry pear";
const strCopy = str.split();

console.log(strCopy); // [apple banana orange]
console.log(strCopy.length); // 1
```

파라미터로 값을 전달하지 않을 경우 문자열 전체를 길이(length)가 1인 배열에 담아 리턴한다.

### 구분자로 문자열 분리 및 배열 변환하기

```javascript
const str = "apple banana orange";

const words = str.split(" ");
console.log(words); // ['apple', 'banana', 'orange']
console.log(Array.isArray(words)); // true
console.log(words.length); // 3
```

`str.split(" ")` 문자열을 공백으로 분리하고 분리된 문자들을 배열로 변환한다.

`Array.isArray(words)` <br>
배열인지 판단하기 true 반환함.

`words.length`<br>
구분자로 문자열을 분리한 후 배열로 변환하였기 때문에 길이(length)는 3이 된다.
