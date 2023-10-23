# 배열 중간에 값 추가, 삭제하기 splice()

- [배열 중간에 값 추가, 삭제하기 splice()](#배열-중간에-값-추가-삭제하기-splice)
  - [splice()](#splice)
    - [배열의 앞에 추가하기 (값 삭제X)](#배열의-앞에-추가하기-값-삭제x)
    - [배열의 중간에 추가하기 (값 삭제X)](#배열의-중간에-추가하기-값-삭제x)
    - [배열의 뒤에 추가하기 (값 삭제X)](#배열의-뒤에-추가하기-값-삭제x)
    - [배열의 앞에 값 삭제하기 (값 추가X)](#배열의-앞에-값-삭제하기-값-추가x)
    - [배열의 중간 값 삭제하기 (값 추가X)](#배열의-중간-값-삭제하기-값-추가x)
    - [배열의 마지막 값 삭제하기 (값 추가X)](#배열의-마지막-값-삭제하기-값-추가x)
    - [전체 또는 특정 인덱스 이후의 모든 요소 삭제](#전체-또는-특정-인덱스-이후의-모든-요소-삭제)
    - [삭제와 추가 동시에 하기](#삭제와-추가-동시에-하기)
    - [값 변경하기](#값-변경하기)

## splice()

```javascript
  array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

`splice()` 메서드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경한다.

- splice() 함수는 start, deleteCount, items원소 목록을 파라미터로 입력 받는다.
- splice() 함수는 start index부터 deleteCount만큼의 원소를 삭제하고,
  뒤 이어 오는 items를 start index 위치에 추가한다.

**start**<br>
변경을 시작할 배열의 시작 index

**deleteCount**<br>
start index부터 deleteCount 갯수만큼 원소를 삭제한다.<br>
deleteCount가 입력되지 않으면, start index 이후의 모든 값이 삭제됨.

**items**<br>
배열의 start index에 item들을 추가한다.

**리턴값**<br>
삭제된 원소(element)의 배열을 리턴.

---

### 배열의 앞에 추가하기 (값 삭제X)

- splice() 함수의 첫 번째 파라미터로 추가할 값이 들어갈 index 지정.
- 두 번째 파라미터는 삭제할 요소의 개수를 지정.
- 다음으로 추가할 값들을 넘겨준다.

```javascript
const arr = [1, 2, 3];
arr.splice(0, 0, "a", "b");

console.log(arr); // [ 'a', 'b', 1, 2, 3]
```

`arr.splice(0, 0, "a", "b");`<br>
arr.splice.(0번째 index, 삭제할 요소 0개, 추가할 값 "a", "b")

---

### 배열의 중간에 추가하기 (값 삭제X)

```javascript
const arr = [1, 2, 3];
arr.splice(1, 0, "a", "b");

console.log(arr); // [1, 'a', 'b', 2, 3]
```

`arr.splice(1, 0, "a", "b");`<br>
arr.splice(1번째 index, 삭제할 요소 0개, 추가할 값 "a", "b")

---

### 배열의 뒤에 추가하기 (값 삭제X)

```javascript
const arr = [1, 2, 3];
arr.splice(arr.length, 0, "4", "5");

console.log(arr); //  [1, 2, 3, '4', '5']
```

`arr.splice(arr.length, 0, "4", "5");`<br>
arr.splice.(arr의길이(3)index, 삭제할 요소 0개, 추가할 값 "4", "5")

---

### 배열의 앞에 값 삭제하기 (값 추가X)

- splice() 함수의 첫 번째 파라미터로 삭제할 값의 시작 index 지정.
- 두 번째 파라미터는 삭제할 원소의 개수를 지정.
- 추가할 값이 없으므로, 다음 파라미터는 지정하지 않는다.

**splice 함수에는 2개의 파라미터(삭제 시작 index, 삭제할 원소 갯수)만 전달한다.**

```javascript
const arr = ["a", "b", 1, 2, 3];
arr.splice(0, 2);

console.log(arr); // [1, 2, 3]
```

`arr.splice(0, 2);`<br>
arr.splice(0번째 index, 요소 2개 삭제)

---

### 배열의 중간 값 삭제하기 (값 추가X)

```javascript
const arr = [1, "a", "b", 2, 3];
arr.splice(1, 2);

console.log(arr); // [1, 2, 3]
```

`arr.splice(1, 2);`<br>
arr.splice(1번째 index, 요소 2개 삭제)

---

### 배열의 마지막 값 삭제하기 (값 추가X)

```javascript
const arr = [1, 2, 3, "a"];
arr.splice(arr.length - 1, 1);

console.log(arr); // [1, 2, 3]
```

`arr.splice(arr.length - 1, 1);`<br>
arr.splice(arr길이 끝, 요소 1개 삭제)

---

### 전체 또는 특정 인덱스 이후의 모든 요소 삭제

```javascript
// 전체 원소 삭제
const arr1 = [1, 2, 3];
arr1.splice(0);

console.log(arr1); // []

// index 1 이후의 모든 원소 삭제
const arr2 = [1, 2, 3];
arr2.splice(1);

console.log(arr2); // [1]
```

`arr1.splice(0);`<br>
배열 전체의 요소를 삭제하고 싶다면,<br>
첫 번째 파라미터(start index)를 0으로 지정하고, 나머지 파라미터는 입력하지 않는다.

`arr2.splice(1);`<br>
특정 index 이후의 요소를 삭제하고 싶다면,<br>
첫 번째 파라미터(start index)를 삭제할 특정 index를 지정하고, 나머지 파라미터는 입력하지 않는다.

---

### 삭제와 추가 동시에 하기

```javascript
const arr = [1, 2, 3];
arr.splice(1, 1, "b", "c");

console.log(arr); //  [1, 'b', 'c', 3]
```

`arr.splice(1, 1, "b", "c");`<br>
index 1에서부터 1개의 요소(2)를 삭제하고, index 1에 'b', 'c' 원소 2개를 추가함.

---

### 값 변경하기

```javascript
const arr = [1, 2, 3];
arr.splice(1, 1, "b");

console.log(arr); // [1, 'b', 3]
```

`arr.splice(1, 1, "b");`<br>
index 1에서부터 1개의 요소(2)를 삭제하고, 그 위치에 새로운 값('b')을 추가함.
