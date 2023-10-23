# 배열 특정 값 위치(index) 찾기 indexOf(), lastIndexOf(), findIndex()

- [배열 특정 값 위치(index) 찾기 indexOf(), lastIndexOf(), findIndex()](#배열-특정-값-위치index-찾기-indexof-lastindexof-findindex)
  - [indexOf()](#indexof)
    - [찾는 요소가 있는 모든 위치 찾기 indexOf()](#찾는-요소가-있는-모든-위치-찾기-indexof)
  - [lastIndexOf()](#lastindexof)
  - [findIndex()](#findindex)
    - [findIndex() 사용하여 객체 찾기](#findindex-사용하여-객체-찾기)

## indexOf()

Array 인스턴스의 `indexOf()` 메서드는 배열에서 주어진 요소를 찾을 수 있는 `첫 번째 인덱스를 반환`하고, `찾을 수 없는 경우 -1을 반환`한다.

```javascript
arr.indexOf(searchElement[, fromIndex])
```

**searchElement**<br>
찾으려는 값

**fromIndex**<br>
검색을 시작할 index
입력하지 않으면 0부터 검색 시작.

```javascript
const beasts = ["ant", "bison", "camel", "duck", "bison"];

console.log(beasts.indexOf("bison")); // 1
console.log(beasts.indexOf("bison", 2)); // 4
console.log(beasts.indexOf("giraffe")); // -1
```

`beasts.indexOf("bison")`<br>
"bison"값에 해당하는 첫 번째 인덱스 반환.

`beasts.indexOf("bison", 2)`<br>
2번째 index부터(beasts[2]) "bison"값에 해당하는 첫 번째 인덱스 반환.

`beasts.indexOf("giraffe")`<br>
"giraffe" 해당 값을 찾을 수 없으므로 -1 반환.

### 찾는 요소가 있는 모든 위치 찾기 indexOf()

```javascript
const indices = [];
const array = ["a", "b", "a", "c", "a", "d"];
const element = "a";

let idx = array.indexOf(element);
while (idx !== -1) {
  indices.push(idx);
  idx = array.indexOf(element, idx + 1);
}
console.log(indices); // [0, 2, 4]
```

indexOf()의 결과가 -1이 될때까지,<br>
fromIndex값을 이전에 찾아낸 index값 이후로 설정해주어<br>
특정값이 있는 모든 index를 찾아낸다.

## lastIndexOf()

`lastIndexOf()` 메서드는 배열에서 주어진 값을 발견할 수 있는 `마지막 인덱스를 반환`하고, `요소가 존재하지 않으면 -1을 반환`한다.<br>
`배열 탐색은 fromIndex에서 시작하여 역방향으로(index값을 줄여나감) 진행`한다.<br>
fromIndex값이 입력되지 않으면, 기본값은 (배열의 길이 -1)이다.

```javascript
arr.lastIndexOf(searchElement[, fromIndex])
```

```javascript
const beasts = ["ant", "bison", "camel", "duck", "bison"];

console.log(beasts.lastIndexOf("bison")); // 4
console.log(beasts.lastIndexOf("bison", 2)); // 1
```

**lastindexOf()는 뒤에서부터 앞으로(역순으로) 탐색하지만,<br>
요소를 찾은 후 반환되는 index 값은<br>
앞에서부터 몇 번째에 (왼쪽 -> 오른쪽) 위치하는지를 반환한다.**

`beasts.lastIndexOf("bison")`<br>
배열의 뒤에서부터 탐색했을 때 "bison"값을 가지는 마지막 index는 4이다.<br>

`beasts.lastIndexOf("bison", 2)`<br>
배열의 뒤에서부터 탐색했을 때 2번째 index부터 "bison"값을 가지는 마지막 index는 1이다.

## findIndex()

`findIndex()` 메서드는 `주어진 판별 함수를 만족하는 배열의 첫 번째 요소에 대한 인덱스를 반환`한다.<br>
`만족하는 요소가 없으면 -1을 반환`한다.

```javascript
arr.findIndex(callbackFn, thisArg);
```

**`callback(element, index, array) 함수`**<br>
조건을 비교할 callback 함수이고, 다음 3개의 파라미터가 전달된다.<br>
callback 함수에서 사용자가 테스트할 조건을 정의<br>
만약 배열의 값이 조건에 부합하면 true를 리턴<br>
해당 배열의 index가 findIndex()의 리턴 값이 된다.

조건에 부합하는 값을 찾으면, 그 이후의 배열 값은 테스트 되지 않는다.

**`element`** : 현재 처리중인 배열의 element.<br>
**`index`** : 현재 처리중인 배열의 index. (optional)<br>
**`array`** : findIndex가 호출된 배열. (optional)<br>

**`thisArg (optional)`**<br>
callback을 실행할 때 this로 사용할 객체.

**`리턴 값`**<br>
callback 함수에 정의한 조건에 부합하는 배열의 첫 번째 index를 리턴.<br>
조건에 부합하는 배열 값이 없을 경우 -1을 리턴.

```javascript
const ages = [3, 10, 16, 20];

function checkAge(age) {
  return age > 16;
}

console.log(ages.findIndex(checkAge)); // 3
```

callback 함수에 배열의 값들이 순서대로 전달되고,<br>
그 값이 16보다 작거나 같다는 해당 조건에 부합하는 요소의 첫 번째 index를 반환한다.

```javascript
const arr = [2, 6, 8, 12];
function isOdd(element, index, array) {
  return element % 2 == 1;
}

console.log(arr.findIndex(isOdd)); // -1
```

홀수를 포함하는 모든 인덱스를 찾고, 홀수가 존재하지 않으므로 -1을 반환한다.

### findIndex() 사용하여 객체 찾기

```javascript
const fruits = [
  { name: "apply", price: 900 },
  { name: "banana", price: 1900 },
  { name: "lemon", price: 800 },
];

function findfruits(element) {
  if (element.name === "banana") return true;
}

console.log(fruits.findIndex(findfruits)); // 1
```

배열의 element가 참조형 타입이 아닌 객체인 경우,<br>
객체를 찾기 위한 조건을 callback 함수에 구현할 수 있다.
