# 객체의 모든 key, value 값 가져오기 for...in문

## for...in문

`for...in` 문은 상속된 열거 가능한 속성들을 포함하여 객체에서 문자열로 키가 지정된 모든 열거 가능한 속성에 대해 반복한다. (Symbol로 키가 지정된 속성은 무시)

```javascript
for (const variable in object) {
  statement;
}
```

- `variable` : object에서 순차적으로 하나씩 꺼내온 property(속성)의 key(이름)
- `object` : 탐색할 object

```javascript
const rabbit = {
  name: 'bunny',
  age: 2
};

for (prop in rabbit) {
  console.log(`${prop} : ${rabbit[prop]}`);
  /*
  Output:
  name : bunny
  age : 2
  */
```

`rabbit`이라는 객체를 생성하여 name과 age 속성을 정의.

`for..in` 구문을 이용하여, rabbit 객체에서 prop 이라는 이름으로 속성을 하나씩 추출한다.  
`for...in` 구문의 블록 안에서, prop이라는 이름으로 객체의 각각 속성명에 접근할 수 있다.

`${prop} : ${rabbit[prop]}`  
속성명(key) 출력 : prop은 객체의 속성명(key)을 출력.  
속성값(value) 출력 : rabbit[속성명] 구문을 사용.
