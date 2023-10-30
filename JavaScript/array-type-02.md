# 배열의 길이 확인, 설정하기 length속성

## 배열의 길이 확인하기

```javascript
const clothing = ["shoes", "shirts", "socks", "sweaters"];

console.log(clothing); // ['shoes', 'shirts', 'socks', 'sweaters']
console.log(clothing.length); // 4
```

clothing 배열의 길이가 4인 것을 확인할 수 있다.

## 배열의 길이 설정하기

```javascript
const clothing = ["shoes", "shirts", "socks", "sweaters"];
clothing.length = 3;

console.log(clothing); // ['shoes', 'shirts', 'socks']
console.log(clothing.length); // 3
```

length 속성에 값을 설정해 배열의 길이를 절단할 수 있다.
또한 배열의 길이를 늘리는 것도 가능하다.

```javascript
const clothing = ["shoes", "shirts", "socks", "sweaters"];
clothing.length = 6;

console.log(clothing); // ['shoes', 'shirts', 'socks', 'sweaters', empty × 2]
```

length 속성으로 배열의 길이를 6으로 늘렸더니,  
기존 원소 4개에서 undefined가 2개 추가되어 총 6개의 길이를 갖게 된다.
