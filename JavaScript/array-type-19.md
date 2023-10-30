# 배열에서 빈값 제거하기

- [배열에서 빈값 제거하기](#배열에서-빈값-제거하기)
  - [undefined 값만 제거하기 (filter 함수와 '!==' 연산자)](#undefined-값만-제거하기-filter-함수와--연산자)
  - [undefined, null(nullish value) 제거하기 (filter 함수와 '!=' 연산자)](#undefined-nullnullish-value-제거하기-filter-함수와--연산자)
  - [빈값(empty value) 제거하기](#빈값empty-value-제거하기)
  - [undefined, null, false, '', 빈값(empty) 모두 제거하기 (Falsy value)](#undefined-null-false--빈값empty-모두-제거하기-falsy-value)

## undefined 값만 제거하기 (filter 함수와 '!==' 연산자)

```javascript
const arr = [1, undefined, null, false, , "", "    "];

const newArr = arr.filter((element, i) => element !== undefined); // (5) [1, null, false, '', '    ']

newArr.forEach((e, i) => {
  console.log(`${i} : ${e}`);
});
/*
  0 : 1
  1 : null
  2 : false
  3 :
  4 :
*/
```

filter 함수로 전달된 callback 함수는  
undefined 값이 아닌 경우에만 true를 리턴하고,  
undefined 값이 아닌 경우의 element만으로 새로운 배열(newArr)을 만들어서 리턴한다.

element와 undefined를 비교하기 위해서 '!==' 연산자를 사용.

원래의 배열인 arr는  
[1(숫자), undefined, null, false, 빈값(empty), ''(empty string), ' '(공백을 포함한 비어있는 문자열)]  
총 7개의 값을 가지고 있다.

filter 함수에서 '!==' 연산자를 사용하여 undefined 값을 제거함으로  
arr[1] = undefined  
arr[4] = empty  
2개 값이 삭제되어 길이가 5인 새로운 배열(newArr)이 생성.

filter 함수는 배열에 값이 할당된 적이 없는 index를 호출하지 않는다.  
arr[4]의 값은 undefined가 아닌 empty이므로 새로운 배열(newArr)에 포함되지 않는다.

## undefined, null(nullish value) 제거하기 (filter 함수와 '!=' 연산자)

javascript에서 undefined, null 값을 nullish value라고 한다.  
이 두 값을 모두 배열에서 제거하기 위해서는  
'!==' 연산자 대신에 `'!=' 연산자를 사용`한다.

```javascript
const arr = [1, undefined, null, false, , "", "    "];

const newArr = arr.filter((element, i) => element != null);

console.log(newArr); // (4) [1, false, '', '    ']
newArr.forEach((e, i) => {
  console.log(`${i} : ${e}`);
});
/*
  0 : 1
  1 : false
  2 :
  3 :
*/
```

filter 함수로 전달된 callback 함수에서  
각 element와 null을 '!=' 비교 연산자를 사용하여 비교함.

arr[1], arr[2], arr[4]의 값이 삭제되고,  
새로운 배열(newArr)은 4개의 원소(1, false, '', ' ')를 갖게 된다.

## 빈값(empty value) 제거하기

배열에 값이 할당되지 않은 요소를 제거하는 방법.  
filter 함수는 값이 할당되지 않은 index는 순회하지 않는다.

```javascript
const arr = [1, undefined, null, false, , "", "    "];

arr.filter((element, i) => {
  console.log(i);
});
/*
  0
  1
  2
  3
  5
  6
*/
```

filter 함수에서 순회하는 index값을 화면에 출력하는 코드를 확인해보면,  
0~6까지 index가 출력되었지만,  
arr[4]의 값이 할당되지 않았으므로 index 4는 출력되지 않는다.

```javascript
const arr = [1, undefined, null, false, , "", "    "];

const newArr = arr.filter((element) => true);

newArr.forEach((e, i) => {
  console.log(`${i} : ${e}`);
});
/*
  0 : 1
  1 : undefined
  2 : null
  3 : false
  4 :
  5 :
*/
```

filter 함수가 무조건 true를 리턴하므로,  
순회하지 않은 arr[4]를 제외한 모든 요소들이 새로운 배열(newArr)에 담긴다.  
즉, 빈 값을 제외한 배열이 됨.

## undefined, null, false, '', 빈값(empty) 모두 제거하기 (Falsy value)

`Javascript의 Falsy value는 Boolean으로 체크했을 때, false로 변환되는 값들을 말한다.`  
undefined, null, false, ""(empty string) 모두 Falsy value에 해당된다.

```javascript
const arr = [1, undefined, null, false, , "", "    "];

const newArr = arr.filter(Boolean);

newArr.forEach((e, i) => {
  console.log(`${i} : ${e}`);
});
/*
  0 : 1
  1 :     
*/

console.log(newArr[1].length); // 4
```

배열에서 Falsy value들을 제거하기 위해  
filter 함수의 callback 함수로 Boolean constructor를 전달한다.

원래의 배열(arr) 요소들 중 falsy value들이 모두 삭제되고,  
새로운 배열(newArr)에는 2개의 요소([1, ' '])만 남는다.  
(' '는 empty string이 아니기 때문에 삭제되지 않는다.)

Boolean constructor는 파라미터로 전달된 값을 판단하여 true 또는 false를 리턴한다.  
Falsy value들은 Boolean에 의해 모두 false로 판된되어지는 값들이니,  
이런 값들은 false를 리턴 하므로,  
filter 함수는 이 값들을 제외한다.
