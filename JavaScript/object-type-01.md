# 객체 속성 읽기, 추가, 변경, 삭제

- [객체 속성 읽기, 추가, 변경, 삭제](#객체-속성-읽기-추가-변경-삭제)
  - [객체 속성 읽기](#객체-속성-읽기)
    - [점 표기법 (dot notation)](#점-표기법-dot-notation)
    - [대괄호 표기법 (square bracket notation)](#대괄호-표기법-square-bracket-notation)
  - [객체 속성 추가, 변경하기](#객체-속성-추가-변경하기)
    - [점 표기법 (dot notation)](#점-표기법-dot-notation-1)
    - [대괄호 표기법 (square bracket notation)](#대괄호-표기법-square-bracket-notation-1)
  - [동적으로 객체 속성 추가/삭제하기 (Computed Property)](#동적으로-객체-속성-추가삭제하기-computed-property)
  - [객체 속성 삭제하기 (delete 연산자)](#객체-속성-삭제하기-delete-연산자)

## 객체 속성 읽기

객체 속성 값을 읽는 방법은 `점 표기법(dot notation)`과 `대괄호 표기법(square bracket notation)`이 있다.

### 점 표기법 (dot notation)

```javascript
const obj = {
  id: 1234,
  product: {
    type: "book",
    title: "object",
  },
};

console.log(obj.id); // 1234
console.log(obj.product); // {type: 'book', title: 'object'}
console.log(obj.product.type); // "book"
```

객체 속성에 접근해서 값을 읽으려면 각 속성 사이에 '`.`'을 입력한다.

### 대괄호 표기법 (square bracket notation)

```javascript
const obj = {
  id: 1234,
  product: {
    "product type": "book",
    title: "Title",
  },
};

console.log(obj["id"]); // 1234
console.log(obj.product["product type"]); // "book"
console.log(obj["product"]["title"]); // 'Title'
console.log(obj["product"].title); // "'Title'"
```

접근하려고 하는 객체의 속성명을 괄호([])로 감싸서 표현한다.

이때, 괄호 안에 들어가는 값은 작은따옴표('') 또는 큰따옴표("")로 감싸줘야 한다.

대괄호 표기법을 사용하면,
속성명이 'product type'과 같이 중간에 공백이 있는 경우에도 해당 값에 접근할 수 있는 장점이 있다.

## 객체 속성 추가, 변경하기

### 점 표기법 (dot notation)

```javascript
const obj = {
  id: 1234,
  product: {
    "product type": "book",
    title: "Title",
  },
};

// 속성 추가
obj.dog = "nana";
console.log(obj.dog); // "nana"

// 속성 값 변경
obj.product.title = "introduce";
console.log(obj.product.title); // "introduce"
```

점 표기법으로 객체의 속성에 접근하여 값을 할당 할 수 있다.<br>
만약, 접근하려는 속성이 객체에 존재하지 않으면, 속성이 추가되고,<br>
접근하려는 속성이 객체에 이미 존재하면, 기존 속성 값이 변경된다.

### 대괄호 표기법 (square bracket notation)

```javascript
const obj = {
  id: 1234,
  product: {
    "product type": "book",
    title: "Title",
  },
};

// 속성 추가
obj["dog"] = "nana";
console.log(obj.dog); // "nana"

// 속성 값 변경
obj["product"]["title"] = "introduce";
console.log(obj.product.title); // "introduce"
```

## 동적으로 객체 속성 추가/삭제하기 (Computed Property)

대괄호 표기법을 사용하면 입력된 파라미터의 값에 따라 동적으로 속성값 추가가 가능하다.<br>
이것을 Computed Property라고 부른다.

```javascript
const obj = {};

["red", "green", "blue"].forEach((color) => {
  obj[color] = color.substring(0, 1);
});

console.log(Object.keys(obj).length); // 3
console.log(obj.red); // r
console.log(obj.green); // g
console.log(obj.blue); // b
```

`obj[color] = color.substring(0,1)`<br>
객체의 속성에 접근해서, 해당 속성을 추가하거나 값을 변경해 준다.

`obj[color]`
괄호 안에 변수가 들어가 있는데, 괄호 안에 들어간 'color'는 따옴표로 둘러싸인 문자열이 아니라 앞에서 정의한 color다.

그리고, 이 color 변수에는 'red', 'green', 'blue' 문자열이 순차적으로 대입될 것이므로, 아래와 같이 실행된다.

`obj['red'] = 'r';`<br>
`obj['green'] = 'g';`<br>
`obj['blue'] = 'b';`

그리고, 최종적으로 obj는 아래와 같은 형태가 된다.

```javascript
obj = {
  red: "r",
  green: "g",
  blue: "b",
};
```

`Object.keys(obj).length`
코드를 모두 수행하고 난 후 객체가 가지고 있는 속성의 숫자는 3이 된다.

## 객체 속성 삭제하기 (delete 연산자)

객체의 속성을 삭제할 때는 `delete 연산자`를 사용한다.

```javascript
const obj = {
  id: 1234,
  product: {
    "product type": "book",
    title: "Title",
  },
};

// 속성 삭제
delete obj.id;
delete obj.product["product type"];

console.log(Object.keys(obj).length); // 1
console.log(obj.id); // undefined
console.log(obj.product["product type"]); // undefined
```

`delete obj.id`<br>
`delete obj.product["product type"]`<br>
삭제하려는 객체의 속성 앞에 delete 연산자를 넣어,<br>
해당 속성을 객체에서 삭제한다.

점 표기법, 대괄호 표기법 모두 사용 가능함.
