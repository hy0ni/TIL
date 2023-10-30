# 반복문 내에서 특정 값을 제외하고 실행하기 (continue 구현)

## for...of 구문 사용하기

```javascript
const arr = [1, 2, 3];

for (const element of arr) {
  if (element === 1) continue;

  console.log(element);
}
```

forEach 반복문에서는 continue 구문을 사용할 수 없다.
for or for..of 문에서 continue 사용.

## return문 사용하기

반드시 forEach문을 사용해야 한다면, return문을 사용할 수 있음.

```javascript
const arr = [1, 2, 3];

arr.forEach((element) => {
  if (element === 1) {
    return;
  }
  console.log(element);
});
```

forEach 문은 배열의 모든 값을 순회하기 때문에, 특정 값의 처리를 건너 뛰고 싶으면  
continue 대신에 return 문을 사용할 수 있다.  
해당 값의 처리를 건너 뛰고, 배열의 다음 값을 처리한다.

## filter 사용하기

```javascript
const arr = [1, 2, 3];

arr.filter((element) => element !== 1).forEach((element) => console.log(element));
```

filter() 함수는 특정 조건에 부합하는 배열의 모든 값을 배열 형태로 리턴한다.  
'값이 1이 아닌 element'만으로 새로운 배열을 만든다.(배열 [2, 3]을 리턴)  
forEach() 함수는 이 '배열 [2, 3]'을 처리하게 된다.
