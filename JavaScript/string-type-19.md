# 콤마 제거 하기 (2가지 방법)

1. replace() 함수 사용하기
2. split(), join() 함수 사용하기

## replace() 함수 사용하기

```javascript
const numberStr = "12,34,56";
const number = numberStr.replace(",", "");

console.log(number); // 1234,56
```

`numberStr.replace(",", "")`  
`replace()` 함수는 2개의 파라미터를 입력받고,
문자열에서 첫 번째 파라미터(",")를 두 번째 파라미터("")로 치환해 준다.

`replace()` 함수는 첫 번째로 발견한 값만 치환해 줌.

문자열 전체에서 모든 값(첫 번째 파라미터와 일치하는)을 치환해 주기 위해서는 반복문을 사용하거나 정규식을 사용해야 한다.

```javascript
const numberStr = "12,34,56";
const number = numberStr.replace(/,/g, "");

console.log(number); // 123456
```

replace()의 첫 번째 파라미터로 일반 문자열 대신 정규식을 넣어준다.  
`/,/g`

정규식은 '/'로 감싸서 작성한다.
'/,/'은 단순히 ','(콤마)를 찾는 정규식이며
뒤에 붙은 'g'는 문자열 전체에서 콤마를 찾도록 해주는 플래그다.

(정규식의 'g'를 한번 삭제하고 실행할 경우 첫 번째 콤마만 삭제된다.)

## split(), join() 함수 사용하기

```javascript
const numberStr = "12,34,56";

const number = numberStr.split(",").join("");
console.log(number); // 123456
```

`split()` 함수는 문자열을 첫 번째 파라미터(",")로 잘라서 배열로 리턴한다.

`numberStr.split(",")`  
['12', '34', '56'] 리턴함.

`join()` 함수는 배열의 모든 요소를 연결해 하나의 문자열로 만들어 준다.

`numberStr.split(",").join("")`  
split() 함수가 리턴 한 값이 ['12', '34', '56']이니까
이 배열의 문자열을 모두 연결하면, "123456"이 된다.
