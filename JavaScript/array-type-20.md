# 빈 배열 체크하기

특정 객체가 배열인지 확인하고, 배열이라면 빈 배열인지 확인한다.

```javascript
const arr1 = [];
const arr2 = [1, 2];
const obj = {};
const str = "";

function isEmptyArr(arr) {
  if (Array.isArray(arr) && arr.length === 0) {
    return true;
  }

  return false;
}

console.log(isEmptyArr(arr1)); // true
console.log(isEmptyArr(arr2)); // false
console.log(isEmptyArr(obj)); // false
console.log(isEmptyArr(str)); // false
```

객체가 배열인지 확인하기 위해 `Array.isArray()` 함수를 사용한다.

일반적으로, javascript에서 데이터 타입을 확인하기 위해서는 typeof를 사용하지만<br>
typeof를 사용하게 되면 배열은 'object'를 리턴한다.

데이터 타입 확인하기: typeof<br>
배열인지 확인하기: isArray()

`arr.length === 0`<br>
배열이 비어있는지 확인하기 위해 arr.length의 값을 체크한다.
