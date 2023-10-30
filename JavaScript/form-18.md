# 사용자 입력을 도와주는 datalist 알아보기

datalist 태그는 사용자의 입력을 돕기 위해,
select box 형태로 사용자가 추천할 수 있는 선택지를 제공하고,
자동완성 기능을 제공한다.

- `<datalist>` 태그 알아보기
- `<datalist>`에 value와 label 추가하기
- `<datalist>` default 값 지정하기
- `<datalist>`의 option 전체 목록 가져오기

## `<datalist>` 태그 알아보기

```html
<input list="fruitsList" name="fruits" id="fruits" />
<datalist id="fruitsList">
  <option value="apple" label="사과"></option>
  <option value="banana" label="바나나"></option>
  <option value="grape" label="포도"></option>
  <option value="orange" label="오렌지"></option>
</datalist>
```

`<datalist> `태그는 `<input>` 태그에 연결되어  
사용자가 값을 쉽게 입력할 수 있도록 추천 목록을 제공하고,  
사용자가 추천 목록 안의 값을 타이핑할 경우 자동완성되는 기능을 제공한다.

datalist가 제공하는 추천 목록 이외의 값을 입력할 수도 있다.

select box와 텍스트 입력 창을 합쳐 놓은 것과 비슷함.

주의할 점은  
`<input>`의 list에 정의된 값과 `<datalist>`의 id 값이 같아야 한다.  
이 두 속성이 두 태그를 연결해 주는 역할을 함.

## `<datalist>`에 value와 label 추가하기

```html
<input list="fruitsList" name="fruits" id="fruits" />
<datalist id="fruitsList">
  <option value="apple" label="사과"></option>
  <option value="banana" label="바나나"></option>
  <option value="grape" label="포도"></option>
  <option value="orange" label="오렌지"></option>
</datalist>
```

option에서 value 값은 `<form>`에서 submit 될 때 전달되는 값이다.

option에서 label은 사용자에게 보여주는 값이다.

이렇게 label과 value를 같이 적용했을 때, 브라우저마다 보여주는 방법이 조금씩 다른데  
크롬 브라우저의 경우 value와 label 값을 모두 보여준다.

## `<datalist>` default 값 지정하기

```html
<input list="fruitsList" name="fruits" id="fruits" value="apple" />
<datalist id="fruitsList">
  <option value="apple" label="사과"></option>
  <option value="banana" label="바나나"></option>
  <option value="grape" label="포도"></option>
  <option value="orange" label="오렌지"></option>
</datalist>
```

default 값을 지정하기 위해서는  
`<input>` 태그에 datalist의 option value 중 하나를 value로 설정해 주면 된다.

## `<datalist>`의 option 전체 목록 가져오기

```html
<!-- datalist -->
<input list="fruitsList" name="fruits" id="fruits" value="orange" />
<datalist id="fruitsList">
  <option value="apple" label="사과"></option>
  <option value="banana" label="바나나"></option>
  <option value="grape" label="포도"></option>
  <option value="orange" label="오렌지"></option>
</datalist>

<!-- 버튼 -->
<input type="button" value="option 목록 가져오기" onclick="getOptionList()" />

<!-- option 목록 출력 -->
<div id="valueList"></div>
<div id="labelList"></div>
```

```javascript
function getOptionList() {
  // datalist의 option 목록 가져오기
  const options = document.getElementById("fruitsList").options;

  // 각각의 option에서 value, label 가져오기
  const optionsValue = [];
  const optionsLabel = [];
  for (let i = 0; i < options.length; i++) {
    const option = options[i];
    optionsValue.push(option.value);
    optionsLabel.push(option.label);
  }

  // datalist 목록 출력
  document.getElementById("valueList").innerText = optionsValue;
  document.getElementById("labelList").innerText = optionsLabel;
}
```

`document.getElementById('fruitslist').options;`  
datalist의 option 목록을 가져온다.

`for(...)`  
options 목록을 반복문으로 순회하면서  
각각 option element의 value와 label 값을 가져온다.
