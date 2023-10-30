# URL 파라미터 값 가져오기 (쿼리스트링 값)

URL에 포함된 파라미터(쿼리스트링)의 값을 읽어오는 방법.

- [URL 파라미터 값 가져오기 (쿼리스트링 값)](#url-파라미터-값-가져오기-쿼리스트링-값)
  - [현재 페이지의 URL과 파라미터 읽기](#현재-페이지의-url과-파라미터-읽기)
  - [특정 파라미터 값 읽기](#특정-파라미터-값-읽기)
  - [특정 파라미터가 있는지 체크하기](#특정-파라미터가-있는지-체크하기)
  - [파라미터 추가, 변경, 삭제하기](#파라미터-추가-변경-삭제하기)
  - [전체 파라미터 목록 가져오기](#전체-파라미터-목록-가져오기)
    - [key 목록 가져오기 - URLSearchParams.keys()](#key-목록-가져오기---urlsearchparamskeys)
    - [value 목록 가져오기 - URLSearchParams.values()](#value-목록-가져오기---urlsearchparamsvalues)
    - [key, value 목록 가져오기 - URLSearchParams.entries()](#key-value-목록-가져오기---urlsearchparamsentries)

## 현재 페이지의 URL과 파라미터 읽기

**`window.location.href`**  
현재 페이지 URL 가져오기

**`window.location.search`**  
전체 URL중 쿼리스트링(파라미터)만 가져오기

## 특정 파라미터 값 읽기

전체 URL "https://example.com/?name=hyoni&age=20"에서
hyoni, 20 2개의 파라미터 값을 읽을 수 있다.

```javascript
let params = new URL("https://example.com/?name=hyoni&age=20").searchParams;
let name = params.get("name"); // "hyoni"
let age = parseInt(params.get("age")); // 20
let paramsAll = params.getAll("name"); // ['hyoni']
```

`const url = new URL("URL문자열(document.location)")`  
new URL()을 사용하여 생성된 URL 객체는, URL의 여러 구성 요소를 쉽게 다룰 수 있도록 도와준다.

`URL: searchParams 속성`
URL 객체중 searchParams 속성은, URL의 파라미터를 다룰 수 있는 객체인 URLSearchParams 객체를 리턴한다.

`params.get("파라미터명")`
URLSearchParams.get() 함수는 URL의 쿼리스트링에서 '파라미터명'으로 조회된 첫번째 값을 리턴한다.

`params.getAll("파라미터명")`
params.getAll() 함수는 URL의 쿼리스트링에서 `파라미터명`으로 조회된 모든 값을 배열로 리턴한다.

## 특정 파라미터가 있는지 체크하기

```javascript
let params = new URLSearchParams("?name=hyoni&age=20");
let name = params.has("name"); // true
let age = params.has("x"); // false
```

`new URLSearchParams("쿼리스트링")`  
URLSearchParams에 쿼리스트링을 전달하여,  
URLSearchParams 객체를 직접 생성할 수 있다.

`params.has('파라미터명')`  
params.has() 함수를 사용하면,  
쿼리스트링에 '파라미터명'에 해당하는 파라미터가 있는지 확인 할 수 있다.

## 파라미터 추가, 변경, 삭제하기

```javascript
let params = new URLSearchParams("?name=hyoni&age=20");

// 파라미터 추가 append()
params.append("lang", "ko");
params.append("lang", "en");
document.write(params); // name=hyoni&age=20&lang=ko&lang=en

// 파라미터 변경 set()
params.set("lang", "cn");
document.write(params); // name=hyoni&age=20&lang=cn

// 파라미터 삭제 delete()
params.delete("lang");
document.write(params); // name=hyoni&age=20
```

파라미터 추가: `params.append("파라미터명", "값")`  
파라미터 변경: `params.set("파라미터명", "값")`  
파라미터 삭제: `params.delete("파라미터명")`

## 전체 파라미터 목록 가져오기

### key 목록 가져오기 - URLSearchParams.keys()

```javascript
let params = new URLSearchParams("?name=hyoni&age=20");

// key 목록
const keys = params.keys();

for (const key of keys) {
  console.log(key);
}
```

URLSearchParams.keys() 메서드는 key 목록을 순회할 수 있는 iterator를 반환한다.

### value 목록 가져오기 - URLSearchParams.values()

```javascript
let params = new URLSearchParams("?name=hyoni&age=20");

// value 목록
const values = params.values();

for (const value of values) {
  console.log(value);
}
```

URLSearchParams.values() 메서드는 value 목록을 순회할 수 있는 iterator를 반환한다.

### key, value 목록 가져오기 - URLSearchParams.entries()

```javascript
let params = new URLSearchParams("?name=hyoni&age=20");

// value 목록
const entries = params.entries();

for (entry of entries) {
  console.log(`${entry[0]}, ${entry[1]}`);
}
```

URLSearchParams.entries() 메서드는 key와 value 목록을 순회할 수 있는 iterator를 반환한다.

**(!) URL, URLSearchParams 객체는 인터넷 익스플로러와 사파리 일부 버전에서는 사용할 수 없다.**
