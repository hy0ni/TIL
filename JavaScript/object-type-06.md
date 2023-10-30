# JSON 문자열을 객체로 변경하기 JSON.parse()

- [JSON 문자열을 객체로 변경하기 JSON.parse()](#json-문자열을-객체로-변경하기-jsonparse)
  - [JSON.parse() 함수](#jsonparse-함수)
  - [JSON 문자열의 값을 변경하여 객체로 변환하기](#json-문자열의-값을-변경하여-객체로-변환하기)

## JSON.parse() 함수

JSON 문자열을 객체로 변경할 때 JSON.parse() 함수를 사용한다.

```javascript
JSON.parse(text[, reviver])
```

**`text`**  
JSON으로 변환할 문자열.

**`reviver (Optional)`**  
JSON 문자열을 객체로 변환하여 리턴하기 전에, 값을 변형시키기 위한 함수.

```javascript
const json = '{"result":true, "count":42}';
const obj = JSON.parse(json);

console.log(obj.count); // 42
console.log(obj.result); // true
```

JSON.parse() 함수에 JSON 문자열을 파라미터로 전달하여,  
JSON 문자열을 객체로 변환함.

obj는 객체 형태이기 때문에 '`.`' 연산자를 사용하여
각각의 값에 접근할 수 있다.

## JSON 문자열의 값을 변경하여 객체로 변환하기

JSON.pare() 함수의 2번째 파라미터를 사용하여  
JSON 문자열을 객체로 변환하기 전에 특정 속성의 값을 변경할 수 있다.

```javascript
const json = '{"result":true, "count":42, "date":"2023-01-10"}';
const obj = JSON.parse(json);

console.log(typeof obj.count); // number
console.log(typeof obj.result); // boolean
console.log(typeof obj.date); // string
```

obj.date 속성의 값은 날짜를 나타낸다.  
이 속성은 문자열로 변환이 되는데 이 date 속성을 Date 객체로 변환하여 객체에 넣고 싶다면 JSON.pare() 함수의 2번째 파라미터(reviver)를 활용해야 한다.

```javascript
const json = '{"result":true, "count":42, "date":"2023-01-10"}';

function getDateObject(key, value) {
  if (key === "date") return new Date(value);
  return value;
}
const obj = JSON.parse(json, getDateObject);

console.log(typeof obj.date); // object
console.log(obj.date.getDate()); // 10
```

JSON.parse() 함수의 2번째 파라미터로 함수가 전달되면  
JSON.parse() 함수는 분석한 객체의 각 속성의 key와 value를 이 함수로 전달한다.

그리고 이 함수가 리턴하는 값을 다시 최종 결과의 속성값으로 설정한다.

만약, 이 함수에서 아무런 값도 리턴하지 않거나 undefined를 리턴하면 그 속성은 최종 결과에서 제외된다.

getDateObject(key, value) 함수는  
속성의 'key'가 'date'인 경우에  
속성값인 문자열을 Date 객체로 변환(new Date() 사용)하여 리턴한다.

만약, key가 'date'가 아닌 다른 속성이 들어오면  
원래의 속성값(value)을 그대로 리턴한다.

즉, 이 함수는 JSON 문자열의 여러 항목 중  
'key'가 'date'인 항목의 값을,  
문자열이 아닌 Date 객체로 변환해서 최종 결과에 포함시켜준다.

그리고, 나머지 값들은 다른 변경 없이 그대로 최종 결과에 포함시키게 된다.

만약, key가 'date'가 아닌 경우, 원래의 속성값을 리턴해주지 않으면,  
나머지 속성들이 최종 결과에 포함되지 않기 때문에
이 점을 주의해야 한다.

이렇게 JSON.parse() 함수의 2번째 파라미터인 reviver 함수를 사용하면 JSON 문자열을 객체로 변경하면서 속성값들의 값도 변경시켜 줄 수 있다.
