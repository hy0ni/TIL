# 객체(Object) 속성(property) 개수 구하기

```javascript
const obj = {
  product: "book",
  id: 111,
  page: 23,
};

console.log(Object.keys(obj)); // ['product', 'id', 'page']
console.log(Object.keys(obj).length); // 3
```

객체의 속성 개수를 구하기 위해<br>
Object.keys() 함수를 이용해서<br>
객체가 가지고 있는 key 값들을 배열로 리턴 받는다.

Object.keys() 함수는 파라미터로 입력받은 객체의 key 목록을 배열로 리턴한다.

그리고, 그 배열의 길이를 length 속성을 사용하여 가져오면,<br>
그 값이 객체의 속성 개수가 된다
