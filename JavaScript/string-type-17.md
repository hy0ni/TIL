# 문자열 거꾸로 뒤집는 방법

- String.protype.split()
  - `split()` 함수는 문자열을 부분 문자열(substring)로 구분해 문자열 객체를 여러 개의 문자열로 이루어진 배열로 분할한다.
- Array.protype.reverse()
  - `reverse()` 함수는 배열을 반전시킴.  
    첫 번째 배열 요소는 마지막 요소가 되고 마지막 요소는 첫 번째 요소가 된다.
- Array.protype.join()
  - join() 메서드는 배열의 모든 요소를 문자열로 결합한다.

```javascript
const str = "가나다라";
const strSplit = str.split(""); // ['가', '나', '다', '라']
const reverseArray = strSplit.reverse(); // ['라', '다', '나', '가']
const joinArray = reverseArray.join(""); // 라다나가
```

`str.split("")`  
split() 함수를 사용하여 문자열을 배열로 변환한다.

`strSplit.reverse()`  
reverse() 함수를 사용해 새 배열의 순서를 뒤집는다.

`reverseArray.join("")`  
`join()` 함수를 사용해 배열의 모든 요소를 문자열로 결합한다.

## 코드를 간결하게 작성하기

```javascript
function reverseString(str) {
  return str.split("").reverse().join("");
}
reverseString("가나다라"); // // 라다나가
```
