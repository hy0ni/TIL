# select box에서 선택한 값, 텍스트 출력하기

- [select box에서 선택한 값, 텍스트 출력하기](#select-box에서-선택한-값-텍스트-출력하기)
  - [select box에서 선택한 값 출력하기](#select-box에서-선택한-값-출력하기)
  - [선택한 select box 텍스트 출력하기](#선택한-select-box-텍스트-출력하기)
  - [중복 선택된(multiple) 값과 텍스트 출력하기](#중복-선택된multiple-값과-텍스트-출력하기)

## select box에서 선택한 값 출력하기

```html
<select name="language" onchange="handleOnChange(this)">
  <option value="korean">한국어</option>
  <option value="english">영어</option>
  <option value="spanish">스페인어</option>
</select>
<div id="result"></div>
```

```javascript
function handleOnChange(e) {
  // 선택된 데이터 가져오기
  const value = e.value;

  // 데이터 출력
  document.getElementById("result").innerText = value;
}
```

select box가 선택되면 handleOnChange() 함수를 호출하고,  
파라미터로 select element를 전달한다.

파라미터로 넘어온 select element의 value 값은
사용자가 선택한 항목의 'value' 속성 값을 리턴한다.

## 선택한 select box 텍스트 출력하기

```javascript
function handleOnChange(e) {
  // 선택된 데이터의 텍스트값 가져오기
  const text = e.options[e.selectedIndex].text;

  console.log(text);

  // 선택한 텍스트 출력
  document.getElementById("result").innerText = text;
}
```

`e.selectedIndex`  
선택된 항목의 index 값 가져오기.

`e.options`  
select box의 선택(options) element 목록 가져오기.

`e.options[e.selectedIndex]`  
사용자가 선택한 항목의 index를 사용하여  
select box의 선택 목록에서  
사용자가 선택한 select box의 선택항목 element를 가져오기.

`e.options[e.selectedIndex].text`  
선택된 element의 text 값 가져오기.

## 중복 선택된(multiple) 값과 텍스트 출력하기

```html
<select name="language" onchange="handleOnChange(this)" multiple>
  <option value="korean">한국어</option>
  <option value="english">영어</option>
  <option value="chinese">중국어</option>
  <option value="spanish">스페인어</option>
</select>
<div id="values"></div>
<div id="texts"></div>
```

```javascript
function handleOnChange(e) {
  // options에서 selected 된 element의 value 찾기
  const values = [...e.options].filter((option) => option.selected).map((option) => option.value);

  // options에서 selected 된 element의 text 찾기
  const texts = [...e.options].filter((option) => option.selected).map((option) => option.text);

  // 선택된 데이터 출력
  document.getElementById("values").innerText = values;
  document.getElementById("texts").innerText = texts;
}
```

`[...e.options]`  
options에 filter(), map() 함수를 적용하기 위해  
options에 destructuring(구조 분해 할당)을 적용해  
배열 형태로 만든다.

`filter(options => option.selected)`  
options 목록 중 selected 값이 true인 것만 골라낸다.

`map(option => option.value)`  
`map(option => option.text)`  
filter로 걸러진 목록의 value 또는 text 값으로 새로운 배열을 만들어 리턴.
