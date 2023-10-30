# 데이터 타입 확인하기 typeof

## typeof

```javascript
typeof operand;
```

typeof 연산자는 operand(type을 알고 싶은 객체 or 표현식)의 타입을 나타내는 문자열을 리턴한다.

```javascript
console.log(typeof "ABC"); // string
console.log(typeof 5); // number
console.log(typeof { name: "hyoni" }); // object
console.log(typeof null); // object
console.log(typeof [1, 2, 3]); // object
console.log(typeof true); // boolean
console.log(typeof undeclaredVariable); // undefined
console.log(typeof function () {}); // function
console.log(typeof 11n); // bigint
```

**`typeof [1, 2, 3]`**  
배열은 object를 리턴한다.  
배열은 object의 특수한 한 형태이기 때문에 `객체가 배열인지 확인하기 위해서는 isArray() 함수`를 사용해야 한다.
