# 같은 값으로 배열 채우기 fill()

## fill()

Array 인스턴스의 `fill()` 메서드는 `배열의 인덱스 범위 내에 있는 모든 요소를 정적 값으로 변경`한다.<br>
그리고 `수정된 배열을 반환`한다.

```javascript
fill(value, start, end);
```

**value**<br>
배열을 채울 값 지정.

**start**<br>
value 값을 채울 배열의 시작 index.<br>
입력하지 않으면 기본값은 0.

**end**<br>
value 값을 채울 배열의 종료 index.<br>
입력하지 않으면 기본값은 배열의 길이(arr.length).

**리턴값**<br>
지정한 값(value)으로 채워진 배열을 리턴.

---

```javascript
const arr1 = [1, 2, 3];
arr1.fill("A");

console.log(arr1); // ['A', 'A', 'A']

const arr2 = [1, 2, 3];
arr2.fill("A", 1);

console.log(arr2); // [1, 'A', 'A']

const arr3 = [1, 2, 3];
arr3.fill("A", 1, 3);

console.log(arr3); //  [1, 'A', 'A']
```

`arr1.fill("A");`<br>
arr1배열 전체를 "A"로 채움.

`arr2.fill("A", 1);`<br>
arr2배열의 arr2[1]부터 끝까지 "A"로 채움.

`arr3.fill("A", 1, 3);`<br>
arr3배열의 arr3[1] ~ arr[2]를 "A"로 채움.

---

### index가 음수일 경우

```javascript
const arr = [1, 2, 3];
arr.fill("A", -3, -1);

console.log(arr); // ['A', 'A', 3]
```

`arr.fill("A", -3, -1);`<br>
start index or end index가 음수로 지정되면,<br>
배열의 마지막 원소의 index가 -1이 되고<br>
앞쪽으로 올수록 index가 감소한다.

arr[-3]은 1이고, arr[-1]은 3이다.
`[1, 2, 3] -> ['A', 'A', 3]`

---

### 배열 초기화

```javascript
const arr1 = Array(5);
console.log(arr1); // (5) [empty × 5]

const arr2 = Array(5).fill();
console.log(arr2); // (5) [undefined, undefined, undefined, undefined, undefined]

const arr3 = Array(5).fill("A");
console.log(arr3); // (5) ['A', 'A', 'A', 'A', 'A']
```

`Array(5)`<br>
5개의 비어있는 값("")을 가진 배열 생성.

`Array(5).fill()`
5개의 element를 가지는 빈 배열이 생성되고,<br>
fill() 메서드를 사용하였지만 값이 비어있으므로, 각 값은 undefined로 채워짐.

`Array(5).fill("A")`<br>
fill() 함수를 사용하여, 생성된 배열의 element의 초기값을 지정할 수 있다.
