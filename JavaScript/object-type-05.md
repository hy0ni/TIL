# 객체를 JSON으로 변환하기 JSON.stringify()

- [객체를 JSON으로 변환하기 JSON.stringify()](#객체를-json으로-변환하기-jsonstringify)
  - [JSON.stringify() 함수](#jsonstringify-함수)
    - [JSON 형식의 특징](#json-형식의-특징)
    - [JSON.stringify() 함수로 변환되지 않는 항목](#jsonstringify-함수로-변환되지-않는-항목)
  - [특정 항목만 JSON으로 변환하기](#특정-항목만-json으로-변환하기)
    - [replacer가 배열인 경우](#replacer가-배열인-경우)
    - [replacer가 함수인 경우](#replacer가-함수인-경우)
      - [JSON으로 변환 시 속성 값 변경하기 (함수 replacer)](#json으로-변환-시-속성-값-변경하기-함수-replacer)
  - [들여쓰기(indent) 설정하기](#들여쓰기indent-설정하기)
    - [숫자로 space 지정하기](#숫자로-space-지정하기)
    - [문자로 space 지정하기](#문자로-space-지정하기)

Javascript에서 사용하는 객체(Object)를 네트워크를 통해 전송하려면  
객체를 그대로 서버로 전송할 수는 없기때문에  
주로 객체를 JSON(JavaScript Object Notation) 형식으로 변환하여 전달한다.  
(Javascript가 아닌 언어에서도 데이터 교환 목적으로 JSON 형식을 많이 사용함.)

## JSON.stringify() 함수

JSON.stringify() 정적 메서드는 JavaScript 값을 JSON 문자열로 변환하며,  
대체 함수가 지정된 경우 선택적으로 값을 바꾸고,  
대체 배열이 지정된 경우 지정된 속성만 선택적으로 포함한다.

```javascript
JSON.stringify(value, replacer, space);
```

`value (필수)`  
JSON 문자열로 변환할 값 또는 객체

`replacer (optional)`  
JSON 변경 규칙을 정의 할 함수 또는 JSON에 포함 될 프로퍼티(속성)을 가지는 배열

`space (optional)`  
가독성을 위해 출력 JSON 문자열에 공백(들여쓰기, 줄 바꿈 문자 등 포함)을 삽입하는 데 사용되는 문자열 또는 숫자.

```javascript
const obj = {
  id: 123,
  product: {
    type: "book",
    page: 200,
    title: "Javascript",
    tags: ["JS", "language"],
  },
};

const json = JSON.stringify(obj);
console.log(typeof obj); // object
console.log(typeof json); // string
console.log(json);
/*
  {"id":123,"product":{"type":"book","page":200,"title":"Javascript","tags":["JS","language"]}}
*/
```

JSON.stringify() 함수를 이용하여 객체를 JSON 형식의 문자열로 변환.

### JSON 형식의 특징

- 문자열을 감쌀 때 쌍따옴표("")를 사용한다. (홑따옴표('')X)
- 프로퍼티 키(property key)는 쌍따옴표("")로 감싸져야 한다.
- 주석을 작성할 수 없다.

### JSON.stringify() 함수로 변환되지 않는 항목

```javascript
const obj = {
  x: undefined,
  y: Symbol(""),
  z: function () {
    alert("Hello");
  },
  arr: [
    1,
    undefined,
    Symbol(""),
    function () {
      alert("Hello");
    },
  ],
};

const json = JSON.stringify(obj);

console.log(json); // {"arr":[1,null,null,null]}
```

JSON.stringify() 함수로 객체를 JSON 형태의 문자열로 변환할 때

undefined, Symbol, function은 변환되지 않고 무시된다.
만약, undefined, Symbol, function이 배열 안에 있다면 이 값들은 null로 전환되어 표시된다.

## 특정 항목만 JSON으로 변환하기

**`replacer`**

JSON.stringify() 함수는 두번째 파라미터로 replacer를 받는데  
이 값은 배열이 될 수도 있고, 함수가 될 수도 있다.

이 replacer를 이용하여, Javascript 객체에서 JSON 문자열로 변환 할 property(속성)을 지정할 수 있다.

### replacer가 배열인 경우

```javascript
const obj = {
  x: "x",
  y: "y",
  z: {
    z1: "z1",
  },
};

const json = JSON.stringify(obj, ["y", "z"]);

console.log(json); // {"y":"y","z":{}}
```

JSON.stringify() 함수의 2번째 파라미터로 JSON으로 변환 할 속성명을 포함하는 배열을 전달.  
'y', 'z' 2개의 속성만을 JSON으로 변환하도록 했을때,  
'z' 속성이 가지고 있는 객체에 포함 된 'z1'은 제대로 변환되지 않는다.  
'z1' 속성도 JSON 문자열에 포함시키고 싶다면,
'z1'도 replacer 배열에 포함시켜 주어야 한다.

```javascript
const obj = {
  x: "x",
  y: "y",
  z: {
    z1: "z1",
  },
};

const json = JSON.stringify(obj, ["y", "z", "z1"]);

console.log(json); // {"y":"y","z":{"z1":"z1"}}
```

'z1'도 배열에 포함시키면,  
'z' 속성의 값인 객체('z1'을 포함하고 있는)도 JSON 문자열로 변환된다.

### replacer가 함수인 경우

replacer는 함수가 될 수도 있다.  
JSON으로 변환할 속성을 일일히 나열하기 힘들 다거나, 특별한 조건을 주어야 할 때 유용하다.

```javascript
const obj = {
  x: "x",
  y: "y",
  z: {
    z1: "z1",
  },
};

function replacer(key, value) {
  console.log(`${key} : ${value}`);
  if (key === "x") {
    return undefined;
  } else {
    return value;
  }
}

const json = JSON.stringify(obj, replacer);

console.log(json);
/*
  : [object Object]
  x
  y
  [object Object]
  z1
  {"y":"y","z":{"z1":"z1"}}
*/
```

replacer가 함수일 때는, 파라미터로 객체의 key와 value가 전달된다.  
가장 먼저 찍히는 ': [object Object]'는 JSON으로 변환할 'obj' 객체를 가리킨다.  
replacer 함수에서 undefined를 반환하면 해당 속성은 JSON으로 변환되지 않고 무시된다.  
'x'는 JSON 문자열에 포함시키지 않기 위해서 undefined를 리턴.  
replacer 함수에서 특정 문자열이나 숫자값을 반환하면,  
그 값은 해당 속성의 값으로 JSON으로 변환된다.  
속성 'x'가 아닌 경우에는, 해당 속성의 value를 그대로 리턴해서,  
원래의 속성값이 그대로 JSON으로 변환되도록 함.

#### JSON으로 변환 시 속성 값 변경하기 (함수 replacer)

```javascript
const obj = {
  x: 1,
  y: 2,
};

function replacer(key, value) {
  if (key === "x") {
    return value + 1;
  } else {
    return value;
  }
}

const json = JSON.stringify(obj, replacer);

console.log(json); // {"x":2,"y":2}
```

replacer 함수를 작성하여, 객체를 JSON으로 변환할 때, 특정 속성의 값을 변경할 수 있다.  
속성명이 'x'일 경우, 속성 'x'의 값에 1을 더해서 리턴.

## 들여쓰기(indent) 설정하기

JSON.stringify() 함수는 3번째 파라미터로 space를 입력 받는다.  
이 값은 숫자가 될 수도 있고, 문자열이 될 수도 있다.  
이 값을 이용해 JSON 문자열의 들여쓰기 간격을 지정할 수 있다.

### 숫자로 space 지정하기

```javascript
const obj = {
  x: "x",
  y: "y",
  z: {
    z1: "z1",
  },
};

const json = JSON.stringify(obj, null, 5);

console.log(json);
/*
  {
   "x": "x",
   "y": "y",
   "z": {
        "z1": "z1"
    }
  }
*/
```

JSON.stringify() 함수의 3번째 파라미터 space에 숫자가 지정되면,  
해당 숫자만큼 들여쓰기가 적용된 JSON 문자열이 생성된다.

JSON.stringify() 함수의 3번째 파라미터로 숫자 5를 지정하니,  
생성된 JSON 문자열은 5개의 스페이스만큼 들여쓰기가 된다.

이 때, 숫자는 최대 10까지 지정할 수 있고, 만약 숫자 10을 넘는 숫자가 space값으로 지정되면,  
10만큼만 들여쓰기가 적용된다.

### 문자로 space 지정하기

```javascript
const obj = {
  x: "x",
  y: "y",
  z: {
    z1: "z1",
  },
};

const json = JSON.stringify(obj, null, "**");

console.log(json);
/*
  {
  **"x": "x",
  **"y": "y",
  **"z": {
  ****"z1": "z1"
  **}
  }
*/
```

JSON.stringify() 함수의 3번째 파라미터인 space에 문자열을 지정하면,  
해당 문자열을 들여쓰기 자리에 넣어준다.

만약, 문자열의 길이가 10을 넘어가면, 앞에서부터 10자리까지만 들여쓰기 자리에 넣어준다.
