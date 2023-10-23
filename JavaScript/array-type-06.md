# 배열 자르기 slice()

## slice()

```javascript
arr.slice([begin[, end]])
```

`slice()` 함수는 어떤 배열의 begin 부터 end 까지(end 미포함)에 대한 얕은 복사본을 새로운 배열 객체로 반환한다.<br>
원본 배열은 바뀌지 않는다.

```javascript
const arr = ["a", "b", "c", "d"];

const arr1 = arr.slice(0, 3);
const arr2 = arr.slice(1);
const arr3 = arr.slice(-3, -1);

console.log(arr1); // ['a', 'b', 'c']
console.log(arr2); // ['b', 'c', 'd']
console.log(arr3); // ['b', 'c']
```

`const arr1 = arr.slice(0, 3);`<br>
배열의 arr[1] ~ arr[3]까지(arr[3] 미포함)를 복사한 새 배열을 리턴한다. `['a', 'b', 'c']`

`const arr2 = arr.slice(1);`<br>
두번째 파라미터인 end 값이 입력되지 않으면,<br>
시작 index부터 배열의 끝까지를 복사한, 새 배열을 리턴한다. `['b', 'c', 'd']`

`const arr3 = arr.slice(-3, -1);`<br>
begin index나 end index가 음수면,
배열의 끝에서부터의 길이를 나타낸다.

["a", "b", "c", "d"]; 여기에서<br>
"b"가 arr[-3]자리이고,<br>
"d"가 arr[-1]자리이므로,<br>
arr[-3] ~ arr[-1]까지(arr[-1] 미포함)를 복사한 새 배열을 리턴한다. `['b', 'c']`
