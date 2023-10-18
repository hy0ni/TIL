# 특정 문자 위치 찾기 indexOf()

## indexOf()

```javascript
str.indexOf(searchValue[, fromIndex])
```

- `indexOf()` 함수는 호출한 String 객체에서 주어진 값과 일치하는 첫 번째 인덱스를 반환한다. 일치하는 값이 없으면 -1을 반환한다.
- `indexOf()` 함수는 대소문자를 구분한다.
- `searchValue`: 찾으려는 문자열
- `fromIndex`: 문자열에서 찾기 시작하는 위치를 나타내는 index 값

```javascript
const str = "apple banana orange";

console.log(str.indexOf("a")); // 0
console.log(str.indexOf("banana")); // 6
console.log(str.indexOf("q")); // -1
```

문자열에 "p"가 없으므로 -1을 리턴.

## fromIndex 값을 입력한 경우

```javascript
const str = "apple apple banana orange";

console.log(str.indexOf("apple")); // 0
console.log(str.indexOf("apple", 1)); // 6
```

`str.indexOf("apple")`
indexOf() 함수의 두 번째 파라미터인 fromIndex 값이 입력되지 않으면 0으로 처리됨.

`str.indexOf("apple", 1)`
두 번째 파라미터인 fromIndex 값에 1을 전달하였으므로
index 0번에 있는 "apple"값은 무시된다.

## 문자열에 있는 모든 searchvalue 위치 찾기

```javascript
const str = "apple apple banana apple";

let pos = 0;
while (true) {
  let foundPos = str.indexOf("apple", pos);
  if (foundPos == -1) break;

  console.log(foundPos); // 0 6 19
  pos = foundPos + 1;
}
```

`let foundPos = str.indexOf("apple", pos)`<br>
while 반복문 안에서 searchValue("apple")를 찾은 후

`pos = foundPos + 1`<br>
fromIndex 값을 foundPos의 다음 index값으로 변경해 준다.

`if (foundPos == -1) break;`<br>
더이상 찾는 문자열이 없다면 종료.
