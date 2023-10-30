# 체크박스(checkbox)에 선택 된 값 출력하기

- [체크박스(checkbox)에 선택 된 값 출력하기](#체크박스checkbox에-선택-된-값-출력하기)
  - [체크박스를 선택 했을 때, 선택한 값만 출력하기](#체크박스를-선택-했을-때-선택한-값만-출력하기)
  - [체크박스를 선택 했을 때, 선택된 모든 값 출력하기](#체크박스를-선택-했을-때-선택된-모든-값-출력하기)
  - ['확인' 버튼을 눌렀을 때 선택된 값 출력하기](#확인-버튼을-눌렀을-때-선택된-값-출력하기)

## 체크박스를 선택 했을 때, 선택한 값만 출력하기

```html
<input type="checkbox" name="animal" value="dog" onclick="getCheckboxValue(event)" /> 개
<input type="checkbox" name="animal" value="cat" onclick="getCheckboxValue(event)" /> 고양이
<div id="result"></div>
```

```javascript
function getCheckboxValue(event) {
  let result = "";
  if (event.target.checked) {
    result = event.target.value;
  } else {
    result = "";
  }

  document.getElementById("result").innerText = result;
}
```

getCheckboxValue() 함수는  
이벤트가 발생한 체크박스의 checked 값이 true이면,  
이벤트가 발생한 체크박스의 value 값을 가져와서 화면에 출력한다.

## 체크박스를 선택 했을 때, 선택된 모든 값 출력하기

```html
<input type="checkbox" name="animal" value="dog" onclick="getCheckboxValue()" /> 개
<input type="checkbox" name="animal" value="cat" onclick="getCheckboxValue()" /> 고양이
<div id="result"></div>
```

```javascript
function getCheckboxValue() {
  // 선택된 목록 가져오기
  const query = 'input[name="animal"]:checked';
  const selectedEls = document.querySelectorAll(query);

  // 선택된 목록에서 value 찾기
  let result = "";
  selectedEls.forEach((el) => {
    result += `${el.value} `;
  });

  // 출력
  document.getElementById("result").innerText = result;
}
```

**`선택된 목록 가져오기`**  
전체 체크박스에서 선택된 목록 전체를 가져오기 위해  
document.querySelectorAll() 함수를 사용.  
query 문을 파라미터로 받아,  
query 문을 만족하는 모든 element를 포함하는 NodeList를 리턴한다.

**`선택된 목록에서 value 찾기`**  
querySelectorAll() 함수가 리턴 한 값은 element 목록이기 때문에  
반복문을 사용하여 각각의 element에 접근하여 value 값을 가져온다.

## '확인' 버튼을 눌렀을 때 선택된 값 출력하기

```html
<input type="checkbox" name="animal" value="dog" /> 개
<input type="checkbox" name="animal" value="cat" /> 고양이
<button onclick="getCheckboxValue()">확인</button>
<div id="result"></div>
```

버튼에만 onclick 이벤트로 getCheckboxValue() 함수 전달.
