# 배열의 특정 값 찾기 find(), filter()

## find()

```javascript
find(callbackFn, thisArg);
```

`find()` 메서드는 배열에서 특정 값을 찾는 조건을 callback 함수를 통해 전달하여,  
조건에 만족하는 첫 번째 요소의 값을 반환한다.  
조건에 만족하는 요소가 없다면 undefined를 반환한다.  
`find()` 메서드는 호출의 대상이 된 원본 배열을 변경하지 않는다.

**`callback`**  
배열의 각 값에 대해 실행할 함수.

**`element`**: 콜백함수에서 처리할 현재 요소  
**`index(optional)`**: 콜백함수에서 처리할 현재 요소의 인덱스  
**`array(optional)`**: find()를 호출한 배열

**`thisArg(optional)`**  
callback 함수가 실행될 때 this로 사용할 객체.

**`반환 값`**  
callback 함수에 전달한 조건에 만족하는 배열의 첫 번째 요소의 값을 반환한다.  
조건에 만족하는 요소가 없다면 undefined를 반환한다.

```javascript
const fruits = [
  { name: "apply", price: 1000 },
  { name: "banana", price: 2000 },
  { name: "banana", price: 2000 },
  { name: "lemon", price: 3000 },
];

function isBanana(element) {
  if (element.name === "banana") return true;
}

const banana = fruits.find(isBanana);
console.log(banana); // {name: 'banana', price: 2000}
console.log(banana.name); // banana
console.log(banana.price); // 2000
```

`const banana = fruits.find(isBanana)`  
find() 메서드에 isBanana() 함수를 callback 함수에 전달.

isBanana() 함수는 파라미터로 입력받은 객체(element)의 name이 'banana'가 맞다면 true를 리턴한다.  
find() 메서드는 파라미터로 전달된 callback 함수가 true를 리턴하면
해당 배열의 값을 리턴하고 callback 함수를 종료한다.

fruits 배열의 여러 객체 중  
`name === 'banana'`  
name이 'banana'인 fruits[1]의 값을 반환.

find() 메서드는  
callback 함수에 전달한 조건에 만족했을 때 배열의 첫 번째 값을 반환함.

## filter()

```javascript
filter(callbackFn, thisArg);
```

`find()` 메서드가 특정 조건에 부합하는 배열의 첫번째 값만을 리턴한다고 한다면,  
`filter()` 메서드는 특정 조건에 부합하는 배열의 모든 값을 배열 형태로 리턴한다.

**`반환 값`**  
callback 함수에 정의한 조건에 부합하는 배열의 모든 값을 새로운 배열로 반환한다.  
조건에 부합하는 배열 값이 없을 경우 빈 배열을 반환한다.

```javascript
const fruits = [
  { name: "apply", price: 1000 },
  { name: "banana", price: 2000 },
  { name: "banana", price: 2000 },
  { name: "lemon", price: 3000 },
];

function isBanana(element) {
  if (element.name === "banana") return true;
}

const bananas = fruits.filter(isBanana);
const melons = fruits.filter(isMelon);

console.log(bananas.length); // 2
console.log(bananas); // Array(2) {name: 'banana', price: 2000} {name: 'banana', price: 2000}

function isMelon(element) {
  if (element.name === "melon") return true;
}

console.log(melons); // []
```

`const bananas = fruits.filter(isBanana)`  
filter() 메서드에 isBanana 함수를 callback함수에 전달.

filter() 메서드는 fruits 배열에서 객체의 name이 'banana'인 모든 객체를 찾아
새로운 배열을 생성하여 반환한다.

filter() 메서드가 반환하는 bananas는  
length가 2인 배열이고, 배열 2개의 값은 fruits[1], fruits[2]의 값과 같다.

`const melons = fruits.filter(isMelon)`  
filter() 메서드에 isMelon 함수를 callback함수에 전달.

fruits배열에 name이 'melon'인 객체는 없으므로 filter() 메서드는 빈 배열을 반환한다.
