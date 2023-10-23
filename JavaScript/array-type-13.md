# map() 함수로 변경된 새로운 배열 생성하기

```javascript
arr.map(callback(currentValue[, index[, array]])[, thisArg])
```

map() 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환한다.

```javascript
const array = [1, 4, 9, 16];

const map = array.map((x) => x * 2);

console.log(map);
// output: Array [2, 8, 18, 32]
```

### 인자를 받는 함수를 사용하여 숫자 배열 재구성하기

```javascript
const numbers = [1, 4, 9];
const doubles = numbers.map(function (num) {
  return num * 2;
});
// doubles는 이제 [2, 8, 18]
// numbers는 그대로 [1, 4, 9]
```

인자인 배열과 안의 요소들은 map을 통해 순회하면서 원본 배열로부터 자동으로 할당된다.
